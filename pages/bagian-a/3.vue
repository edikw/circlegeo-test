<template>
  <div>
    <h1 class="font-bold mb-4 cursor-pointer w-max" @click.prevent="$router.go(-1)">&#8592; Bagian A No 2</h1>
    <div class="w-1/2 rounded-md p-4 mx-auto border">
      <p>
        Sebagai frontend developer, Anda bertanggung jawab untuk memastikan
        bahwa aplikasi web yang Anda bangun dapat diakses oleh pengguna dengan
        berbagai kebutuhan aksesibilitas. Bagaimana Anda akan memastikan bahwa
        sebuah tombol pada halaman web Anda dapat diakses dengan mudah
        melalui keyboard dan dapat diakses dengan perangkat pembaca layar?
        Jelaskan teknik dan praktik terbaik yang akan Anda terapkan dalam situasi
        ini.
      </p>
      <div class="my-6 text-sm border p-4 rounded-md">
        <div class="mb-4 w-full">

          <button class="btn w-full" @click="handleClick" aria-label="Klik untuk melakukan tindakan">Klik Saya</button>
        </div>
        <div>
          <p>1 Gunakan elemen <span class="font-bold">
              button
            </span> untuk tombol. Elemen ini secara otomatis dapat diakses oleh keyboard
            dan pembaca
            layar.</p>
          <p>2. Gunakan atribut ARIA (Accessible Rich Internet Applications) untuk memberikan informasi tambahan kepada
            pembaca layar.</p>
          <p>3. Gunakan CSS untuk Indikator Fokus yang Jelas <span class="font-bold">button:focus</span></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const handleClick = () => {
  alert('Tombol diklik!');
};
</script>

<style>
button:focus {
  outline: 2px solid blue;
}
</style>
