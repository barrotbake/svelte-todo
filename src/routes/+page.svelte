<script>
    import TaskList from '../components/TaskList.svelte';
    import TaskForm from '../components/TaskForm.svelte';
    import { setContext } from 'svelte';
    import { writable } from 'svelte/store';

    const todoList = writable([
        {
            text: "Task 1",
            description: "This is a task description",
            checked: false
        },
        {
            text: "Task 2",
            description: "This is a task description",
            checked: false
        },
        {
            text: "Task 3",
            description: "This is a task description",
            checked: false
        },
    ])

    setContext('todoList', todoList);
    let showAddTask = false

    let handleAddTask = () => {
        showAddTask = !showAddTask
    }

    let dummy = {
        text: "Task 4",
        description: "This is a task description",
        checked: false
    }
</script>

<h1>Today</h1>
<hr>
<!-- Task List Component -->
<TaskList taskList={$todoList}/>
<div class="addGroup">
    <button on:click={handleAddTask}>+</button>
    <p>Add Task</p>
</div>
<!-- Add task Component -->
<TaskForm showForm={showAddTask}/>

<style>
    .addGroup {
        display: flex;
        flex-direction: row;
        margin: 10px;
    }

    button {
        font-size: 2em;
        margin-right: 10px;
    }


</style>

