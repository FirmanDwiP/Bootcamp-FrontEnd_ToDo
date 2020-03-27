# MATERI
## Vue CLI
Vue memiliki sebuah CLI (command line interface) yang sangat membantu kamu untuk men-setup project Vue dengan lebih mudah. Jika kamu ingin membuat sebuah project single page application yang scopenya besar sangat disarankan jika kamu menginstall Vue menggunakan CLI. Perbedaan vue.js dengan framework yang lain dapat dilihat di [sini](https://docs.vuejs.id/v2/guide/comparison.html)

#### Install
```sh
sudo npm install -g @vue/cli
```

#### Struktur file dan folder
- src → folder utama
- src/main.js → file yang pertama kali dibaca
- src/App.vue → file .vue yang pertama kali di-load
- src/components → folder untuk menyimpan file component
- public → folder yang bisa diakses langsung oleh khalayak umum, bisa juga digunakan untuk menyimpan file statis seperti CSS, gambar, dan file lainnya.
- node_modules → folder yang dibuat oleh NPM. Berisi source code yang digunakan oleh Vue.js maupun 3rd-party library lainnya
- package.json → File berisi informasi tentang library/package yang digunakan
- src/router → untuk routing
- src/views → file .vue yang digunakan untuk menyimpan tampilan. Berbeda dengan src/components yang digunakan untuk menyimpan component kecil.
- src/store → digunakan untuk menyimpan file Vuex (state management)
- src/assets → menyimpan file asset seperti gambar, file .sass atau .scss.
.
###### NOTE: Kita bebas mengubah struktur file dan folder tergantung dari kebutuhan.
.
#### Mendefinisikan data reactive di Vue.js
```sh
<script>
export default {
  data() {
    return {
    }
  }
}
</script>

```

#### Menampilkan data ke template
```sh
<template>
  <div>
    Nama: {{ name }} / Usia: {{ age }} tahun
  </div>
</template>
```

#### Form model binding dengan v-model
```sh
<template>
  <div>
    Nama: {{ name }} / Usia: {{ age }} tahun

    <input v-model="name" type="text" />
    <input v-model.number="age" type="number"/>
  </div>
</template>

//v-bind shorthand
<abbr :title="Vue.js is great!">Vue.js</abbr>
<abbr v-bind:title="Vue.js is great!">Vue.js</abbr>
```

#### v-for
```sh
<template>
  <ol>
    <li v-for="n in numbers">
      {{ n }}
    </li>
  </ol>
</template>

<script>
export default {
  data: () => ({
    numbers: [1, 2, 3, 4]
  })
}
</script>
```

#### V-if
```sh
<template>
  <ol>
    <li v-for="room in rooms" :key="room.id">
      Kamar nomor: {{ room.roomNumber }}
      <span v-if="room.available">Tersedia</span>
      <span v-else>Tidak Tersedia</span>
    </li>
  </ol>
</template>
```

# client

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your unit tests
```
npm run test:unit
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
