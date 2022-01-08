<template>
  <DefaultLayout>
    <div class="flex ml-3 rounded-md justify-center">
      <button 
        class="inline-flex items-center justify-center px-5 py-3 text-base font-medium leading-6 text-green-500 transition duration-150 ease-in-out bg-white border border-transparent rounded-md hover:bg-emerald-200 hover:text-green-700 focus:outline-none"
        @click="addCourse"   
      >
        <svg 
          class="h-10 w-10"
          width="18"
          height="18"
          viewBox="0 0 24 24"
          stroke-width="2"
          stroke="currentColor"
          fill="none"
          stroke-linecap="round"
          stroke-linejoin="round"
        >  
          <path stroke="none" d="M0 0h24v24H0z"/>  
          <circle cx="12" cy="12" r="9" />  
          <line x1="9" y1="12" x2="15" y2="12" />  
          <line x1="12" y1="9" x2="12" y2="15" />
        </svg>
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
  props: {
    addCourse: { type: Function },
  },
  mounted() {
    this.addCourse();
  }
}
</script>