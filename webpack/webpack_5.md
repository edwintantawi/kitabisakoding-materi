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

Hallo semua, selamat datang di channel KitaBisaKoding.
Pada video ini kita akan melanjutkan playlist ini yang membahas mengenai webpack 5, di video sebelumnya kita sudah melihat studi kasus yang akan kita kerjakan di playlist ini, kita juga sudah membagi file javascript menjadi beberapa file.

sekarang kita akan menggunakan webpack di studi kasus kita sebelumnya.

sebelum itu pastikan di komputer teman teman sudah terinstall javascript package manager baik itu npm untuk npm secara kalau kita menginstall nodejs npm juga ikut terinstall atau kalau terbiasa menggunakan yarn bisa pakai yarn. di sini saya menggunakan npm. cara ceknya cukup ketikan di terminal:

"npm --v"

jika muncul verisinya, maka npm sudah bisa di gunakan.

sekarang di terminal pastikan pathnya mengarah ke root project kita ini.

kalau kita pakai terminal dari vscode, itu otomatis akan di arahkan ke direktori yg sesuai

yang pertama kita lakukan adalah melakukan "npm init" untuk menginisialisasikan npm di project ini. caranya cukup jalankan perintah "npm init -y" agar cepat saya gunakan flag y agar semua di isi secara default.

jika kita jalanakan maka kita akan mendapatkan file baru bernama package.json,
isinya ada informasi mengenai project kita.

selanjutnya kita akan menginstall webpack.
untuk menginstall webpack kita memerlukan 2 module yang akan kita install yaitu:

webpack dan webpack-cli,

cara menginstallya cukup dengan
"npm install --save-dev webpack webpack-cli"

karena nantinya webpack dan webpack cli hanya kita gunakan waktu proses development, dan tidak akan dibawa ke tahap production, maka kita menambahkan flag --save-dev agar di install pada devDependency.

webpack yang kita install ini sebagai core atau inti dari webpacknya, lalu webpack-cli gunanya agar kita dapat menjalankan perintah yang ada pada webpack di command line kita tau terminal kita.

jika kita enter maka webpack dan webpack-cli akan di install. pastikan untuk terkoneksi ke internet.

jika sudah, kita bisa lihat ke file package.json kita,
muncul object baru bernama devDependency isinya ada webpack dan webpack-cli beserta versinya yang kita install tadi. di sini versi webpack saya 5.24.2 saat video ini dibuat.

lalu ada juga file package-lock.json dan folder node_module yang beisi module yang kita install.

sekarang kita akan menggunakan webpack kita, caranya cukup mudah kita cukup memanggil perintah "webpack" di terminal kita. atau kita bisa meletakan perintahnya di script package.json agar kita lebih mudah memanggilnya berulang.

kita letak perintahnya di file package.json lalu di dalam object script, untuk test ini bisa kita hapus karena ga kita gunakan,

lalu kita isi dengan
"start" : "webpack"

dengan begini kita bisa menjalankan di terminal dengan perintah
"npm start"

kita coba jalankan, ini kita akancoba webpack tanpa konfigurasi apaun alias default dari webpacknya, kedepannya kita akan memberikan konfigurasi kita sendiri.

jika kita jalankan,

maka akan muncul banyak error dan warning, jika kira scroll ke atas,
di sini npm start kita menjalankan perintah webpack,

lalu ada warning in configuration,
mode option has not been set

ini karena kita tidak memberikan konfigurasi mode pada webpacknya, maka akan di alihkan ke mode production,
di webpack ada 2 mode yaitu production dan development, di video kedepan juga akan kita bahas.

di bawahnya kita mendapat error:
Module not found: Error: Can't resolve './src'

di sini dikatakan tidak di jumpai module pada folder './src'
jika kita lihat struktur folder kita kita tidak memiliki module apapun di folder src, hanya 3 buah folder.

secara default webpack akan menjadi module javascript pada folder './src'
module yang akan di jalankan webpack pertama kali ini kita sebut sebagai entry point.

coba kita ikuti, kita pindahkan module main.js kita ke folder './src' karena main.js ini tempat awal jalannya program kita.

dan kita harus mengubah nama dari main.js menjadi index.js agar terbaca oleh webpack

setelah kita pindahkan dan rename, kita jalankan ulang
"npm start"

