# Senin, 31 Oktober 2022

## **Prop Types**

Prop Type digunakan untuk melakukan _type checking_ (mengecek tipe data sebuah props) pada Javascript.

Type checking dilakukan untuk mencegah adanya perbedaan tipe data pada saat Parent melemparkan _props_ ke Childnya (component-nya). Nantinya akan muncul pesan error yang akan memberitahukan adanya error dan di baris mana.

contoh: Pada parent tipe data propsnya adalah String, namun saat dilempar propsnya ke Child, tipe data props yang diterima adalah number.

contoh kasus: Terdapat file **App.jsx** sebagai parent, dan file **StudentInfo.jsx** sebagai childnya.

<img src=".png"/>

<img src=".png"/>

### Cara menggunakan prop-types

1. Install pada folder projek react

```
npm install prop-types
```

2. Import pada Child (component)

```javascript
import PropTypes from "prop-types";
```

<img src=".png"/>

3. Tambahkan method proptypes pada function component.

<img src=".png"/>

Setelah ada pesan eror, kita jadi mengetahui alasan eror dan dapat membenarkan letak kesalahannya.

Di sini code **App.js** akan dibenarkan setelah mendapat pesan error.

<img src=".png"/>

### Tipe data "_any_"

Tipe data ini dapat menampung tipe data apa saja.

```javascript
props: PropTypes.any;
```

### .isRequired

.isRequired digunakan utk memberi tahu bahwa harus ada data yang diinput pada props.

```javascript
props: PropTypes.any.isRequired;
```

### .oneOfType

.oneOfType memberikan pilihan kepada props untuk menerima lebih dari satu tipe data.

```javascript
props: PropTypes.any.oneOfType([PropTypes.string, PropTypes.number]);
```

pesan eror yang ditampilkan apabila tipe data yg diinput bukan string atau number

<img src=".png"/>

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

<img src>

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
