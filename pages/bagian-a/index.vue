<template>
  <div>
    <div>
      <h1 class=" font-bold mb-4 cursor-pointer w-max" @click.prevent="$router.push('/')">&#8592; Bagian A</h1>
    </div>
    <div class="bg-primary-dark min-h-screen flex justify-center">
      <div class="bg-white w-[400px] p-6 shadow rounded-md self-center">
        <div class="mb-4">
          <button @click.prevent="$router.push('/bagian-a/1')"
            class="bg-gray-100 p-4 border rounded-lg w-full hover:bg-blue-500 hover:text-white transition-all ease-in-out duration-300">Soal
            No 1</button>
        </div>
        <div class="mb-4">
          <button @click.prevent="$router.push('/bagian-a/2')"
            class="bg-gray-100 p-4 border rounded-lg w-full hover:bg-blue-500 hover:text-white transition-all ease-in-out duration-300">Soal
            No 2
          </button>
        </div>
        <div>
          <button @click.prevent="$router.push('/bagian-a/3')"
            class="bg-gray-100 p-4 border rounded-lg w-full hover:bg-blue-500 hover:text-white transition-all ease-in-out duration-300">Soal
            No 3
          </button>
        </div>
      </div>
    </div>

  </div>
</template>
<script setup>
</script>
