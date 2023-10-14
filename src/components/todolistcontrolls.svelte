<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher(); 

    let inputvalue = '';
    function onclick() {
        if (inputvalue.length) {
            dispatch('add', {text: inputvalue});
            inputvalue = '';
        }
    }
</script>


<div class="todolistcontrols">
    <input class="todolistinput" type="text" id="example" bind:value = {inputvalue} />
    <button class="todolistbutton" on:click={onclick}>Добавить</button>
</div>

<style>
     .todolistcontrols {
        display: grid;
        grid-template-columns: 70% 30%;
    
    }

    .todolistinput {
        border: none;
        border-radius: 15px 0px 0px 15px;
        padding: 20px 10px;
    }
    
    .todolistbutton {
        background-color: rgb(146, 94, 94);  
        border-radius: 0px 15px 15px 0px;
        border:none;
    
    }
</style>