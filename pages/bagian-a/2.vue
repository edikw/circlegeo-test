<template>
  <div>
    <div>
      <h1 class=" font-bold mb-4 cursor-pointer w-max" @click.prevent="$router.go(-1)">&#8592; Bagian A No 2 </h1>
    </div>
    <div class="w-1/2 rounded-md p-4 mx-auto border">
      <p>
        Saat mengembangkan aplikasi web, Anda perlu mengoptimalkan performa
        dengan meminimalkan jumlah permintaan HTTP. Bagaimana Anda akan
        menggabungkan beberapa file CSS dan JavaScript menjadi satu file untuk
        mempercepat waktu muat halaman? Jelaskan langkah-langkahnya dan
        berikan contoh implementasinya.
      </p>
      <div class="my-6 text-sm border p-4 rounded-md">
        <h1 class="mb-2 font-bold">Case Menggunakan Nuxtjs</h1>
        <div class="mb-4">
          <p>1. Tambahkan File CSS di <span class="font-bold">assets/css/main.css</span></p>
          <p>2. Tambahkan File JS di <span class="font-bold">plugins/my-plugins.js</span></p>
          <p>3. Edit File nuxt.config.ts untuk mengimpor file CSS dan plugin Javascript</p>
          <p>4. Build Proyek <span class="font-bold">npm run build</span> untuk menggabungkan dan meminimalkan file</p>
        </div>
        <div class="mb-4">
          <p>Dengan langkah-langkah ini, Nuxt.js akan secara otomatis menggabungkan dan meminimalkan file CSS dan
            JavaScript selama proses build, sehingga mengoptimalkan performa aplikasi web.</p>
        </div>
        <p class="text-xs text-orange-500 font-bold">Untuk Pengimplementasian,bisa dilihat di project ini</p>
      </div>
    </div>
  </div>
</template>
