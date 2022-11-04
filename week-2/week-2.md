# Senin, 31 Oktober 2022

## **Prop Types**

Prop Type digunakan untuk melakukan _type checking_ (mengecek tipe data sebuah props) pada Javascript.

Type checking dilakukan untuk mencegah adanya perbedaan tipe data pada saat Parent melemparkan _props_ ke Childnya (component-nya). Nantinya akan muncul pesan error yang akan memberitahukan adanya error dan di baris mana.

contoh: Pada parent tipe data propsnya adalah String, namun saat dilempar propsnya ke Child, tipe data props yang diterima adalah number.

contoh kasus: Terdapat file **App.jsx** sebagai parent, dan file **StudentInfo.jsx** sebagai childnya.

**StudentInfo.jsx**

<img src="./gambar/1.jpg"/>

**App.jsx**

<img src="./gambar/2.jpg"/>

Maka hasilnya pada browser adalah :

<img src="./gambar/3.jpg"/>

### Cara menggunakan prop-types

1. Install pada folder projek react

```
npm install prop-types
```

2. Import pada Child (component)

```javascript
import PropTypes from "prop-types";
```

<img src="./gambar/4.jpg"/>

3. Tambahkan method propTypes pada function component.

<img src="./gambar/5.jpg"/>

Setelah ada pesan eror, kita jadi mengetahui alasan eror dan dapat membenarkan letak kesalahannya.

### Tipe data "_any_"

Tipe data ini dapat menampung tipe data apa saja.

```javascript
props: PropTypes.any;
```

### .isRequired

.isRequired digunakan utk memberi tahu bahwa harus ada props yang didefinisikan prop-types.

contoh: kita menambahkan prop-types untuk props dengan nama _info_ pada Child, namun ternyata pada Parent tidak ada props yang bernama _info_. Maka ketika kita menggunakan .isRequired akan dimunculkan pesan eror.

```javascript
props: PropTypes.any.isRequired;
```

### .oneOfType

.oneOfType memberikan pilihan kepada props untuk menerima lebih dari satu tipe data.

```javascript
props: PropTypes.any.oneOfType([PropTypes.string, PropTypes.number]);
```

pesan eror yang ditampilkan apabila tipe data yg diinput bukan string atau number

<img src="./gambar/6.jpg"/>

### PropTypes untuk tipe data Array

```javascript
props: PropTypes.array;
```

### Mengecek tipe data unsur sebuah Array menggunakan .arrayOf

1. Memberikan satu tipe data pada unsur array

```javascript
props: PropTypes.arrayOf(PropTypes.number);
```

Pada contoh di atas prop-types diminta untuk mengecek apakah tipe data unsur yang ada di dalam array adalah _number_.

2. Memberikan .oneOfType pada unsur array

```javascript
props: PropTypes.arrayOf(PropTypes.oneOfType([PropTypes.string, PropTypes.number]));
```

### Prop-types untuk Tipe data Object

<img src="./gambar/7.jpg"/>

**info** memiliki tipe data object.

```javascript
info: PropTypes.object;
```

### Mengecek tipe data properti sebuah Object

```javascript
props: PropTypes.shape({
  properti1: PropTypes.string,
  properti1: PropTypes.number,
});
```

### Mengecek nilai dan key dari sebuah Object dengan menggunakan _.exact_

Apabila menggunakan .exact maka prop-types tidak hanya akan memeriksa tipe data dari properti object, namun juga jumlah keynya. Prop types akan memeriksa apakah key yang terdapat pada Parent sudah sesuai dengan key yang dicek pada Child.

contoh: Pada Parent terdapat object dengan 3 properti (key), namun pada saat melakukan type checking pada Child properti (key) yang didefinisikan hanya 2. Dengan menggunakan _.exact_ akan mengecek hal ini. Apabila tidak sesuai maka akan memunculkan pesan eror.

```javascript
props: PropTypes.exact({
  properti1: PropTypes.string,
  properti1: PropTypes.number,
});
```

### Menggabungkan .isRequired pada prop-types object

```javascript
props: PropTypes.exact({
  properti1: PropTypes.string,
  properti1: PropTypes.number,
}).isRequired,
```

# Selasa, 1 November 2022

## Router

Pada SPA, kita tetap bisa berpindah-pindah halaman dengan menggunakan **router**.

