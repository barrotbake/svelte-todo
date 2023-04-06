<script>
    import {getContext} from 'svelte';
    export let showForm = false;
    $: showFormTag = showForm ? "showForm" : "todoFormHide";
    let todoList = getContext('todoList');

    let getTask = () => {
        let task = {
            text: document.querySelector("input[name=text]").value,
            description: document.querySelector("input[name=description]").value,
            checked: false
        }
        return task;
    }

    let addTask = () => {
        let task = getTask();
        todoList.update(list => {
            list.push(task);
            return list;
        })
        showForm = false;
        document.querySelector("input[name=text]").value = "";
        document.querySelector("input[name=description]").value = "";
    }

    let cancelTask = () => {
        showForm = false;
        document.querySelector("input[name=text]").value = "";
        document.querySelector("input[name=description]").value = "";
    }
    
</script>

<div class={showFormTag}>
    <form>
        <input type="text" name="text" placeholder="Task text"/>
        <input type="text" name="description" placeholder="Task description"/>
    </form>
    <div class="buttonGroup">
        <button class="addTask" on:click={addTask}>Add Task</button>
        <button class="cancelTask" on:click={cancelTask}>Cancel</button>
    </div>
</div>

<style>
    /* Rounded input */
    input[type=text] {
        border: 2px solid #ccc;
        border-radius: 4px;
        font-size: 16px;
        background-color: white;
        padding: 12px 20px 12px 40px;
        -webkit-transition: width 0.4s ease-in-out;
        transition: width 0.4s ease-in-out;
    }

    form {
        display: flex;
        flex-direction: column;
    }
    .buttonGroup {
        display: flex;
        flex-direction: row;
        float: right;
    }
    .buttonGroup button {
        margin-left: 10px;
        border-radius: 10px;
        padding: 12px 20px 12px 20px;
    }
    .addTask {
        background-color: #4CAF50;
        color: white;
    }
    .cancelTask {
        background-color: #f44336;
        color: white;
    }
    .todoForm {
        display: flex;
        flex-direction: column;
        margin: 10px;
    }

    .todoFormHide {
        display: none;
    }
</style>