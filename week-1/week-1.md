# React JS

React JS adalah library yang gunanya untuk membuat tampilan user interface website. React JS dapat mempermudah developer untuk memanipulasi tampilan, dan membuat event.

React JS membuat aplikasi front end jadi lebih cepat.

React JS bersifat:

- declarative
- component based
- learn once, write everywhere

Maksud dari Component-based adalah misalnya ketika kita membuat sebuah komponen navbar, maka kita hanya perlu membuat navbar sekali saja, kemudian ketika akan menggunakannya di banyak page, komponen navbar bisa dipanggil. Jadi ketika ada perubahan pada navbar, tidak perlu merubah semua navbar yang ada di setiap page (seperti pada JS vanilla).

## Single Page Application (SPA)

Sebelumnya pada Traditional Web Application, ketika kita ingin membuat beberapa halaman seperti _home, about, contact_, maka setiap halaman harus dibuat file htmlnya menjadi _home.html, about.html, contact.html_.

Namun ketika kita menggunakan teknologi SPA, maka kita hanya perlu satu file html saja, yaitu _index.html_. Dengan menggunakan react, maka javascript akan mengganti isi di dalamnya secara otomatis.

React menggunakan Virtual DOM utk berinteraksi dgn DOM.

Virtual DOM adalah duplikasi dari real DOM yang sebenarnya.

Beda Virtual DOM dan Real DOM.

- Pada Real DOM, ketika kita menambah elemen baru atau mengupdate suatu elemen, maka real DOM akan merender ulang semua elemen yang ada.

- Pada Virtual DOM, React JS hanya akan melakukan render ulang pada komponen yang diupdate. Jadi tidak semua komponen dirender ulang.

Hal itulah yang membuat React JS menjadi lebih cepat performancenya jika dibandingkan dengan Vanilla JS (JS biasa).

## Cara menggunakan React JS

1. Mendownload Node.js terlebih dahulu
2. Membuka cmd pada folder parent tempat di mana folder projek akan dibuat. contohnya di sini saya akan membuat sebuah projek baru pada folder week 1.

3. Menuliskan _npx create-react-app [nama folder]_

   ```
   npx create-react-app first-project
   ```

   <br>
   <img src="./gambar/gambar-1.png">

   <br>

4. Projek selesai dibuat setelah cmd memberitahukan _Happy Hacking!_

   <img src="./gambar/gambar-2.png">

   <br>

5. Isi dari folder react

   <img src="./gambar/gambar-3.png">

    <br>

6. Cara menjalankan aplikasi react pada browser adalah dengan mengetikkan

   ```
   npm start
   ```

   contohnya pada projek react yang telah kita buat sebelumnya.

   <img src="./gambar/gambar-5.png">

   Maka setelah menunggu beberapa saat, akan ada tab baru yang terbuka pada browser dan tampilan defaultnya akan terlihat seperti ini:

   <img src="./gambar/gambar-6.png">

<br>

Dari gambar pada nomor 5 di atas, terdapat 3 folder di dalam folder projek react yang telah dibuat:

- **node_modules** -> berisi package-package yg digunakan dalam projek react
- **public** -> struktur utama web, memiliki _index.html_
- **src** -> isinya adalah file-file js dan css

Pada _index.html_ terdapat baris code

```html
<div id="root"></div>
```

elemen tersebut berada di dalam element <_body_>. Di dalam tag <_div id="root"></div_> tersebutlah nantinya akan disisipkan halaman-halaman lainnya seperti halaman about, contact, dll.

File _index.html_ ini akan secara otomatis memanggil file _index.js_ yang terdapat di dalam folder **src**.

Isi dari folder **src** :

<img src="./gambar/gambar-4.png">

<br>

cuplikan file **index.js**

<img src="./gambar/gambar-7.png">

Dapat dilihat bahwa pada _index.js_, virtual DOM dibuat dan virtual DOM mengambil element id 'root' dari file _index.html_.

Kemudian virtual DOM ini akan merender (menampilkan) **App**.

```html
<App />
```

Tapi dengan syarat, pada _index.js_ harusnya terlebih dahulu mengimport App.

```javascript
import App from "./App";
```

import diletakkan di bagian atas.

Berikut code lengkap dari _index.js_

<img src="./gambar/gambar-8.png">

App adalah sebuah **component** pada React. Setiap component akan berekstensi _.js_.

