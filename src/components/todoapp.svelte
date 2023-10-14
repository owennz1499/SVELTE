<script>
    import Todolistcontrolls from "./todolistcontrolls.svelte";
    import Todoitem from "./todoitem.svelte";
	import { onMount } from "svelte"


    let items = [];
    let id = 0;


  onMount(() => {
    if(localStorage.key('items')) {
        items = JSON.parse(localStorage.getItem('items'))
    }
    if(items.length) {
    items.forEach((i) => {
        if (id < i.id) {
            id  =  i.id;
        }
    });
    id=id++;
  }
    });

   function onchangestatus(event) {
    const item = items.find((i) => i.id === event.detail.id );
    item.isDone = !item.isDone;
    items = items;
    localStorage.setItem('items', JSON.stringify(items));
   }


   function onadditem(event) {
    const item = {
        id: id++,
        Text: event.detail.Text,
        isDone:false
   };
   
   items.push(item);
   items = items;
   localStorage.setItem('items', JSON.stringify(items));
}

function ondeleteitem(event) {
    const idx = items.findIndex((i) => i.id === event.detail.id);
    items.splice(idx, 1);
    items = items;
    localStorage.setItem('items', JSON.stringify(items));
   };
</script>
    <div class="todolist">
        <Todolistcontrolls on:add = {onadditem} />
            <div class="todolistfield">
                {#each items as item}
                    <Todoitem id={item.id} Text={item.Text} isDone={item.isDone} on:change={onchangestatus} on:remove={ondeleteitem}/>
                {/each}
             </div>
    </div>
<style>
    .todolist {
        background: #595a5a;
        border-radius: 15px;
        height: 50%;
        width: 600px;
        padding: 40px 60px ;
        display: flex;
        flex-direction: column;
        gap: 20px;
        margin-top: 120px;
        overflow-y: auto;
    }

    .todolistfield {
    background: rgb(110, 95, 95);
    border-radius: 15px;
    display: flex;
    flex-direction: column;
    gap: 10px;
    padding: 20px;
    flex-grow: 1;
    }
</style>