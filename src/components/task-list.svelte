<script lang="ts">
	import type { Tasks } from "../types/types";

    let { tasks } : {
        tasks: Tasks[]
    } = $props();

</script>

<section>
    <article>
        {#each tasks as task}
        <label class="task-item">
            <input type="checkbox">
                <span>{task.name}</span>
        </label>

        {/each}
    </article>
</section>

<style>
    section {
        min-height: 200px;
        display: flex;
        justify-content: center;
        align-items: flex-start;
        padding: 1rem;
        border-radius: 8px;
    }
    
    article {
        display: flex;
        flex-direction: column;
        gap: 0.75rem;
        width: 100%;
        max-width: 400px;
    }
    
    .task-item {
        display: flex;
        align-items: center;
        gap: 0.75rem;
        padding: 0.75rem 1rem;
        background: rgb(98, 128, 219);
        border-radius: 6px;
        box-shadow: 0 2px 4px rgba(217, 207, 207, 0.05);
        transition: all 0.2s ease;
    }
    
    .task-item:hover {
        background: #a79494;
        box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    }
    
    .task-item input[type="checkbox"] {
        width: 2em;
        height: 2em;
        accent-color: #4f46e5;
    }
    
    .task-item span {
        flex-grow: 1;
        font-size: 1rem;
        color: #272222;
        font-weight: 600;
        letter-spacing: 1px;
    }
</style>