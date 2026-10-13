Lab4Web - Praktikum 4: CSS Layout
	
Nama	Albert Maulana
NIM	312510162
Mata Kuliah	Pemrograman Web
Praktikum	4 - CSS Layout
Tujuan Praktikum
Memahami struktur dasar pembuatan layout.
Memahami konsep box element.
Memahami CSS Floating.
Memahami HTML5 Semantic Elements.
Membuat layout web sederhana.
Struktur Folder
Lab4Web/
├── lab4_box/
│   └── lab4_box.html
├── lab4_layout/
│   ├── home.html
│   ├── about.html
│   ├── kontak.html
│   └── style.css
├── screenshots/
└── README.md

Bagian 1 - Box Element & CSS Float (lab4_box.html)
1.1 Persiapan Dokumen HTML

Dibuat file lab4_box.html berisi struktur dasar HTML5 dengan elemen semantik <header> yang memuat judul <h1>Box Element</h1>.

html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Box Element</title>
</head>
<body>
    <header>
        <h1>Box Element</h1>
    </header>
</body>
</html>
1.2 Membuat Box Element

Di dalam <section> ditambahkan tiga elemen <div> dengan class div1, div2, dan div3. Setiap div dianggap sebagai sebuah box yang terdiri dari margin, border, padding, dan content.

html
<section>
    <div class="div1">Div 1</div>
    <div class="div2">Div 2</div>
    <div class="div3">Div 3</div>
</section>
1.3 CSS Float Property

Pada <head> ditambahkan CSS di dalam tag <style>. Properti float: left membuat setiap div "mengambang" ke kiri sehingga ketiga box tersusun menyamping, bukan bertumpuk ke bawah seperti perilaku default elemen block. Properti padding: 10px memberi ruang di dalam box, dan background memberi warna pembeda.

css
div {
    float: left;
    padding: 10px;
}
.div1 { background: red; }
.div2 { background: yellow; }
.div3 { background: green; }

Hasil:
<img width="1920" height="1080" alt="Screenshot (130)" src="https://github.com/user-attachments/assets/1850ce02-6e7e-445a-86f8-16dd58366e47" />


1.4 Mengatur Clearfix

Ditambahkan div4 setelah div3. Karena elemen sebelumnya memakai float, elemen berikutnya akan ikut naik di samping mereka. Untuk mencegahnya digunakan properti clear dan float: none pada .div4.

html
<div class="div4">Div 4</div>
css
.div4 {
    background-color: blue;
    clear: left;
    float: none;
}

clear: left membuat div4 turun ke bawah elemen yang mengambang di kiri, sehingga tampil pada baris baru dengan lebar penuh.

Hasil:
<img width="1920" height="1080" alt="Screenshot (132)" src="https://github.com/user-attachments/assets/165e968c-a8cb-4f04-8ea0-9898a14645bf" />
Eksperimen nilai clear:

Nilai	Pengamatan
left	Elemen turun di bawah elemen yang float ke kiri. Pada percobaan ini div4 tampil di bawah div1-div3.
right	Elemen hanya menghindari float kanan. Karena div1-div3 float kiri, div4 tidak turun ke bawah.
both	Elemen menghindari float kiri maupun kanan sehingga selalu turun ke baris baru. Paling aman dipakai.
none	Tidak ada pembersihan float (perilaku default).
hasil:
<img width="1920" height="1080" alt="Screenshot (133)" src="https://github.com/user-attachments/assets/b41d78ee-f9ca-4c07-bfef-81268fbb89f4" />
Bagian 2 - Layout Web Sederhana (lab4_layout)
2.1 Membuat Folder dan File

Dibuat folder lab4_layout yang berisi home.html dan style.css. File HTML menghubungkan stylesheet dengan <link rel="stylesheet" href="style.css"> dan seluruh konten dibungkus <div id="container">.

2.2 Kerangka Layout dengan Semantic Elements

Kerangka halaman disusun menggunakan elemen semantik HTML5:

Elemen	Fungsi
<header>	Header halaman (judul situs)
<nav>	Menu navigasi (Home, Artikel, About, Kontak)
<section id="hero">	Panel utama / hero
<section id="wrapper">	Pembungkus area main dan sidebar
<section id="main">	Konten utama
<aside id="sidebar">	Sidebar / widget
<footer>	Footer halaman
html
<header>
    <h1>Layout Sederhana</h1>
