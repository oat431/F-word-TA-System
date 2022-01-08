<template>
  <TA/> 
  <Course v-for="item in course" :key="item" :name="item"/>

  <div class="grid grid-cols-1 gap-6 mt-4 sm:grid-cols-2">
    <AddCourse :addCourse="addCourse"/>
    <GenPdf/>
  </div>
</template>

<script>
import TA from '@/components/TA.vue'
import Course from '@/components/Course.vue'
import AddCourse from '@/components/ButtonRepo.vue'
import GenPdf from '@/components/GenPdf.vue'
export default {
  data(){
    return {
      course : [],
      number : 1
    }
  },
  components : {
    TA,
    Course,
    AddCourse,
    GenPdf
  },
  methods : {
    addCourse(){
      if(this.course.length < 3){
        this.course.push(this.number);
        this.number++;
      }
    }
  } 
}
</script>