sekarang sudah tidak ada error lagi, hanya tersisa warning tadi nanti akan kita perbaiki.

kita sudah bisa menjalankan dan menggunakan webpack, walau hanya sebatas menjalankannya langsung tanpa konfigurasi.

jika kita lihat kita di buatkan folder baru bernama dist atau singkatakan dari distribution, di dalamnya terdapat main.js yang di buatkan webpack, jika kita buka isinya hanya pemanggilan fungsi getPokemon(); seperti pada index.js kita.

karena cara kerja dari webpack yang kita bahas pada video pertama,
webpack akan mentracking atau memantau ketergantungan antar module si sini kita hanya memanggil fungsi getPokemon() dan memberitahuan menggunakan fungsi getPokemon() dari module mana.

cara kita dapat menggunakan import export module javascript.

caranya kita bisa memberikan "export" di depan variabel ataupun fungsi yang nantinya akan digunakan atau di import di module lain.

jika kita lihat di api.js ada fungsi getPokemon() yang mana akan digunakan di index.js kita, maka kita harus melakukan export, dengan menambahkan export di depan fungsinya,

sebenarnya ada 2 cara untuk melakukan export di javascript, pertama denga keyword export lalu dengan export default, untuk perbedaannya teman teman bisa explore sendiri di internet, di sini saya akan mengguakan keyword export

selanjutnya pada endpoint.js ada variabel yang akan di pakai di api.js
maka kita perlu mengexportnya denga menambahkan keyword export di depan,

selanjutnya pada insert.js ada variabel list, vaiabel ini tidak di pakai di module lain, karena hanya di pakai di fungsi ini, lalu ada fungsi getPokemonDetail(), fungsi ini digunakan di api.js maka kita perlu mengexportnya

sekarang kita bisa import module ke setiap module yang membutuhkan module lain,

pertama di index.js kita memerlukan fungsi getPokemon() dari api.js

cara mengimportnya kita tuliskan keyword import di paling atas javascript kita,
lalu diikuti kurung kurawal {} berisi nama fungsi yang kita export, di api.js kita mengexport fungsi getPokemon, lalu "form" lalu lokasi dari module yang akan kita import, di sini api.js kita berada di folder script lalu api.js,

kita akan lakukan ke api.js
import { API_END_POINT } from './endpoint.js';
karena kita memerlukan variabel API_END_POINT

import { getPokemonDetail } from './insert.js';
lalu fungsi getPokemonDetail

sekarang semua module kita sudah saling terhubung.

sekarang coba kita jalankan,
"npm start"

tidak ada error, kita lihat ke main.js di folder dist, sekarang sudah berisi javascript yang telah dibuatkan oleh webpack , susah untuk terbaca karena sudah di minify karena webpack mode kita berada di tahap production.

jika kita cek di browser,
maka tidak tampil apapun, karena pada index.html kita masih mengaikan ke main.js di lokasi lama kita, sedangkan yang harusnya kita gunakan hasil dari webpack di folder dist,

sekarang kita rubah ke main.js di folder dist, kita juga cukup 1x saja memanggil main.js tanpa perlu memanggil yang lainnya

<script src="./dist/main.js"></script>

sekarang html kita sudah menggunakan javascript yang di buatkan oleh webpack,
jika kita cek di browser

dan semua bekerja dengan normal dengan menggunakan javascript hasil dari webpack.

selamat kita sudah berhasil menggunakan webpack dengan zero configuration atau tanpa konfigurasi sama sekali,

di video selanjutnya kita akan memberikan konfigurasi pada webpack kita, memberikan loader dan plugins agar webpack kita semakin powerfull.

## Part 4 [ Konfigurasi Webpack ]

Hallo semua, selamat datang di channel KitaBisaKoding.
Pada video ini kita akan melanjutkan playlist ini yang membahas mengenai webpack 5, di video sebelumnya kita menerapkan webpack di studi kasus kita dengan konfigurasi webpack default. Sekarang kita akan membuat dan menggunakan Konfigurasi yang kita buat sendiri untuk digunakan oleh webpack.

Cara membuat konfigurasi webpack, kita bisa buat file baru dengan nama
"webpack.config.js" di root project kita.

nantinya semua konfigurasi akan kita letakan di file ini.

