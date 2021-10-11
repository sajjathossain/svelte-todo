<script>
  import { Todos } from '../../store.js'

  const deleteTodo = (event) => {
    Todos.update((todos) => {
      return todos.filter((todo) => todo.id !== parseInt(event.target.id))
    })
  }

  const handleTaskComplition = (passedTodo) => {
    // Todos.update((todos) => {
    //   return todos.forEach((todo) =>
    //     todo.id === taskId ? (todo.isCompleted = true) : todo.isCompleted,
    //   )
    // })
    Todos.update((todos) =>
      todos.filter((todo) =>
        todo.id === passedTodo.id
          ? (todo.isCompleted = true)
          : todo.isCompleted,
      ),
    )
  }
</script>

<style>
  .container {
    width: 100%;
    margin: 0 auto;
  }
  .warning {
    font-size: 1.2rem;
    font-weight: 500;
    color: lightcoral;
  }

  .list {
    width: 100%;
  }

  .item {
    width: 95%;
    height: auto;
    font-size: 1.1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border: 1px solid;
    border-radius: 5px;
    padding: 0.5rem;
    background-color: #fff;
    margin: 10px 0;
  }

  .deleteBtn {
    height: 100%;
    background-color: lightcoral;
    border: none;
    border-radius: 5px;
    padding: 0.5rem;
    color: #fff;
  }

  .deleteBtn:hover {
    box-shadow: 0 2px 2px rgba(0, 0, 0, 0.2);
    cursor: pointer;
  }
</style>

<div class="container">
  {#if $Todos.length > 0}
    <ul class="list">
      {#each $Todos as todo}
        <li class="item" on:dblclick={() => handleTaskComplition(todo)}>
          <div class={`${todo.isCompleted ? 'completed' : ''}`}>
            {todo.id + 1}: {todo.task}
          </div>
          <div
            class={`deleteBtn ${!todo.isCompleted ? 'deactivated' : ''}`}
            id={todo.id}
            on:click={deleteTodo}>
            Delete
          </div>
        </li>
      {/each}
    </ul>
  {:else}
    <div class="warning">No Todo found</div>
  {/if}
</div>
