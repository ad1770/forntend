<script>
  export let task;
  export let onComplete;
  export let onDelete;

  const handleDelete = () => {
    onDelete(task);
  };
</script>

<div class="task-item">
  <input
    type="checkbox"
    checked={task.completed}
    on:change={() => onComplete(task)}
  />

  <div class="task-details">
    <span class="task-title">{task.title}</span>
    <span class="task-description">{task.description}</span>
    <span class="task-due-date">Due date: {task.dueDate}</span>
    <span class="task-description">{task.category}</span>
  </div>
  <button on:click={handleDelete}>Delete</button>
</div>

<style>
  .task-item {
    padding: 15px;
    border: 2px solid #ccc;
    border-radius: 8px;
    background-color: #f9f9f9;
    display: flex;
    justify-content: space-between;
    align-items: center;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    margin-bottom: 10px;
    max-width: 600px;
    width: 100%;
    overflow: hidden;
  }

  .task-item button {
    padding: 5px 10px;
    border: none;
    background-color: #ff4d4d;
    color: white;
    border-radius: 5px;
    cursor: pointer;
  }

  .task-item button:hover {
    background-color: #ff1a1a;
  }

  .task-details {
    display: flex;
    flex-direction: column;
    gap: 5px;
    margin-left: 10px;
    flex-grow: 1;
    max-width: 60%;
    align-items: center;
    justify-content: center;
  }

  .task-title {
    font-weight: bold;
    font-size: 18px;
    word-wrap: break-word;
    text-align: center;
  }

  .task-description {
    font-size: 14px;
    color: #666;
    white-space: normal;
    word-wrap: break-word;
    overflow-wrap: break-word;
    text-align: center;
    max-width: 100%;
  }

  .task-due-date {
    font-size: 12px;
    color: #999;
    text-align: center;
  }

  .task-item input[type='checkbox'] {
    margin-right: 10px;
  }
</style>
