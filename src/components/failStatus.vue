<script setup>
    import {ref, defineProps} from 'vue';

    const props = defineProps({
        fails:{
            type: String,
            required: false,
        },
    })
    
</script>

<template>
    <div>
        <img :src="props.fails" alt="Fail Status">
    </div>
</template>

<style scoped>
    div{
        width: 100%;
    }
    img{
        width: 100%;
    }

</style>