<template>
  <div class="bg-primary-dark min-h-screen flex justify-center">
    <div class="bg-white w-[400px] p-6 shadow rounded-md self-center">
      <div class="mb-4">
        <button @click.prevent="$router.push('/bagian-a')"
          class="bg-gray-100 p-4 border rounded-lg w-full hover:bg-blue-500 hover:text-white transition-all ease-in-out duration-300">Bagian
          A</button>
      </div>
      <div>
        <button @click.prevent="$router.push('/bagian-b')"
          class="bg-gray-100 p-4 border rounded-lg w-full hover:bg-blue-500 hover:text-white transition-all ease-in-out duration-300">Bagian
          B</button>
      </div>
    </div>
  </div>
</template>
<script setup>
</script>
