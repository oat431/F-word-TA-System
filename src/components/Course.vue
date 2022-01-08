<template>
    <DefaultLayout>
      <section class="max-w-4xl p-6 mx-auto bg-white rounded-md shadow-md">
        <h2 class="text-lg font-semibold text-gray-700 capitalize">Course {{name}}</h2>
        
        <Form @submit="handleRegister" :validation-schema="schema">
            <div class="grid grid-cols-1 gap-6 mt-4 sm:grid-cols-1">
                <div>
                    <label class="text-gray-700" for="courseID">Course ID</label>
                    <Field name="courseID" type="text" class="block w-full px-4 py-2 mt-2 text-gray-700 bg-white border border-gray-300 rounded-md focus:border-blue-500 focus:outline-none focus:ring"/>
                    <ErrorMessage name="courseID" class="text-red-500"/>
                </div>
            </div>
            <div class="grid grid-cols-1 gap-6 mt-4 sm:grid-cols-1">
                <div>
                    <label class="text-gray-700" for="working">Working Day</label>
                    <Field name="working" as="select" :v-slot="{working}" class="block w-full px-4 py-2 mt-2 text-gray-700 bg-white border border-gray-300 rounded-md focus:border-blue-500 focus:outline-none focus:ring" >
                        <option value="M-Th">M-TH</option>
                        <option value="Tue-Fri">Tue-Fri</option>
                        <option value="Web">Web</option>
                        <option value="Fri">Fri</option>
                    </Field>
                    <ErrorMessage name="working" class="text-red-500"/>
                </div>
            </div>
            <div class="grid grid-cols-1 gap-6 mt-4 sm:grid-cols-2">
                <div>
                    <label class="text-gray-700" for="startTime">Start time</label>
                    <Field name="startTime" type="time" class="block w-full px-4 py-2 mt-2 text-gray-700 bg-white border border-gray-300 rounded-md focus:border-blue-500 focus:outline-none focus:ring"/>
                    <ErrorMessage name="startTime" class="text-red-500"/>
                </div>

                <div>
                    <label class="text-gray-700" for="endTime">End Time</label>
                    <Field name="endTime" type="time" class="block w-full px-4 py-2 mt-2 text-gray-700 bg-white border border-gray-300 rounded-md focus:border-blue-500 focus:outline-none focus:ring"/>
                    <ErrorMessage name="endTime" class="text-red-500"/>
                </div>
            </div>
            <div class="grid grid-cols-1 gap-6 mt-4 sm:grid-cols-1">
                <div>
                    <label class="text-gray-700" for="description">description</label>
                    <Field name="description" type="text" class="block w-full px-4 py-2 mt-2 text-gray-700 bg-white border border-gray-300 rounded-md focus:border-blue-500 focus:outline-none focus:ring"/>
                    <ErrorMessage name="description" class="text-red-500"/>
                </div>
            </div>

            <div class="flex justify-end mt-6">
                <button class="px-6 py-2 leading-5 text-white transition-colors duration-200 transform bg-green-500 rounded-md hover:bg-green-600 focus:outline-none focus:bg-green-600">Confirm</button>
            </div>
        </Form>
      </section>
    </DefaultLayout>
</template>


<script>
import DefaultLayout from '@/layouts/DefaultLayout.vue'
import { Form, Field, ErrorMessage } from 'vee-validate'
// import RegisterService from '../services/registerAPI'
import * as yup from 'yup'
export default {
    name:"Course Part",
    components:{
        DefaultLayout,
        Form,
        Field,
        ErrorMessage
    },
    props: {
        name:''
    },
    data(){
        const schema = yup.object().shape({
            courseID :
            yup.string()
            .required('Course ID is require!')
            .min(3,'Must be at least 3 characters!')
            .max(20, 'Must be maximum 20 characters'),
            working : yup.string()
            .required("The working day is require"),
            startTime :
            yup.string()
            .required("your start working time is required!"),
            endTime : 
            yup.string()
            .required("your working end time is required!"),
            description :
            yup.string()
        })
        return {
            working:'',
            schema
        }
    },
    methods:{
        handleRegister(user){
            RegisterService.register(user)
            .then(()=>{
                this.$router.push({name:'LandingPage'})
            }).catch(()=>{
                console.log("could not register")
            })            
        }
    }
}
</script>