<img src="./gambar/selasa-1.png"/>

React Router yg akan digunakan adalah v6, disarankan untuk pemula.

### Proses Instalasi

Pada folder react yang dituju, ketik pada command prompt

```
npm install react-router-dom@6
```

### Proses pemasangan

1. Pada main.jsx atau index.jsx import BrowserRouter

```
import { Browser Router } from react-router-dom
```

2. Pada main.jsx atau index.jsx bungkus <_App_/> dengan <_BrowserRouter_>

<img src="./gambar/selasa-2.png"/>

3. Pada **App.jsx**, import _Routes, Route_, dan _Link_

```
import {Routes, Route, Link} from 'react-router-dom'
```

Kemudian pada bagian return berikan pembungkus <_Routes_>

<img src="./gambar/selasa-5.png"/>

4. Membuat folder 'pages' di dalam folder 'src' untuk menampung file halaman

<img src="./gambar/selasa-3.png"/>

5. Buat HomePage.jsx dan AboutPage.jsx di dalam folder _page_

<img src="./gambar/selasa-4.png"/>

HomePage.jsx

<img src="./gambar/selasa-7.png"/>

6. Di dalam tag <_Routes_> panggil single tag <_Route_>

<img src="./gambar/selasa-6.png"/>

**path** adalah penulisan yang akan muncul pada link ketika halaman yang dipanggil dimuat. Contohnya pada gambar ini, dapat disimpulkan **path**nya adalah **"/bundles"**

<br>
<img src="./gambar/selasa-1.png"/>

Tambahkan juga **element={}** untuk memanggil page yang mau kita tuju. Di sini kita menjadikan HomePage.jsx sebagai halaman yang pertama kali dirender. Oleh karena itu kita dapat mengisi **path="/"**

Cara pemanggilan page **HomePage.jsx** sama seperti ketika kita memanggil component.

<img src="./gambar/selasa-8.png"/>

### Pemasangan Navbar

Jika kita memiliki 4 page, dan kita ingin semua page tersebut memiliki navbar, maka kita dapat memasang navbar pada **App.jsx** tempat di mana kita akan memanggil 4 page tadi. Jadi tidak perlu memasangkan navbar satu-persatu untuk setiap 4 page tadi.

Jika pada HTML biasa kita menggunakan tag <_a_>, pada penggunaan router kita akan gunakan <_Link_> dilengkapi dengan attribute **to**

<img src="./gambar/selasa-9.png"/>

### Params

Params digunakan untuk mengirim data. Format penulisannya adalah "/:params"

Contohnya di sini akan dibuat page DetailPage.jsx

<img src="./gambar/selasa-10.jpg"/>

Lalu pada **App.jsx** dipanggil halaman DetailPage. Kemudian di bagian **path**nya diberikan params berupa **id**

<img src="./gambar/selasa-11.jpg"/>

<br>

Alurnya adalah pada Home Page akan menampilkan list nama-nama siswa, yang mana setiap siswa memiliki halaman detilnya masing-masing. User akan diarahkan ke halaman detil seorang siswa apabila button **Detail** nya diklik. Halaman detil setiap siswa masih akan tetap memiliki navbar yang sudah ada.

Perhatikan ilustrasi di bawah ini.

<img src="./gambar/selasa-12.png"/>

Cara agar menampilkan list nama siswa pada Home Page adalah sebagai berikut :

- Pada **HomePage.jsx** dibuat array of object.

  <img src="./gambar/selasa-13.png"/>

- Kemudian data ditampilkan dengan method .map()

  <img src="./gambar/selasa-14.png"/>

- Kemudian tambahkan event onClick pada button

  ```javascript
  <button onClick={() => handleDetail(el.id)}>Detail</button>
  ```

Cara agar button **Detail** berfungsi dan akan membawa user ke halaman detil siswa

- Membuat function handleDetail yang memiliki parameter _id_

  ```javascript
  const handleDetail = (id) => {};
  ```

- import useNavigate pada **HomePage.jsx**

  ### useNavigate untuk **berpindah halaman** sekaligus melakukan **pengiriman data**

  Kelebihan: lebih mudah digunakan jika kita melakukan pengiriman data. Contohnya untuk halaman detail, (contoh pada Tokopedia) setiap barang jika diklik akan memiliki detailnya sendiri yang akan menampilkan deskripsi lengkap barang, review pembeli, button untuk menambah ke keranjang, dll. Untuk setiap detail.

  ```javascript
  import { useNavigate } from "react-router-dom";
  ```

