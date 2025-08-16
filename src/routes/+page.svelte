<script lang="ts">
	import Form from "../components/form.svelte";
	import TaskList from "../components/task-list.svelte";
	import { type Filter, type Task } from "../types/types";

    let tasks = $state<Task[]>([]);
    let currentFilter = $state<Filter>("all");
    let totalCompleted = $derived(tasks.reduce(
        (total, task)=> total + Number(task.completed), 0
    ))

    function addTask(newTask : string) { 
        tasks.push({
            id: crypto.randomUUID(),
            name: newTask,
            completed: false
        });
    }

    function toggleTask(task: Task) {
        task.completed = !task.completed
    }

    function removeTask(id: string) {
        const index = tasks.findIndex((task)=> task.id === id);
        tasks.splice(index, 1);
    }

    let filteredTasks = $derived.by(()=>{
        switch(currentFilter) {
            case "all": {
                return tasks;
            }
            case "todo": {
                return tasks.filter((task) => !task.completed);
            }
            case "done": {
                return tasks.filter((task) => task.completed);
            }
        }
        return tasks;
    })

</script>

{#snippet filterButton(filter: Filter)}
    <button onclick={()=> currentFilter = filter} class:contrast={currentFilter === filter} class="capitalised">{filter}</button>
{/snippet}


<main>
<h1> Todo List</h1>
    <Form {addTask}/>
    {#if tasks.length > 0}
    <div class="button-container">
        <span>Filter</span>
        {@render filterButton("all")}
        {@render filterButton("todo")}
        {@render filterButton("done")}
    </div>
    <p>{totalCompleted} of {tasks.length} tasks completed</p>
    {:else}
    <p>Add a task</p>
    {/if}
    <TaskList tasks={filteredTasks} {toggleTask} {removeTask}/>
</main>

<style>
  h1 {
	text-align: center;
  }

  .button-container {
    display: flex;
    justify-content: end;
    margin-top: 2em;
    gap: 10px;
  }

  button {
    min-width: 4rem;
  }

  .contrast {
    background-color: rgb(94, 117, 218);
    border-radius: 5px;
    border: 1px solid grey;
  }

  .capitalised {
    text-transform: capitalize;
  }
</style>