cara menuliskan konfigurasinya, kita wajip melakukan export sebuah object yang berisi konfigurasi kita dengan menggunakan module.exports, module.exports ini mirip seperti export di javascript yang kita pernah buat sebelumnya, tapi module.exports ini digunakan pada enviroment nya si nodejs. lalu yang kita export adalah sebuah object,

ada banyak konfigurasi yang bisa kita masukan ke object ini. Kita akan bahas satu persatu.

yang pertama kita bisa mengatur entrypoint webpack kita, entrypoint ini sebagai lokasi titik awalnya webpack akan menelusuri keterkaitan antar module agar di buatkan dependency graph. pada beberapa video sebelumnya secara default entry point ini akan mencari file/module javascript dengan nama index.js di dalam folder src.

cara menerapkannya kita cukup memberikan key value di dalam object.
"entry:" dengan value lokasi dari file yg akan dijadikan sebagai entrypoint. di sini saya akan berikan lokasi nya ke index.js pada folder src sama seperti defaultnya.

"entry: './src/index.js'"

berikutnya kita bisa mengkonfigurasi output dari webpack.
jika kita perhatian sebelumnya jika kita menjalankan webpack, maka webpack akan menghasilkan output berupa folder dist dan berisi hasil dari proses webpack.

sekarang kita bisa mengatur itu, dengan menambahkan konfigurasi output, caranya kita bisa tambahkan lagi key value pada object,
dengan key "output" lalu kita bisa memberikan value berupa object lagi, di dalam object ini kita bisa berikan beberapa konfigurasi untuk output,
pertama kita bisa memberikan penamaan untuk hasil file yang di bundle oleh webpack, jika sebelumnya kita mendapatkan file javascript bernama main.js sekarang kita dapat menggantinya sesuka kita. dengan memberikan "filename" dengan value berisi string nama file yg kita inginkan, contohnya saya akan buat dengan nama 'main.bundle.js'

setelah filename kita juga bisa mengatur di mana output akan di keluarkan, secara default webpack akan mengeluarkan output berupa folder dist di root project kita,
kita bisa merubahnya sesuai keinginan kita, caranya kita bisa menambahkan pasangan key value lagi di object output,

dengan key "path" lalu kita bisa berikan value berupa lokasi nya, yang perlu di perhatikan di sini, pada output path kita ga bisa menggunakan relative path seperti pada entrypoint jika kita coba menggunakan relative path, contohnya saya berikan "./dist" jika kita jalankan maka akan muncul error, dan mengharuskan kita menggunakan absolute path.

caranya kita bisa menggunakan module path, dengan cara melakukan import module path ke webpack.config.js kita.
dengan "const path = require('path')" module path ini sendiri ga perlu kita install karena sudah ada ketika kita menginstall nodejs.

sekarang kita bisa memanfaatkan module path ini dengan cara
path.resolve(\_\_dirname, 'dist'),

kita menggunakan fungsi resolve dari module path lalu kita berikan dua parameter yg pertama **dirname. **dirname ini akan merujuk pada direktori kita sekarang, lalu kita berikan string sebagai parameter kedua sebagai nama folder yang akan di gunakan, biasanya kita bisa beri nama dist atau build jika pada reactjs. kita coba berikan nama "build" sebagai pembeda dari setting default.

jika kita jalankan npm start,

di terminal tidak ada error, sekarang kita dibuatkan sebuah folder baru bernama build seperti yang kita buat pada konfigurasi webpacknya, dan didalamnya ada file javascript bernama main.bundle.js yg juga kita konfigurasi sebelumnya isinya tetapa sama seperti sebelumnya, sekarang kita bisa hapus folder dist, karena kita akan memakai penamaan build, jika kita tes web kita ini ga akan jalan ya, karena kita harus ubah lagi pemanggilan javascript kita yang sebelumnya mengambil file main.js di folder dist, sekarang kita alihkan ke main.bundle.js di folder build.

jika kita coba buka di browser, maka web kita berjalan normal.

Kalau kita lihat di terminal dari pertama sertiap kali kita jalankan, ada satu warning yang peringati kita kalau kita belum memberikan konfigurasi mode pada webpack kita, dan secara default webpack akan menggunakan mode production.

sekarang coba kita hilangkan peringatan ini dengan cara memberikan konfigurasi mode di webpack.config.js kita.

