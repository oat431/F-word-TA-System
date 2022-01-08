<template>
  <DefaultLayout>
    <div class="flex ml-3 rounded-md justify-center">
      <button 
        class="inline-flex items-center justify-center px-5 py-3 text-base font-medium leading-6 text-white transition duration-150 ease-in-out bg-green-500 border border-transparent rounded-md hover:bg-green-600 focus:outline-none"
      >
        Gen Pdf 
      </button>
    </div>
  </DefaultLayout>
  
</template>

<script>
import DefaultLayout from '@/layouts/DefaultLayout.vue' 
export default {
  components : {
    DefaultLayout,
  }, 
}
</script>