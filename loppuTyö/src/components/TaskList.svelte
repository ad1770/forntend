<script>
  import TaskItem from './TaskItem.svelte';

  export let tasks = [];
  export let onComplete;
  export let onDelete;
</script>

<div>
  {#if tasks.length === 0}
    <p>No tasks available</p>
  {:else}
    {#each tasks as task (task.title)}
      <TaskItem {task} {onComplete} {onDelete} />
    {/each}
  {/if}
</div>

<style>
</style>
