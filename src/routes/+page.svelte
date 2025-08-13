<script lang="ts">
	import Form from "../components/form.svelte";
	import TaskList from "../components/task-list.svelte";
	import type { Tasks } from "../types/types";

    let tasks = $state<Tasks[]>([]);

    function addTask(newTask : string) { 
        tasks.push({
            id: crypto.randomUUID(),
            name: newTask,
            completed: false
        });
    }
</script>

<main>

<h1> Todo List</h1>
    <Form {addTask}/>
    <TaskList {tasks}/>
</main>

<style>
  h1 {
	text-align: center;
  }
</style>