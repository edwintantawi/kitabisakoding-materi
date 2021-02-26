# **Webpack 5**

## Part 1 [ Pengenalan webpack 5 ]

Hallo semua, selamat datang di channel KitaBisaKoding.
Pada video ini dan playlist ini kita akan membahas Salah satu Module Bundler yang sangat terkenal yaitu webpack. Nantinya di Playlist ini kita akan membahas Mengenai Webpack 5, atau versi ke 5 saat ini. Kita juga akan belajar cara menggunakannya dengan langsung mengimplementasikannya ke project kita.
Sebelum kita mulai belajar module bundler ini, teman teman sebaiknya memahami terlebih dahulu dengan baik mengenai HTML, CSS, Javascript, terutama javascript Module, array, object, lalu NPM atau (Node Package Manager). Karena nantinya kita tidak akan jauh dari itu semua.

Sekarang kita mungkin bertanya tanya kenapa kita perlu Module bundler? Dan apa lagi itu webpack? Kenapa kita harus gunakan si module bundler atau webpack ini? Karena kita rasa HTML, CSS, Javascript sudah cukup menangani Frontend web kita.
Sekarang kita akan membahasnya satu persatu.

Apa itu module bundler?
Module Bundler adalah sebuah tools yang biasa digunakan seorang Frontend developer untuk melakukan bundle (bundle ini seperti kumpulan sesuatu yang di jadikan satu kesatuan. sesuatu yang dimaksud di sini adalah javascript modules atau file javascript itu sendiri).

jika kita sudah tau apa itu module bundler, sekarang apa itu webpack? Nah webpack ini merupakan salah satu module bundler yang biasa digunakan, selain webpack masih ada banyak lagi seperti Rollup, parcel dan banyak lagi. Tapi webpack ini yang cukup banyak digunakan.

<slide 3>

Sekarang kita tau gunanya module bundler adalah untuk membundle javascript modules kita, padahal tanpa perlu kita bundle. Javascript kita tetap bisa digunakan.
tapi ada satu kondisi yang membuat module bundler ini sangat berguna. Yaitu ketika

<slide move>

project yang kita kerjakan sudah memiliki banyak sekali module javascript.
Yang perlu kita ketahui juga urutan pemanggilan javascript kita juga sangat berpengaruh, apabila setiap javascript module kita saling berkaitan dan saling membutuhkan, kita contohkan kita memiliki beberapa module javascript ada module1, module2 dan seterusnya.
Urutan pemanggilan module nya bisa kita buat memanggil module1 dulu setelah itu module2 dan seterusnya.
Sekarang terdapat kondisi dimana module1 membutuhkan fungsi atau variabel dan lainnya yang ada di module2, dengan gini, module1 kita akan error kalau urutan pemanggilan kita masih seperti ini, kita bisa ngatasin ini dengan menggubah urutan pemanggilan module nya aja. Jadi module2 kita kana di panggil dulu sebelum module1 karena module1 kita membutuhkan fungsi atau variabel yang ada di module2.
Tapi bagaimana jika module kita semakin kompleks setiap module saling membutuhkan. Maka ini bisa sangat membinggungkan untuk mengatur urutannya.
Untuk mengatasi permasalahan itu terciptalah module bundler itu sendiri salah satunya adalah webpack yang akan kita pelajari di playlist ini.
Saat webpack memproses aplikasi kita, webpack secara internal membuat dependency graph yang memetakan setiap module yang dibutuhkan project kita dan menghasilkan satu atau beberapa Bundle.
Jadi Setiap keterkaitan antar module akan di atur oleh webpack. Jadi kita tidak perlu memikirkan lagi hal itu.

Dan sekarang module bunder terutama webpack tidak hanya dapat menangani module javascript saja, tapi bisa diluar javascript seperti Html, css, image, dan lainnya.
Untuk menagani file jenis lain diluar javascript itu, webpack menyediakan yang namanya loader, ada banyak loader yang bisa di gunakan sesuai kebutuhan
Dan juga webpack menyediakan yang namanya plugins,
Kalau pada loader digunakan untuk memungkinkan webpack mengolah file jenis lain diluar javascript, kalau plugins sendiri dapat kita gunakan untuk optimisasi, pengolahan asset, dan lainnya.
Loader dan plugins nantinya akan sering kali kita gunakan pada webpack kita.

Di video selanjutnya kita akan melihat project studi kasus kita untuk kedepannya.

## Part 2 [ Studi kasus ]

Hallo semua, selamat datang di channel KitaBisaKoding.
Pada video ini dan playlist ini kita akan membahas Salah satu Module Bundler yang sangat terkenal yaitu webpack. Di video sebelumnya kita sudah membahas mengenai apa itu module bundler apa itu webpack, hingga gunanya. Bagi yang belum tonton silahkan tonton video sebelumnya mengenai pengenalan webpack.
Di video ini kita akan melihat project atau studi kasus yang akan kita gunakan pada playlist ini kedepan, dan melihat peranan webpack yang kita bahas di video sebelumnya.

<open code editor>

Di sini saya telah sediakan sebuah project sederhana ada index.html, folder src, isinya ada folder images berisi gambar, folder script berisi file javascript di file javascript kita, kita melakukan proses asyncronus dan fetch untuk mengambil data dari api, kita menggunakan api dari pokeAPI untuk mendapatkan list pokemon, lalu kita loop data hasil fetch api dan kita masukan ke DOM html kita agar bisa muncul di layar web kita, lalu kita juga punya folder style berisi file css.

