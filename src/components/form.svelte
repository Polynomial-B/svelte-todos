<script lang="ts">
    let newTask = $state("")

    function onsubmit(e: SubmitEvent) {
        e.preventDefault();
        console.log(newTask);
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