dibawah output kita bisa berikan pasangan key value berupa mode, dengan value berupa string antara production atau development, kita coba berikan production, ini konfigurasi yang akan di gunakan webpack kita sebelumnya jika kita tidak memberikan mode.
kita coba jalnakan npm start, maka warning kita sebelumnya sudah tidak ada lagi,

jadi apa gunanya mode ini, jika kita lihat hasil webpack kita di main.bundle.js,
isinya berupa file javascript yang dibundle oleh webpack, lalu javscript kita juga di minify menjadi satu baris. jika kita lihat di vscode jumlah barisnya 1, ini kelihatan banyak karena textnya kalau melebihi layar akan di wrap ke bawah, lalu jika kita meletakan komentar, komentarnya juga akan di hilangkan. maksud dari mode production ini, untuk membuat bundle yang siap untuk dibawa ke tahap production, tahap ini nanti file yang di hasilkan ini sudah siap langsung dunakan baik itu di hosting/deploy. makanya hasil dari webpack dengan mode production susah untuk dibaca, di minify, dan menghilangkan komentar yang ada untuk menekan ukuran file yang besar.

selain production ada mode development, untuk mode ini digunakan untuk tahap development ataup tahap dimana kita masih mengerjakan project ini, jika kita ganti modenya menjadi mode development, lalu kita jalankan npm start.

kita lihat lagi ke main.bundle.js sekarang isi dari main.bundle.js kita lebih banyak dari sebelumnya, dan ga di minify. jadi kita dipermudah memahami kode ini untuk proses debuging. di sini kita bisa lihat logic dari webpack pada code kita. yg paling bawah ini code punyanya si webpack.

untuk mempermudah proses devlopment kita, kita juga bisa menmbah 1 konfigurasi lagi yaitu devtool, kita cukup menambahkannya setelah mode kita, dengan key "devtool" lalu valuenya ada beberapa konfigurasi yang bisa kita gunakan, kita bisa cek langsung ke dokumentasinya, linknya nanti akan saya taruh di deskripsi.

di dokumentasinya kita bisa lihat value apa aja yang bisa kita gunakan, lalu ada deskripsi kegunaannya, di sini ada yang bisa di gunakan di mode production juga.

kita akan coba pakai soure-map, kita jalankan ulang, jika kita lihat di folder build kita bertambah satu file lagi ini file sourcemap untuk file main.bundle.js kita, dan di main.bundle.js kita formatnya beda lagi dari sebelumnya.

teman teman boleh coba coba explorasi tes devtool yg tersedia.

masih banyak lagi konfigurasi yang dapat kita berikan, pada video selanjutnya kita akan mengenal loader untuk menagani berkas css kita.

## Part 5 [ CSS Loader & Style Loader untuk CSS ]

Hallo semua, selamat datang di channel KitaBisaKoding.
Pada video ini kita akan melanjutkan playlist ini yang membahas mengenai webpack 5, di video sebelumnya kita sudah membuat konfigurasi webpack kita sendiri,

pada video kali ini kita akan menggunakan loader, pada beberapa video sebelumnya kita sudah menyinggung mengenai loader.

dimana fungsi loader ini untuk memungkinkan webpack mengolah file jenis lain diluar javascript, kalau plugins sendiri dapat kita gunakan untuk optimisasi, pengolahan asset, dan lainnya. sebelumnya webpack kita hanya menagani file javascript kita.
di video ini kita akan gunakan loader untuk menangani file css kita.

kita perlu menginstall terlebih dahulu loader yang kita butuhkan sebelum kita menggunakan.
untuk css kita perlu 2 loader yaitu css-loader dan style-loader, kedua loader ini punya fungsi nya masing masing,

cara menginstallnya cukup

"npm install --save-dev css-loader style-loader"
kita akan instal kedua loader ini ada css-loader dan style-loader,

sekarang jika sudah terinstall, sekarang kita bisa terapkan loader ini di webpack config kita.

cara menambahkan loader, kita bisa menmabahkan key value
module, dengan value object lagi,

di dalam object module kita tambahkan rules, dengan value berupa array. Didalam array ini kita bisa menerapkan loader loader kita,

caranya kita perlu memberikan object, di dalam object ini akan kita letakan konfigurasi loader untuk css kita.
yang pertama kita butuhkan adalah memberitaukan ke webpack file apa saja yang akan di di proses oleh webpack dengan loader ktia,
dengan key test lalu valuenya kita bisa menggunakan regex. kita bisa tulisakan /\.css$/i dengan begini kita memilih semua file dengan extensi akhiran css tanpa memperhatikan case sensitive.

