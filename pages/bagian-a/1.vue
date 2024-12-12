<template>
  <div>
    <div>
      <h1 class=" font-bold mb-4 cursor-pointer w-max" @click.prevent="$router.go(-1)">&#8592; Bagian A No 1 </h1>
    </div>
    <div class="w-1/2 rounded-md p-4 mx-auto border">
      <p>
        Anda sedang bekerja pada proyek web yang menggunakan HTML, CSS, dan
        JavaScript. Anda perlu membuat sebuah tombol yang memiliki efek hover
        berupa perubahan warna latar belakang. Bagaimana Anda akan
        menerapkannya menggunakan CSS?
      </p>
      <div class="my-6">
        <button class="button_hover">Hover Me!</button>
      </div>
      <p>Dengan menambah attribute class di button lalu styling menggunakan css</p>
    </div>
  </div>
</template>
<style>
.button_hover {
  padding: 10px 20px;
  font-size: 16px;
  border: 2px solid #3498db;
  background-color: #3498db;
  color: white;
  cursor: pointer;
  transition: background-color 0.3s ease;
  border-radius: 5px;
  width: 100%;
}

.button_hover:hover {
  background-color: #2980b9;
}
</style>