</header>
<nav>
    <a href="home.html" class="active">Home</a>
    <a href="artikel.html">Artikel</a>
    <a href="about.html">About</a>
    <a href="kontak.html">Kontak</a>
</nav>
<section id="hero"></section>
<section id="wrapper">
    <section id="main"></section>
    <aside id="sidebar"></aside>
</section>
<footer>
    <p>&copy; 2021 - Universitas Pelita Bangsa</p>
</footer>

Tampilan kerangka (belum diberi CSS):
hasil:
<img width="1920" height="1080" alt="Screenshot (135)" src="https://github.com/user-attachments/assets/01dd25dc-d5f5-45bd-bbbb-d35df5e913f8" />
2.3 CSS Dasar & Header
@import memuat font Open Sans dari Google Fonts.
Reset CSS (* { margin: 0; padding: 0; }) menghapus margin dan padding bawaan browser agar tampilan konsisten.
body diatur font, ukuran, dan warna teks.
#container dibuat selebar 980px, rata tengah (margin: 0 auto), dengan box-shadow tipis.
header diberi padding dan h1 diberi warna abu-abu muda.
css
* { margin: 0; padding: 0; }

body {
    line-height: 1;
    font-size: 100%;
    font-family: 'Open Sans', sans-serif;
    color: #5a5a5a;
}

#container {
    width: 980px;
    margin: 0 auto;
    box-shadow: 0 0 1em #cccccc;
}

header { padding: 20px; }
header h1 { margin: 20px 10px; color: #b5b5b5; }
hasil:
<img width="1920" height="1080" alt="Screenshot (136)" src="https://github.com/user-attachments/assets/60c227d1-615c-4283-8387-e7c559a23fdb" />
2.4 Navigasi

Menu navigasi diberi latar biru. Link dibuat display: inline-block agar tersusun horizontal namun tetap bisa diberi padding. Kelas .active dan efek :hover memberi warna biru lebih terang.

css
nav {
    display: block;
    background-color: #1f5faa;
}
nav a {
    padding: 15px 30px;
    display: inline-block;
    color: #ffffff;
    font-size: 14px;
    text-decoration: none;
    font-weight: bold;
}
nav a.active,
nav a:hover {
    background-color: #2b83ea;
}
hasil:
<img width="1920" height="1080" alt="Screenshot (137)" src="https://github.com/user-attachments/assets/ff776b05-8eda-4ab9-bd35-1c9f43e48c64" />
2.5 Hero Panel

Ditambahkan judul "Hello World!", paragraf, dan tombol "Learn more »" pada section#hero, lalu diberi latar abu-abu, padding, dan margin bawah.

css
#hero {
    background-color: #e4e4e5;
    padding: 50px 20px;
    margin-bottom: 20px;
}
#hero h1 { margin-bottom: 20px; font-size: 35px; }
#hero p  { margin-bottom: 20px; font-size: 18px; line-heigh
hasil:
<img width="1920" height="1080" alt="Screenshot (138)" src="https://github.com/user-attachments/assets/3824631f-1daf-4b06-a6a3-ce5ad81fd8b2" />
2.6 Layout Main dan Sidebar

#main (lebar 640px) dan #sidebar (lebar 260px) sama-sama float: left sehingga tampil berdampingan. Total lebar: 640 + 260 + padding (4 x 20px) = 980px, sesuai lebar container.

css
#wrapper { margin: 0; }
#main    { float: left; width: 640px; padding: 20px; }
#sidebar { float: left; width: 260px; padding: 20px; }
2.7 Sidebar Widget

Sidebar diisi dua widget-box: satu berisi daftar link (<ul>), satu berisi teks. Gaya widget meliputi border tipis, header biru (.title), daftar tanpa bullet, dan efek hover pada link.

