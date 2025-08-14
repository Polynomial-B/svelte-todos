<script lang="ts">
	import Form from "../components/form.svelte";
	import TaskList from "../components/task-list.svelte";
	import type { Task } from "../types/types";

    let tasks = $state<Task[]>([]);
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

    function removeTask(index: number) {
        tasks.splice(index, 1)
    }
</script>

<main>

<h1> Todo List</h1>
    <Form {addTask}/>
    <p>{totalCompleted} of {tasks.length} tasks completed</p>
    <TaskList {tasks} {toggleTask} {removeTask}/>
</main>

<style>
  h1 {
	text-align: center;
  }
</style>