berikutnya kita berikan key "use" dengan value nama loader yang akan digunakan, karena kita akan menggunakan 2 loader untuk css kita, kita akan letakan ke sebuah array.

di dalamnya kita bisa masukan nama nama loadernya ['style-loader','css-loader'], yang perlu kita ingat untuk pemanggilan urutan loader juga berpengaruh, webpack akan menggunakan loader satu persatu dari urutan terakhir atau yg paling kanan, di sini kita buat style loader lalu css loader,

sekarang apa gunanya kedua loader ini, yang pertama css loader, css loader digunakan untuk mengubah dan memasukan css menjadi javascript,
nanti semua css kita akan menjadi satu dengan javascript.

lalu setelah css-loader selesai di jalankan, style-loader akan di jalankan, fungsi dari style loader ini untuk memasukan/inject css yang ada pada javascript kita yang hasil dari css-loader ke DOM atau html kita.

sebelum kita jalankan ada 1 hal lagi yang perlu kita lakukan, kita perlu mengimport css kita ke javascript. kita akan import di index.js
import './style/style.css';

lalu kita dapat menghapus link css kita yang di index.html.

sekarang jika kita jalankan "npm start" maka jika kita lihat pada browser, semua berjalan normal, css nya semua berjalan. lalu jika kita inspect element, dibagian head html kita ada tag style yang berisi css kita, padahal kita tidak ada membuatnya, ini karena peran dari style loader yang menginject css kita ke DOM html dengan tag style.

sekarang jika kita balik, lihat ke bundle javascript kita, di sini kita bisa lihat css kita ada di sini, ini hasil dari css-loader yang kita gunakan.

kita sudah bisa menangai css dengan webpack, di video selanjutnya kita akan belajar gimana menagani sass pada webpack dengan sass-loader.

## Part 6 [ sass-loader untuk SASS ]

Hallo semua, selamat datang di channel KitaBisaKoding.
Pada video ini kita akan melanjutkan playlist ini yang membahas mengenai webpack 5, di video sebelumnya kita sudah menggunakan css-loader dan style-loader untuk menangani berkas css kita dengan webpack. selanjutnya di video ini kita akan menangani berkas sass atau pun scss jika kita menggunakan sass/scss di project kita. jika hanya css, css-loader dan style-loader sudah cukup. sekarang kita akan coba bagaimana jika kita menggunakan sass atau scss.

sebelumnya kita punya hanya berkas style, sekarang coba kita ganti jadi scss.
lalu kita ganti juga yang ada di index.js menjadi style.scss

jika kita jalankan "npm start"

maka akan muncul error, karena webpack belum mengenal berkas sass atau scss kita, yang kita perlukan sekarang adalah loader yang tepat untuk berkas scss atau sass kita.

yang perlu kita install adalah sass-loader dan sass
"npm install --save-dev sass-loader sass"

sass-loader ini sebagai loader untuk membuat webpack kita mengenali berkas sass/scss, lalu kita juga perlu menginstall sass, sass ini nantinya berguna untuk mengcompile berkas sass/scss kita menjadi css.

setelah kita instal sass dan sass-loader kita perlu menerapkannya di webpack config kita.

kita bisa merubah test kita yang sebelumnya css menjadi sass atau scss dengan regex yang baru
/\.s[ac]ss$/i

dengan begini, kita bisa memilih semuah file dengan extensi akhiran sass mupun scss.

selanjutnya kita perlu menambahkan loader lagi di array use kita, kita tambahkan sass-loader

pastikan sass-loader kita letakan di posisi paling kananatau akhir, agar sass-loader pertama kali di jalankan, nantinya sass-loader akan mengcompile atau merubah berkas scss atau sass kita menjadi css, lalu css-loader akan mengubah css hasil dari sass-loader kita ke dalan javascript, lalu style-loader akan menginject css yang ada di javascript ke DOM html kita.

jika kita coba jalankan, maka ga ada error lagi, dan jika kita lihat di browser, semua style berjalan normal.

sekarang kita sudah bisa menangani berkas sasss/scss di project kita, selanjutnya kita akan menggunakan babel pada webpack kita.

## Part 7 [ Babel untuk Javascript ]
