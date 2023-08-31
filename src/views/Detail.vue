<template>
    <div class="w-screen bg-white pt-20">
      <main class="relative mx-auto px-10 md:max-w-screen-md">
        <div class="top-20 -left-56 mb-10 w-full max-w-xs rounded-md border bg-white px-7 py-7 shadow-md lg:absolute lg:w-70">
          <div class="pb-2 text-xl font-medium text-red-600">Tambah Foto</div>
          <hr class="h-1 w-10 bg-red-700" />
      <div>
        <form @submit.prevent="uploadPhoto">
          <label for="photo">Upload Foto:</label>
          <input type="file" id="photo" ref="photoInput">
          <button type="submit">Upload</button>
        </form>
      </div>
    </div>
    <form class="mx-auto w-full max-w-xl border-gray-200 px-10 py-8 md:px-8">
        <div class="pb-2 text-xl font-medium text-orange-600">Informasi Umum</div>
        <h1>Nomor</h1>
        <p>#01</p>
        <br>
            <div class="mb-4"><label class="text mb-2 block font-medium" for="email">Nama:</label><input class="w-full rounded border border-gray-300 px-3 py-2 outline-none ring-blue-500 focus:ring" id="email" type="email" /></div>
            <div class="grid gap-3 lg:grid-cols-2">
        <div>
          <label class=""> Types </label>
          <div class="relative w-56 mt-2 bg-gray-100 rounded-lg">
            <input class="peer hidden" type="checkbox" name="select-1" id="select-1" />
            <label for="select-1" class="flex w-full cursor-pointer rounded-lg select-none border p-2 px-3 text-sm text-gray-700 ring-blue-400 peer-checked:ring">Select Option </label>
            <svg xmlns="http://www.w3.org/2000/svg" class="pointer-events-none absolute right-5 top-3 h-4 text-gray-600 transition peer-checked:rotate-180" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M19 9l-7 7-7-7" />
            </svg>
            <ul class="max-h-0 select-none flex-col overflow-hidden rounded-b-lg shadow-md transition-all duration-300 peer-checked:max-h-56 peer-checked:py-3">
              <li class="cursor-pointer px-3 py-2 text-sm text-gray-500 hover:bg-blue-500 hover:text-white">Flying</li>
            </ul>
          </div>
        </div>
        </div>
              <br>
              <br>
        <div class="grid gap-3 lg:grid-cols-2">
          <div>
          <label class=""> Classification </label>
          <div class="relative w-56 mt-2 bg-gray-100 rounded-lg">
            <input class="peer hidden" type="checkbox" name="select-2" id="select-2" />
            <label for="select-2" class="flex w-full cursor-pointer rounded-lg select-none border p-2 px-3 text-sm text-gray-700 ring-blue-400 peer-checked:ring">Select Option </label>
            <svg xmlns="http://www.w3.org/2000/svg" class="pointer-events-none absolute right-5 top-3 h-4 text-gray-600 transition peer-checked:rotate-180" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M19 9l-7 7-7-7" />
            </svg>
            <ul class="max-h-0 select-none flex-col overflow-hidden rounded-b-lg shadow-md transition-all duration-300 peer-checked:max-h-56 peer-checked:py-3">
              <li class="cursor-pointer px-3 py-2 text-sm text-gray-500 hover:bg-blue-500 hover:text-white">Seed Pokemon</li>
            </ul>
          </div>
        </div>
        <div>
        </div>
        </div>
              <br>
              <br>
        <div class="grid gap-3 lg:grid-cols-2">
        <div>
          <label class=""> Resistant </label>
          <div class="relative w-56 mt-2 bg-gray-100 rounded-lg">
            <input class="peer hidden" type="checkbox" name="select-3" id="select-3" />
            <label for="select-3" class="flex w-full cursor-pointer rounded-lg select-none border p-2 px-3 text-sm text-gray-700 ring-blue-400 peer-checked:ring">Select Option </label>
            <svg xmlns="http://www.w3.org/2000/svg" class="pointer-events-none absolute right-5 top-3 h-4 text-gray-600 transition peer-checked:rotate-180" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M19 9l-7 7-7-7" />
            </svg>
            <ul class="max-h-0 select-none flex-col overflow-hidden rounded-b-lg shadow-md transition-all duration-300 peer-checked:max-h-56 peer-checked:py-3">
              <li class="cursor-pointer px-3 py-2 text-sm text-gray-500 hover:bg-blue-500 hover:text-white">Water</li>
              <li class="cursor-pointer px-3 py-2 text-sm text-gray-500 hover:bg-blue-500 hover:text-white">Electric</li>
              <li class="cursor-pointer px-3 py-2 text-sm text-gray-500 hover:bg-blue-500 hover:text-white">Grass</li>
            </ul>
          </div>
        </div>
        <div>
        </div>
        </div>
        <br>
        <div class="flex items-center">
            <div class="flex-2"></div>
            <button class="rounded-xl bg-blue-600 px-4 py-3 text-center font-bold text-white hover:bg-blue-700" type="submit">Tambah</button>
        </div>
          </form>

      </main>
    </div>

</template>

<script>
import axios from 'axios';

export default {
    methods: {
        async uploadPhoto() {
            const photoInput = this.$refs.photoInput;
            if (!photoInput.files.length) {
                alert("Silahkan pilih foto terlebih dahulu!");
                return;
            }

            const formData = new FormData();
            formData.append('photo', photoInput.files[0]);

            try {
                const response = await axios.post('YOUR_API_ENDPOINT', formData, {
                    headers: {
                        'Content-Type': 'multipart/form-data'
                    }
                });

                // Handle response sesuai kebutuhan
                console.log(response.data);
            } catch (error) {
                console.error("Error uploading photo:", error);
            }
        }
    }
}
</script>