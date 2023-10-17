<script> 
 export let id;
 export let isDone;
 export let Text;
 import { createEventDispatcher } from 'svelte';

 const dispatch = createEventDispatcher();

</script>

<div class="todoitem" class:todoitem__done={isDone}>
<input class="todoitem__check" 
 type ="checkbox" 
 on:change={dispatch('change', {id})}
 checked = {isDone}
 />
 <span class="todoitem__text">{Text}</span>
 <button class="todoitem__btn" on:click={dispatch('remove', {id})}>Del</button>
 </div>

<style>
    .todoitem {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .todoitem__check {
    height: 40px;
    }

    .todoitem__text {
        display: flex;
        flex-grow: 1;
        justify-content: center;
    }

    .todoitem__btn {
        border: none;
        height: 30px;
        border-radius: 40px;
        background-color: red;
    }

    .todoitem__done .todoitem__text {
        background: rgb(143, 218, 143);
        border-radius: 30px;
    }
</style>