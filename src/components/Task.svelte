<script>
    export let taskProps = {
        text: "",
        description: "",
        checked: false
    }
    
    let handleCheckTask = () => {
        taskProps.checked = !taskProps.checked
        taskProps = {...taskProps}
    } 
</script>

<style>
    .checkButton {
        width: 20px;
        height: 20px;
        border-radius: 50%;
        border: 1px solid black;
        background-color: white;
    }

    .checkButton:checked {
        background-color: black;
    }

    .textContainer {
        display: flex;
        flex-direction: column;
        margin-left: 10px;
    }

    .taskText {
        font-size: 20px;
    }

    .taskDescription {
        font-size: 15px;
    }

    .taskBox {
        display: flex;
        flex-direction: row;
        margin: 10px;
    }
</style>

<div class="taskBox">
    <button class="checkButton" on:click={handleCheckTask}></button>
    <div class="textContainer">
        <div class="taskText">{taskProps.text}</div>
        <div class="taskDescription">{taskProps.description}</div>
    </div>
</div>