<script setup>
import { reactive } from 'vue';
import Alert from './Alert.vue';

const alert = reactive({
    message:'',
    type:''
})
 defineEmits(['update:name', 'update:owner', 'update:email', 'update:date', 'update:symptoms'])

 const props = defineProps({
    name:{
        type:String,
        Required: true
    },
    owner:{
    type:String,
        Required: true
    }
    ,
    email:{
        type:String,
        Required: true
    },
    date:{
        type:Date,
        Required: true
    }
 })

const validate =()=>{
  if(Object.values(props).includes('')){
    alert.message = 'All Inputs are required'
    alert.type = 'Error'
    return
  }
}
</script>
<template>
    <div class="md:w-1/2">
    <h2 class="font-black text-3xl text-center">patients’ Follow-up </h2>
    <p class="text-center mb-8 text-lg mt-4 ">Add and Manage<span class=" text-rose-500 font-bold"> patients </span></p>
    <Alert v-if="alert.message"
    :alert="alert"/>
    <form class="bg-white shadow-md rounded-lg py-6 mb-10 w-5/6 ml-8" @submit.prevent="validate">
        <div class="mx-5">
            <label for="Pet" class="block text-gray-700 font-bold">
                NAME OF PET
            </label>
            <input type="text" id="pet" placeholder="NAME OF PET" class="border-2 w-full rounded-md mt-1 p-1" @input="$emit('update:name', $event.target.value)"
            :value="name">
        </div> 
        <div class="mx-5">
            <label for="Owner" class="block text-gray-700 font-bold">
                OWNER
            </label>
            <input type="text" id="Owner" placeholder=" Name of the Owner" class="border-2 w-full rounded-md mt-1 p-1" @input="$emit('update:owner', $event.target.value)"
            :value="owner">
        </div> 
        <div class="mx-5 my-1">
            <label for="Pet" class="block text-gray-700 font-bold">
                EMAIL
            </label>
            <input type="Email" id="Email" placeholder="Email" class="border-2 w-full rounded-md mt-1 p-1" @input="$emit('update:email', $event.target.value)" :value="email">
        </div> 
        <div class="mx-5 my-1">
            <label for="Date" class="block text-gray-700 font-bold">
                DATE 
            </label>
            <input type="date" id="Date" class="border-2 w-full rounded-md mt-1 p-1" @input="$emit('update:date', $event.target.value)" :value="date">
        </div> 
        <div class="mx-5 my-1">
            <label for="Symptoms" class="block text-gray-700 font-bold">
                SYMPTOMS
            </label>
            <textarea id="Symptoms" class="border-2 w-full rounded-md mt-1 p-1 h-30"  placeholder="Add all Symptoms" @input="$emit('update:symptoms', $event.target.value)" :value="symptoms"/>
        </div>
        <input type="submit" class="bg-rose-400 hover:bg-rose-500 rounded-md text-white p-3 cursor-pointer mx-auto flex items-center w-max transition-colors" value="Register Patient">
    </form>
    </div>
</template>

<style scoped>

</style>