<script setup>
    import {ref, defineProps} from 'vue';
    const palavra  =  ref('');
    const dica  =  ref('');
    const currentForm = ref('palavra');
    const props = defineProps({
        state:{
            type: Object,
            required: true,
        }
    })    

    function nextFormInput(evt){
        const input = evt.target.previousElementSibling;

        console.log(input.validity)

        if(input.validity.valueMissing){    

            return;
        }

        if(currentForm.value == 'palavra'){
            currentForm.value = 'dica'
            palavra.value = evt.target.previousElementSibling.value
            evt.target.previousElementSibling.value = '';
        }
        else{
            dica.value = evt.target.previousElementSibling.value
            props.state.gameData = {
                palavra: palavra.value.toLocaleLowerCase(),
                dica: dica.value.toLocaleLowerCase(),
            }
            props.state.tela = 'game'
        }
    }
</script>

<template>
    <form class="form">
        <h1 id="title">Hangman Game</h1>
        <label :for="currentForm">
            Digite a {{currentForm}}:
        </label>
        <input type="text" :id="currentForm" :name="currentForm" minlength="1" required>
        <button type="submit" @click.prevent = "nextFormInput">
            Próximo
        </button>
    </form>
</template>

<style scoped>
    #title{
    color: var(--color-text-title);
    }
    .form{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 1rem;


        text-align: center;

        margin: 2rem;
    }
    .form input{
        width: 100%;
        height: 3rem;
        border-radius: 0.5rem;
    }
    button{
        display: block;
    }
</style>