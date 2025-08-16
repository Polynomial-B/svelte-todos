<script lang="ts">
	import type { Task } from "../types/types";
	import RemoveButton from "./remove-button.svelte";

    let { tasks, toggleTask, removeTask } : {
        tasks: Task[],
        toggleTask: (task: Task) => void;
        removeTask: (id: string) => void;
    } = $props();


</script>

<section>
    <article>
        {#each tasks as task}
        <label class="task-item">
            <input 
            checked={task.completed}
            onchange={()=> toggleTask(task)}
            type="checkbox">
                <span class:completed={task.completed}>{task.name}</span>
                <RemoveButton {removeTask} {task} />
        </label>

        {/each}
    </article>
</section>

<style>
    section {
        min-height: 200px;
        display: flex;
        align-items: flex-start;
        border-radius: 8px;
    }
    
    article {
        display: flex;
        flex-direction: column;
        gap: 0.75rem;
        width: 100%;
    }
    
    .task-item {
        display: flex;
        align-items: center;
        gap: 0.75rem;
        padding: 0.75rem 1rem;
        background: rgb(98, 128, 219);
        border-radius: 6px;
        box-shadow: 0 2px 4px rgba(217, 207, 207, 0.05);
    }
    
    .task-item:hover {
        background: #a79494;
        box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    }
    
    .task-item input[type="checkbox"] {
        width: 2em;
        height: 2em;
        accent-color: #4663e5;
    }

    .task-item input[type="checkbox"]:hover {
        accent-color: #813515;
    }
    .task-item span {
        flex-grow: 1;
        font-size: 1rem;
        color: #272222;
        font-weight: 600;
        letter-spacing: 1px;
    }

    .completed {
        text-decoration:line-through;
    }
</style>