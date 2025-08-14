<script lang="ts">

    let {index, removeTask} : {index: number, removeTask: (index: number)=> void }= $props();

</script>

<button onclick={()=> removeTask(index)}>Remove</button>

<style>
    button {
        height: 30px;
        width: 5rem;
    }
    button:hover {
        background: rgb(171, 10, 10);
        border-radius: inherit;
    }
</style>