<open code index.html>

jika kita lihat di index.html kita akan menggunakan bootstrap 4 cdn, terus di bawah ada javascript yang kita buat di folder script, terus ada cdn jquery, popper js dan bootstrap js untuk bootstrap 4 kita. nantinya kita juga akan coba implementasikan bootstrap offline atau bootstrap yang kita install langsung, untuk sekarang kita pakai bootstrap cdn nya dulu agar fokus ke implementasi webpack nya.

<open in browser>

jika kita coba buka project ini di browser..., di sini saya pakai google chrome.

pastikan teman teman terhubung ke internet karena kita menggunakan bootstrap cdn dan kita juga ada melakukan fetch api.

Jika kita lihat di sini kita punya navbar dari bootstrap dengan logo, dan ini juga sudah responsive, hamburger menunya juga berjalan normal karena kita juga menggunakan bootstrap js dan kawan kawannya,
dibawah navbar ada gambar dari background image di css, lalu ada divider atau pembatas berbentuk wave ya atau gelombang dan ini gambar vektor atau svg.

dan dibawahnya ada list gambar dan nama pokemon, yang kita dapatkan dari api pokeAPI di javascript kita.

Kalau kita lihat kasus ini tidak ada yang masalah kita hanya perlu memanggil file javascript kita 1x karena kita hanya ada 1 file javascript.

sekarang kita akan coba memisahkan file javascript ini menjadi beberapa file atau module.

<process split code>

okeh sekarang sudah saya pecah file javascript kita ke beberapa file terpisah
ada

1. main.js (di sini tempat program javascript kita di mulai kita memanggil fungsi getPokemon())
2. api.js (di sini tempat fungsi getPokemon kita yang kita panggil di main.js)
3. endpoint.js (di sini tempat variabel berisi endpoint api pokeAPI kita yang kita gunakan di api.js)
4. insert.js (di sini tempat fungsi getPokemonDetail untuk loop data dari hasil fetch api lalu di masukan ke DOM)

sekarang coba kita jalankan.

<open browser>

kalau kita lihat list pokemon kita ga muncul, coba kita cek di console..
sekarang kita dapat surat cinta dari javascript, yang isinya
**"getPokemon is not defined"**

ini karena kita hanya memanggil main.js di index.html kita, dan di main.js kita memanggil fungsi getPokemon(), tapi fungsi ini ga di temukan, karena berada di file yang berbeda dan ga kita ikut sertakan.

cara mengatasinya tanpa webpack kita bisa dengan cara memanggil file javascript yang di butuhkan di index.html kita sama seperti yang kita lakukan pada main.js,
agar kita tidak menjumpai error lagi kita akan melakukannya ke semua file javascript

kita panggil semua satu satu dengan tag script

kita panggil api.js
endpoint.js
dan insert.js

sekarang semua javascript yang di butuhkan sudah kita panggil, sekarang kita coba buka di browser, kita refresh.

ops, ternyata masih tidak tampil apaun dan ada pesan error di console, dengan pesan error yang sama. padahal kita sudah memanggil semua file javascript yang di butuhkan di index.html.

ini kembali ke konsep yang ada pada cara pemanggilan javascript yg pernah kita bahas di video sebelumnya, karena urutan pemanggilan juga berpengaruh,
jika sebuah file/module javascript membutuhkan file/module dari file lain. maka file yang dibutuhkan harus di panggil sebelum file yang membutuhkan.

jika kita cek pada index.html

kita memanggil pertama kali main.js dimana di dalam main.js kita memanggil fungsi getPokemon() yang ada di api.js, tetapi fungsi getPokemon belum kita definisikan atau kita buat, karena fungsi getPokemon() kita buat setelah main.js di panggil.

cara mengatasinya kita dapat mengubah urutannya dengan merubah posisi main.js dan api.js,

agar api.js deluan yang di eksekusi yang berisi pembuatan function getPokemon(), lalu saat main.js yang memanggil fungsi getPokemon() maka fungsi ini sudah tersedia dari hasil api.js

sekarang coba kita buka di browser, refresh

ternyata masih tidak muncul apapun, jika kita cek di console, error kita yang sebelumnya sudah hilang dan muncul error baru **"API_END_POINT is not defined"**

kasusnya sama seperti sebelumnya kita hanya perlu memperbaiki urutan pemanggilan javascript nya. di sini lah webpack atau module bundler lainnya berperan, karena kasus kita ini tidak begitu rumit kita bisa hanya dengan mengubah urutannya dengan mudah.

<process fix order>

menjadi seperti ini
pertama kita penggil endpoint.js, lalu insert.js, api.js, dan terakhir main.js

jika kita jalankan maka semua berjalan normal, dan tidak ada error di console.

tapi bagaimana jika module javascript kita sudah banyak dan semakin kompleks.
ini akan membingugkan dan memakan banyak waktu.

pada video selanjutnya kita akan mulai mengimplementasikan webpack ke studi kasus sebelum itu kita juga akan belajar mengenai javascript export import.

## Part 3 [ Instalasi webpack & javascript import export ]
