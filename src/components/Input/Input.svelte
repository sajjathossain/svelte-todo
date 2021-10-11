<script>
  import { Todos } from '../../store'
  let task = ''

  const handleSubmit = (event) => {
    event.preventDefault()
    if (!task) {
      return
    }

    Todos.update((todos) => {
      return [
        ...todos,
        {
          id: todos.length,
          task,
          isCompleted: false,
        },
      ]
    })

    task = ''
  }
</script>

<style>
  .container {
    width: 80%;
    margin: 0 auto;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .input,
  .btn {
    padding: 10px;
    border: none;
    border-radius: 5px;
    font-size: 1.1rem;
  }

  .input {
    width: 80%;
    outline: none;
    margin-right: 10px;
  }

  .btn {
    width: 20%;
    background-color: lightseagreen;
    color: aliceblue;
    font-weight: 600;
  }

  .btn:hover {
    box-shadow: 0 2px 2px rgba(0, 0, 0, 0.2);
    cursor: pointer;
  }
</style>

<div class="container">
  <input
    type="text"
    placeholder="Enter your todo"
    bind:value={task}
    class="input" />
  <button class={`btn ${!task ? 'deactivated' : ''}`} on:click={handleSubmit}>
    Save
  </button>
</div>
