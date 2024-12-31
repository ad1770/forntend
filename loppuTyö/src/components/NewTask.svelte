<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();
  let title = '';
  let description = '';
  let dueDate = '';
  let category = '';

  const categories = ['Work', 'Personal', 'Urgent', 'Category x', 'School'];

  const addTask = () => {
    if (title && dueDate) {
      dispatch('add', {
        title,
        description,
        dueDate,
        category,
        completed: false,
      });
      title = '';
      description = '';
      dueDate = '';
      category = '';
    } else {
      alert('Title and Due Date are required');
    }
  };
</script>

<div>
  <input bind:value={title} placeholder="Task Title" />
  <textarea bind:value={description} placeholder="Task Description"></textarea>
  <input type="date" bind:value={dueDate} />
  <select bind:value={category}>
    <option disabled selected value="">Select Category</option>
    {#each categories as cat}
      <option>{cat}</option>
    {/each}
  </select>
  <button on:click={addTask}>Add Task</button>
</div>
