<script>
const dispatch = createEventDispatcher();
 export let text;
          export let id;
          export let isDone;
          export let Text;

import { createEventDispatcher } from 'svelte';

const dispatch = createEventDispatcher();

</script>

<div class="todoitem" class:todoitem__done={isDone}>
<input class="todoitem__check" type ="checkbox" on/>
<span class="todoitem__text">{Text}</span>
<button class="todoitem__btn" on:click=>Del</button>
</div>

<style>
    .todoitem {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .todoitem__check {
    height: 20px;
    }

    .todoitem__text {
        display: flex;
        flex-grow: 1;
        justify-content: center;
    }

    .todoitem__btn {
        border: none;
        height: 30px;
        border-radius: 10px;
        background-color: red;
    }

    .todoitem__done .todoitem__text {
        background: rgb(143, 218, 143);
    }
</style>