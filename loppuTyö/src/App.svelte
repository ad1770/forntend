<script>
  import TaskForm from './components/NewTask.svelte';
  import TaskList from './components/TaskList.svelte';
  import CategoryFilter from './components/TaskFilter.svelte';

  let tasks = [];
  let filteredCategory = '';

  const addTask = (event) => {
    tasks = [...tasks, event.detail];
  };

  const completeTask = (task) => {
    task.completed = !task.completed;
  };

  const deleteTask = (taskToDelete) => {
    tasks = tasks.filter((task) => task !== taskToDelete);
  };

  const filterTasks = (category) => {
    filteredCategory = category;
  };

  $: filteredTasks = filteredCategory
    ? tasks.filter((task) => task.category === filteredCategory)
    : tasks;
</script>

<main>
  <h1>Task Manager</h1>
  <TaskForm on:add={addTask} />
  <CategoryFilter
    categories={['Work', 'Personal', 'Urgent', 'Category x', 'School']}
    onFilter={filterTasks}
  />
  <TaskList
    tasks={filteredTasks}
    onComplete={completeTask}
    onDelete={deleteTask}
  />
</main>

<style>
  h1 {
    color: orange;
  }
  :global(body) {
    background-color: lightgrey;
    color: black;
  }
</style>
