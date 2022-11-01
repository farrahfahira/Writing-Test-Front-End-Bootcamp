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
import { Broser Router } from react-router-dom
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

### useNavigate untuk **berpindah halaman** sekaligus melakukan **pengiriman data**

Kelebihan: lebih mudah digunakan jika kita melakukan pengiriman data. Contohnya untuk halaman detail, (contoh pada Tokopedia) setiap barang jika diklik akan memiliki detailnya sendiri yang akan menampilkan deskripsi lengkap barang, review pembeli, button untuk menambah ke keranjang, dll. Untuk setiap detail.

```javascript
import { useNavigate } from "react-router-dom";
```

### useParams()

```javascript
import { useParams } from "react-router-dom";
```

### Nested Routing
