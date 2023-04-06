<script>
    import Task from './Task.svelte'
    export let taskList;
</script>

<style>
    .taskList {
        display: flex;
        flex-direction: column;
    }
</style>

<div class="taskList">
    {#each taskList as task}
        {#if !task.checked}
            <Task bind:taskProps={task}/>
        {/if}
    {/each}
</div>