- menampung useNavigate ke dalam sebuah variabel

  ```javascript
  const navigation = useNavigate();
  ```

- menggunakan **navigation** ke dalam function handeDetail

  ```javascript
  const handleDetail = (id) => {
    navigation(`/detail/${id} `);
  };
  ```

Berikutnya adalah membuat halaman detil menampilkan info setiap siswa. Misalkan setiap siswa memiliki info name, address, dan hobby.

- Pada **DetailPage.jsx** dibuat array of object yang memuat data _name, address,_ dan _hobby_ dari siswa.

<img src="./gambar/selasa-15.png"/>

- Mengirim data menggunakan useParams()

  ### useParams()

  ```javascript
  import { useParams } from "react-router-dom";
  ```

  - Membuat variabel untuk menampung useParams()

    ```javascript
    const { id } = useParams();
    ```

- Pada **return** di **DetailPage.jsx** hanya akan menampilkan data detil siswa yang tombol Detailnya diklik (yg idnya sesuai)

<img src="./gambar/selasa-16.png"/>

## Nested Routing

Nested routing akan terlihat seperti ini

<img src="./gambar/selasa-17.png"/>

Di laman _about_ akan ada button yang mengarahkan ke laman lain lagi, yaitu laman _school_.

1. Laman yang memiliki child akan dibungkus oleh tag _Route_ yang memiliki closing tag.

before :

<img src="./gambar/selasa-18.png"/>

after:

<img src="./gambar/selasa-19.png"/>

2. Link pada laman About

<img src="./gambar/selasa-20.png"/>

# Rabu, 2 November 2022

## Menyamakan Data Profile

<img src="./gambar/rabu-1.png"/>

Data pada component Profile dan component Navbar sama, yaitu sama-sama menampilkan foto profil dari user dan menampilkan nama lengkap user. Bagaimana cara membuat data pada kedua component ini sama?

Caranya adalah dengan meletakkan data pada **App.jsx**. Sehingga nantinya data dari **App.jsx** akan diberikan kepada component Navbar dan Profile. Untuk analoginya, perhatikan gambar di bawah.

<img src="./gambar/rabu-2.png"/>

<br>

Component Nav dan component Profile terbagi menjadi component-component yang lebih kecil lagi.

Pada component Navbar, dapat dipecah menjadi component-component yang lebih kecil lagi, yaitu component menu dan component user profile button.

Sedangkan pada component halaman Profile dapat dipecah lagi menjadi component card profile user, user skillBadge, dan user skillPath.

<br>

<img src="./gambar/rabu-3.png"/>

### Proses pemberian data (Props Dealing)

Props akan dilemparkan dari App ke Nav kemudian ke user profile button. Begitu juga dari Nav dilemparkan ke Profile baru kemudian ke user card.

<img src="./gambar/rabu-4.png"/>

Hal ini dimakan **Props dealing** (props akan dioper dari satu component ke component lainnya).

Permasalahan yang mungkin timbul dari props dealing adalah

Mengatasinya bisa dengan menggunakan **state management**.

<img src="./gambar/rabu-5.png"/>

## Redux

Dari beberapa state management yang ada, kita akan mempelajari salah satunya yaitu **redux**.

Sekarang kita akan membuat code untuk kasus seperti ini:

Ketika kita menambahkan sebuah product ke keranjang, maka notifikasi angka pada logo keranjang di navbar akan bertambah.

### **Membuat component Counter, Keranjang, ListProduct, SummaryPembelian**

<br>

<img src="./gambar/rabu-6.png"/>

### Menampilkan list product

<img src="./gambar/rabu-9.png"/>

**App.jsx**

<img src="./gambar/rabu-7.png"/>

Ketika dijalankan pada browser:

<img src="./gambar/rabu-8.png"/>

## **Pemasangan redux**

Tahapannya:

1. Install redux
2. Buat folder **redux**
3. Di dalam folder redux, buat folder **action**, **reducer**, dan **store**
4. Membuat provider
5. Ambil data dari store

- Instalasi redux pada folder projek react yang dituju

  ```
  npm install redux react-redux
  ```

