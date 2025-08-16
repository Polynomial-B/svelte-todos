<script lang="ts">
	import type { Task } from "../types/types";
    let {task, removeTask} : {task: Task, removeTask: (id: string)=> void }= $props();

</script>

<button onclick={()=> removeTask(task.id)}>Remove</button>

<style>
    button {
        height: 30px;
        width: 5rem;
    }
    button:hover {
        background: rgb(142, 0, 0);
        border-radius: inherit;
    }
</style>