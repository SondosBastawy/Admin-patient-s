<script setup>
import { ref,reactive } from 'vue';
import Form from './components/Form.vue';
import Header from './components/Header.vue';

const patients = ref([]) 

  const patient = reactive({
    name: '',
    owner:'',
    email:'',
    date:'',
    symptoms:''
})
</script>

<template>
  <div class="container mx-auto pt-8">
    <Header/>
    <div class="mt-12 px-12 md:flex">
      <Form
      v-model:name="patient.name"
      v-model:owner="patient.owner"
      v-model:email="patient.email"
      v-model:date="patient.date"
      v-model:symptoms="patient.symptoms"/>
      <div class="md:w-1/2 overflow-y-scroll bg-green-500">
        <h3 class="font-black text-3xl text-center"> Manage your Patients</h3>
        <div v-if="patients.length > 0">

        </div>
        <div v-else>
        <p class="mt-20 text-3xl text-center font-bold">You do not have any <span class="text-rose-500">Patients</span></p>
        </div>
    </div>
    </div>
    
  </div>
</template>