Setelah itu kita perlu membuat **store**. Store adalah wadah untuk menampung code props yang akan dibagi-bagi datanya untuk banyak component. Di dalam store bisa terdapat beberapa reducer.

Analoginya:

<img src="./gambar/rabu-12.png"/>

- Membuat folder baru bernama **redux**, kemudian buat folder **store** di dalamnya, lalu buat file **index.js** di dalamnya

  <img src="./gambar/rabu-10.png"/>

- Membuat folder **reducer** di dalam folder **redux**, kemudian membuat file **keranjangReducer.js**

  <img src="./gambar/rabu-11.png"/>

- Membuat provider

  Provider seperti memberi jangkauan kepada component apa saja store dapat diakses.

  <img src="./gambar/provider.png"/>

  Karena **App** adalah component utama yang merupakan jalan masuk untuk seluruh component yang akan dibuat (atau dapat dikatakan App sebagai parent), maka kita hanya perlu membungkus App dengan provider. Component **App** dipanggil pada **main.jsx**, maka kita perlu memasangkan provider pada **main.jsx**.

  **main.jsx**

  <img src="./gambar/rabu-13.png"/>

  <br>

- Mengambil data dari store dengan menggunakan **useSelector**

  <img src="./gambar/rabu-14.png"/>

  useSelector akan mengambil data state dari store. Store akan menyediakan reducer yang bernama KeranjangReducer. Sehingga component Keranjang.jsx akan mengambil data dari KeranjangReducer.

## Action

note: pada action jangan lupa untuk memberi keyword _export_ untuk variabel dan function yang berada di dalam file action.

- Membuat folder action pada folder redux

  <img src="./gambar/rabu-15.png"/>

- keranjangAction.js

<img src="./gambar/rabu-17.png"/>

- pada keranjangReducer.js, diimport objek INCREMENT_KERANJANG dan DECREMENT_KERANJANG

- pada component Counter, gunakan **useDispatch**

Dispatch gunanya adalah **mengirim action ke dalam reducer**.

<img src="./gambar/rabu-16.png"/>

<br>

# Kamis, 03 November 2022

**Combined Reducer** -> digunakan ketika kita memiliki lebih dari satu reducer yang ingin dimasukkan ke dalam store.

Contoh pada kasus ini store sudah menampung counterReducer. Sedangkan kita membuat reducer baru, yaitu todoReducer.

Karena sekarang sudah ada lebih dari 1 reducer yang perlu disimpan pada store, maka digunakan combine Reducer.

before:

```javascript
import { createReducer } from "redux";

const store = createReducer(counterReducer);
```

after:

```javascript
import { combineReducer, createReducer } from "redux";

const allReducer = combineReducer({
  counter: counterReducer,
  todo: todoReducer,
});

const store = createReducer(allReducer);
```

Rangkuman:

store.js (tempat membuat store):

- import createStore, combineReducers
- buat variabel allReducer yang diisi dengan combineReducers dan masukkin list reducernya apa-apa aja
- buat store pake createStore, dengan parameternya (allReducer)
- export store

reducer:

- definisiin intialState (untuk simpan data)
- buat fungsi reducernya (samakan nama function dengan nama file)
- parameter function reducer adalah (state - initialState, action)
- di dalam function reducer ada switch case
- export reducer

setelah itu balik lagi ke file store.js

- import file reducer yang mau dipake
- masukkin nama reducernya ke dalam combineReducers

provider (taruh di file index.js atau main.jsx, pokoknya tempat virtual DOM dibuat):

- import Provider
- import store
- bungkus App dengan tag **Provider**
- berikan properti **store={store}** pada opening tag Provider

useSelector pada component yg dituju:

- import useSelector
- buat variable state yang diisi dengan **useSelector** yang akan mengambil properti dari reducer yang dituju

# Jumat, 04 November 2022

## Menggunakan redux yang mengambil data dari mock API

- memberikan properti **isLoading** dan **err** pada initialState di file reducer.

<img src="./gambar/jumat-1.png"/>

- membuat action yg mengambil data dari API menggunakan **thunk**

## Thunk

dispatch(action) tidak bisa melakukan proses asynchronous, oleh karena itu dibutuhkan thunk apabila ingin membuat action yang mengambil data dari reducer yang menggunakan API. **Thunk** adalah **middleware** yang digunakan untuk **membuat function yang bersifat asynchronous**.
