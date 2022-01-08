<template>
    <DefaultLayout>
      <section class="max-w-4xl p-6 mx-auto bg-white rounded-md shadow-md">
        <h2 class="text-lg font-semibold text-gray-700 capitalize">TA Part</h2>
        
        <Form @submit="handleRegister" :validation-schema="schema">
            <div class="grid grid-cols-1 gap-6 mt-4 sm:grid-cols-1">
                <div>
                    <label class="text-gray-700" for="studentid">StudentID</label>
                    <Field name="studentid" type="text" class="block w-full px-4 py-2 mt-2 text-gray-700 bg-white border border-gray-300 rounded-md focus:border-blue-500 focus:outline-none focus:ring"/>
                    <ErrorMessage name="studentid" class="text-red-500"/>
                </div>
            </div>
            <div class="grid grid-cols-1 gap-6 mt-4 sm:grid-cols-2">
                <div>
                    <label class="text-gray-700" for="firstname">Firstname</label>
                    <Field name="firstname" type="text" class="block w-full px-4 py-2 mt-2 text-gray-700 bg-white border border-gray-300 rounded-md focus:border-blue-500 focus:outline-none focus:ring"/>
                    <ErrorMessage name="firstname" class="text-red-500"/>
                </div>

                <div>
                    <label class="text-gray-700" for="lastname">Lastname</label>
                    <Field name="lastname" type="text" class="block w-full px-4 py-2 mt-2 text-gray-700 bg-white border border-gray-300 rounded-md focus:border-blue-500 focus:outline-none focus:ring"/>
                    <ErrorMessage name="lastname" class="text-red-500"/>
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
    name:"TA part",
    components:{
        DefaultLayout,
        Form,
        Field,
        ErrorMessage
    },
    data(){
        const schema = yup.object().shape({
            studentid :
            yup.string()
            .required('StudentID is required!')
            .min(3,'Must be at least 3 characters!')
            .max(9, 'Must be maximum 20 characters'),
            firstname :
            yup.string()
            .required("your firstname is required!")
            .min(2,'Your name need to be at least 2 character')
            .max(50,'No one have that much long firstname'),
            lastname : 
            yup.string()
            .required("your lastname is required!")
            .min(2,'Your lastname need to be at least 2 character')
            .max(50,'No one have that much long lastname'),
        })
        return {
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