**src** > **App.js**

<img src="./gambar/gambar-9.png">

Pada _App.js_ akan mengexport _export default app_ agar App.js bisa diimport di _index.js_.
Selain itu, _function App_ memiliki nilai **return**. Return hanya dapat memiliki satu element parent. Pada contoh di atas, element parent dibungkus di dalam tag <_div_>.

contoh yang salah (**return** memiliki lebih dari satu element parent) :

```javascript
function App() {
    return (
        // elemen parent pertama
        <div>
            <h1>Judul</h1>
        </div>
        // elemen parent kedua
        <div>
            <p>Ini adalah isi paragraf</p>
        </div>
    )
}
```

Jika diperhatikan, App.js merupakan file javascript. Akan tetapi di dalamnya malah memuat penulisan html. Hal ini dikarenakan App sebenarnya adalah **jsx**, atau bisa dibilang **javascript xml**.

Jika ingin membuat component yang lain, maka hal yang perlu dilakukan adalah dengan membuat folder **components** di dalam folder **src**.

<img src="./gambar/gambar-10.png">

Di dalam folder **components** kita dapat membuat banyak component, misalnya kita akan membuat _Home.js_. Nantinya _Home_ dapat diexport ke _App.js_.

Penulisan nama function pada jsx adalah dengan diawali huruf kapital.

```javascript
function Home() {
  return;
  // tag kosong dapat digunakan sebagai parent element pada return untuk membungkus seluruh element-element lainnya di dalamnya.
  <></>;
}
```

Contoh di atas adalah penulisan function yang benar.

### **Penulisan atribut 'class' pada JSX**

Pada HTML biasa, ketika kita hendak menambahkan sebuat atribut 'class' pada sebuah element, maka caranya adalah seperti ini :

```html
<div class="container"></div>
```

Sedangkan, pada JSX caranya agak sedikit berbeda. Perhatikan contoh di bawah.

```javascript
<div className="container"></div>
```

<br>

## Lebih Banyak tentang Component..

Sekarang kita akan melihat contoh penggunaan component secara langsung. Kita akan membuat sebuah profile card seperti pada contoh gambar di bawah.

<img src="./gambar/gambar-11.png">

<br>
codenya adalah sebagai berikut :

```html
<div className="profile-container">
  <img src="https://i.pinimg.com/564x/0d/e0/c0/0de0c0721c576c0e9fbd79abd6668089.jpg" alt="" className="profile-image" />
  <div className="profile-info">
    <h1>Farrah</h1>
    <h3>20 Tahun</h3>
  </div>
</div>
```

Ketika kita ingin membuat lebih dari satu _profile card_ seperti pada contoh, umumnya kita akan mengcopy code di atas beberapa kali. Namun dengan React kita tidak perlu melakukan hal tersebut. Kita akan menjadikan _profile card_ sebagai component.

Apa ciri suatu komponen dapat menjadi sebuah _component_ pada React?

```
Component dibuat jika component tersebut bersifat reusable code.
```

Pada kasus ini jika kita ingin membuat lebih dari satu _profile card_, maka dapat disimpulkan bahwa code _profile card_ akan menjadi reusable. Oleh karena itu, kita bisa menjadikan _profile card_ sebagai _component_ pada React. Component _profile card_ nantinya akan dipanggil pada **App.js** untuk ditampilkan ke tampilan web.

```javascript
import "./App.css";
import MemberInfo from "./components/MemberInfo";
import "./components/MemberInfo";

function App() {
  return (
    <>
      <MemberInfo />
      <MemberInfo />
      <MemberInfo />
    </>
  );
}

export default App;
```

Karena _MemberInfo_ dipanggil 3 kali pada **App.js**, maka ketika dijalankan pada browser, profile cardnya akan muncul sebanyak 3 kali juga.

<img src="./gambar/gambar-12.png">

Code pada **App.js** hanya berjumlah 3 baris. Beda halnya jika pada Vanilla JS, biasanya kita akan mengcopy code profile card sebanyak 3 kali. Hal ini menyebabkan code menjadi panjang.

Ketiga card di atas masih memiliki data yang sama. Untuk itu, sekarang akan dijelaskan bagaimana caranya agar setiap card di atas memiliki data yang berbeda dengan menggunakan **props** dan **state**.

### Props dan State

