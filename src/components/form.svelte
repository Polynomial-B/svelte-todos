<script lang="ts">
    let newTask = $state("")
    let { addTask } : { addTask: (newTask : string) => void } = $props();


    function onsubmit(e: SubmitEvent) {
        e.preventDefault();
        addTask(newTask);
        newTask = "";
    }

</script>

<form {onsubmit}>
    <label>Task <input name="newTask" bind:value={newTask}/>
    </label>
    <div class="button">

        <button>Add</button>
    </div>
</form> 
<style>
    .button {
        display: flex;
        justify-content: end;
    }
    button {
        padding: 1em 2em;
    }
</style>