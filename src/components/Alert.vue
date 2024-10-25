<script setup>
import { computed } from 'vue';

    const props = defineProps({
        alert:{
            type: Object,
            Required: true
        }
    })

    const isError = computed(()=>{
    return props.alert.type === 'Error'
    })

</script>
<template>
    <div 
    :class="[isError ? 'bg-red-500' : `bg-green-500`]"
    class=" text-white text-center p-2 uppercase mb-3 font-bold bg-red-500 rounded-md w-5/6 ml-8">
       {{ alert.message }}
    </div>
</template>