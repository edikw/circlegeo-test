<template>
  <div>
    <div>
      <h1 class="font-bold mb-4 cursor-pointer w-max" @click.prevent="$router.go(-1)">&#8592; Bagian A No 2</h1>
    </div>
    <div class="md:w-1/2 rounded-md p-4 mx-auto border">
      <p>
        Saat mengembangkan aplikasi web, Anda perlu mengoptimalkan performa
        dengan meminimalkan jumlah permintaan HTTP. Bagaimana Anda akan
        menggabungkan beberapa file CSS dan JavaScript menjadi satu file untuk
        mempercepat waktu muat halaman? Jelaskan langkah-langkahnya dan
        berikan contoh implementasinya.
      </p>
      <div class="my-6 text-sm border p-4 rounded-md">
        <h1 class="mb-2 font-bold">Nuxtjs</h1>
        <div class="mb-4">
          <p>1. Tambahkan File CSS di <span class="font-bold">assets/css/main.css</span></p>
          <p>2. Tambahkan File JS di <span class="font-bold">plugins/my-plugins.js</span></p>
          <p>3. Edit File <span class="font-bold">nuxt.config.ts</span> untuk mengimpor file CSS dan plugin Javascript
          </p>
          <p>4. Build Proyek <span class="font-bold">npm run build</span> untuk menggabungkan dan meminimalkan file</p>
        </div>
        <div class="mb-4">
          <p>Dengan langkah-langkah ini, Nuxt.js akan secara otomatis menggabungkan dan meminimalkan file CSS dan
            JavaScript selama proses build, sehingga mengoptimalkan performa aplikasi web.</p>
        </div>
      </div>
      <div class="my-6 text-sm border p-4 rounded-md">
        <h1 class="mb-2 font-bold">Menggunakan Webpack</h1>
        <div class="mb-4">
          <p>1. Instalasi Webpack dan Dependensi:</p>
          <div class="bg-gray-100 p-2 rounded">
            <p>npm install --save-dev webpack webpack-cli style-loader css-loader babel-loader @babel/core
              @babel/preset-env</p>
          </div>
        </div>
        <div class="mb-4">
          <p>2. Buat Struktur Proyek:</p>
          <pre class="bg-gray-100 p-2 rounded"><code>project/
├── src/
│   ├── index.js
│   ├── style.css
├── dist/
├── webpack.config.js
├── package.json</code></pre>
        </div>
        <div class="mb-4">
          <p>3. Konfigurasi Webpack:</p>
          <pre class="bg-gray-100 p-2 rounded"><code>const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist'),
  },
  module: {
    rules: [
      {
        test: /\.css$/,
        use: ['style-loader', 'css-loader'],
      },
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: ['@babel/preset-env'],
          },
        },
      },
    ],
  },
};</code></pre>
        </div>
        <div class="mb-4">
          <p>4. Buat File Sumber:</p>
          <pre class="bg-gray-100 p-2 rounded"><code>// src/index.js
import './style.css';

console.log('Hello, Webpack!');</code></pre>
          <pre class="bg-gray-100 p-2 rounded"><code>/* src/style.css */
body {
  background-color: lightblue;
}</code></pre>
        </div>
        <div class="mb-4">
          <p>5. Build Proyek:</p>
          <pre class="bg-gray-100 p-2 rounded"><code>"scripts": {
  "build": "webpack"
}</code></pre>
          <pre class="bg-gray-100 p-2 rounded"><code>npm run build</code></pre>
        </div>
        <div class="mb-4">
          <p>6. Gunakan File yang Digabungkan:</p>
          <pre class="bg-gray-100 p-2 rounded"><code>&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
&lt;head&gt;
  &lt;meta charset="UTF-8"&gt;
  &lt;meta name="viewport" content="width=device-width, initial-scale=1.0"&gt;
  &lt;title&gt;Optimized Web&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
  &lt;script src="dist/bundle.js"&gt;&lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;</code></pre>
        </div>
        <div class="mb-4">
          <p>Dengan langkah-langkah ini, dapat menggabungkan dan meminimalkan file CSS dan JavaScript menggunakan
            Webpack, sehingga mengoptimalkan performa aplikasi web.</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
</script>

<style scoped></style>