Props dan State adalah sebuah objek dalam Javascript yang digunakan untuk mengirim data.

State -> Data yang ada di dalam sebuah component.

_props_ digunakan sebagai parameter pada file component yang dituju.

**MemberInfo.js** sebelum diberikan atribut.

```javascript
function MemberInfo(props) /*letakkan props pada parameter*/ {
  return (
    <div className="profile-container">
      <img src="https://i.pinimg.com/564x/0d/e0/c0/0de0c0721c576c0e9fbd79abd6668089.jpg" alt="" className="profile-image" />
      <div className="profile-info">
        <h1>Farrah</h1>
        <h3>20 Tahun</h3>
      </div>
    </div>
  );
}
```

Kemudian berikan atribut pada baris code yang ingin ditampilkan.

<br>

**MemberInfo.jsx** sesudah diberikan atribut.

```javascript
function MemberInfo(props) /*letakkan props pada parameter*/ {
  return (
    <div className="profile-container">
      <img src="https://i.pinimg.com/564x/0d/e0/c0/0de0c0721c576c0e9fbd79abd6668089.jpg" alt="" className="profile-image" />
      <div className="profile-info">
        <h1>{props.name}</h1> // name sebagai atribut
        <h3>{props.age} Tahun</h3> // age sebagai atribut
      </div>
    </div>
  );
}
```

Kemudian pada **App.js** berikan atribut _name_ dan _age_ di dalam tag <_MemberInfo_ />

**App.js**

```javascript
import "./App.css";
import MemberInfo from "./components/MemberInfo";
import "./components/MemberInfo";

function App() {
  return (
    <>
      <MemberInfo name={"Askia"} age={"20"} />
      <MemberInfo name={"Farrah"} age={"20"} />
      <MemberInfo name={"Garsia"} age={"20"} />
    </>
  );
}

export default App;
```

Atribut _name_ dan _age_ adalah **props**. Sedangkan nilai dari atributnya adalah **state**.

### useState

useState digunakan untuk menyimpan variabel yang sifat datanya berubah-ubah.

Sebelumny apabila ada variabel yang sudah didefinisikan nilainya, ketika ingin merubah nilainya maka kita hanya perlu menginisialisasikan nilainya ulang. Seperti contoh di bawah:

```javascript
let name = "Andi";
name = "Gayatri";
```

Sekarang akan diberikan contoh apabila menggunakan useState.

```javascript
let [name, setName] = useState("Andi");
setName("Gayatri");
```

Hal ini juga berlaku untuk **const**.

```javascript
const [name, setName] = useState("Andi");
setName("Gayatri");
```

Penggunaan useState ini biasanya akan memunculkan eror. Hal ini dikarenakan, tidak dideteksi adanya sesuatu yang memicu perubahan pada variabel tersebut. Untuk menyiasatinya, kita bisa tambahkan _button_ yang berfungsi sebagai jembatan untuk membuat nilai _name_ berubah.

```javascript
<button onClick={() => setName("Gayatri")}>change name</button>
```

## Stateful dan Stateless

Stateful -> Memiliki state dan bisa mengirim state tersebut ke component

Stateles -> Tidak memiliki state.

Pada contoh kasus project tadi, MemberInfo() adalah **stateless** karena hanya memiliki props.
Sedangkan App() adalah **stateful** karena memiliki props dan state.

## Menggunakan Bootstrap pada React

- Menggunakan React Bootstrap
- Menggunakan React Biasa

Yang akan dibahas sekarang adalah menggunakan react biasa. Caranya ada 2:

1. Menggunakan versi CDN -> memasang script JS dan stylesheet CSSnya pada _index.html_
2. Install bootstrap melalui npm

Bootstrap tersebut diinstall di dalam direktori projek react yang dituju.

```
npm install bootstrap
```

Berikutnya pada **index.js** import Bootstrap CSS dan Bootstrap Bundle JSnya.

```
import "bootstrap/dist/css/bootstrap.min.css";

import "bootstrap/dist/js/bootstrap.bundle.min";
```

note: cara untuk menggunakan react biasa ini hanya bisa dipilih salah satu, tidak bisa keduanya.

note: Apabila memilih untuk menggunakan Bootstrap biasa pada React, maka harus selalu ingat untuk mengganti nama atribut. Seperti atribut **class** harus ditulis menjadi **className**, dan lain-lain.