css
.widget-box { border: 1px solid #eee; margin-bottom: 20px; }
.widget-box .title { padding: 10px 16px; background-color: #428bca; color: #fff; }
.widget-box ul { list-style-type: none; }
.widget-box li { border-bottom: 1px solid #eee; }
.widget-box li a { padding: 10px 16px; color: #333; display: block; text-decoration: none; }
.widget-box li:hover a { background-color: #eee; }
.widget-box p { padding: 15px; line-height: 25px; }
hasil:
<img width="1920" height="1080" alt="Screenshot (139)" src="https://github.com/user-attachments/assets/c3f80b30-7bfc-42c8-9691-6e40409a939b" />
2.8 Footer

Karena #main dan #sidebar memakai float, footer harus diberi clear: both agar tampil di bawah keduanya, bukan naik ke samping.

css
footer {
    clear: both;
    background-color: #1d1d1d;
    padding: 20px;
    color: #eee;
}
hasil:
<img width="308" height="93" alt="image" src="https://github.com/user-attachments/assets/6a6b5336-4ac3-46c6-b3d8-cccf5847c0e3" />
2.9 Elemen Tambahan pada Main Content
<section id="main">
<div class="row">
<div class="box">
<img src="https://dummyimage.com/120/db7d25/fff.png" alt=""
class="image-circle">
<h3>Heading</h3>
<p>Donec sed odio dui. Etiam porta sem malesuada magna mollis
euismod.</p>
<a href="#" class="btn btn-default">View detail</a>
</div>
<div class="box">
<img src="https://dummyimage.com/120/3e73e6/fff.png" alt=""
class="image-circle">
<h3>Heading</h3>
<p>Donec sed odio dui. Etiam porta sem malesuada magna mollis
euismod.</p>
<a href="#" class="btn btn-default">View detail</a>
</div>
<div class="box">
<img src="https://dummyimage.com/120/71e6d4/fff.png" alt=""
class="image-circle">
<h3>Heading</h3>
<p>Donec sed odio dui. Etiam porta sem malesuada magna mollis
euismod.</p>
<a href="#" class="btn btn-default">View detail</a>
</div>
</div>
</section>
Kemudian tambahkan CSS.
/* box */
.box {
display:block;
float:left;
width:33.333333%;
box-sizing:border-box;
-moz-box-sizing:border-box;
-webkit-box-sizing:border-box;
padding:0 10px;
text-align:center;
}
.box h3 {
margin: 15px 0;
}
.box p {
line-height: 20px;
font-size: 14px;
margin-bottom: 15px;
}
box img {
border: 0;
vertical-align: middle;
}
.image-circle {
border-radius: 50%;
}
.row {
margin: 0 -10px;
box-sizing: border-box;
-moz-box-sizing: border-box;
-webkit-box-sizing: border-box;
}
.row:after, .row:before,
.entry:after, .entry:before {
content:'';
display:table;
}
.row:after,
.entry:after {
clear:both;
}
hasil:
<img width="1920" height="1080" alt="Screenshot (140)" src="https://github.com/user-attachments/assets/e4fed9ea-b7b8-4fed-b132-d88663f0e834" />
Menambahkan Content Artikel
Selanjutnya membuat content artikel. Tambahkan HTML berikut pada main content.
<hr class="divider" />
<article class="entry">
<h2>First featurette heading.</h2>
<img src="https://dummyimage.com/150/7b8a70/fff.png" alt="">
<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum
lorem elit, iaculis in nisl volutpat, malesuada tincidunt arcu. Proin in leo
fringilla, vestibulum mi porta, faucibus felis. Integer pharetra est nunc,
nec pretium nunc pretium ac.</p>
</article>
<hr class="divider" />
<article class="entry">
<h2>First featurette heading.</h2>

<img src="https://dummyimage.com/150/7b8a70/fff.png" alt="" class="right-
img">

<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum
lorem elit, iaculis in nisl volutpat, malesuada tincidunt arcu. Proin in leo
fringilla, vestibulum mi porta, faucibus felis. Integer pharetra est nunc,
nec pretium nunc pretium ac.</p>
</article>
Kemudian tambahkan CSS.
.divider {
border:0;
border-top:1px solid #eeeeee;
margin:40px 0;
}
/* entry */
.entry {
margin: 15px 0;
}
.entry h2 {
margin-bottom: 20px;
}
.entry p {
line-height: 25px;
}
.entry img {
float: left;
border-radius: 5px;
margin-right: 15px;
}
.entry .right-img {
float: right;
}
<img width="1920" height="1080" alt="Screenshot (142)" src="https://github.com/user-attachments/assets/d1c6c018-7660-4782-90df-5ec8c7fb9592" />



hasil:










