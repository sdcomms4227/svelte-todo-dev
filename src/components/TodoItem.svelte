<script>
  export let todo;
  export let deleteTodo;
  export let handleComplete;
</script>

<li class="list-group-item d-flex d-flex justify-content-between align-items-center border-start-0 border-top-0 border-end-0 border-bottom rounded-0 mb-2">
  <div class="d-flex align-items-center">
    <input id="input{todo.id}" class="form-check-input me-2" type="checkbox" checked={todo.completed} on:change={() => handleComplete(todo.id)} />
    <label for="input{todo.id}">
      {todo.id}
      {todo.text}
    </label>
  </div>
  <a href="#!" on:click={() => deleteTodo(todo.id)} data-mdb-toggle="tooltip" title="Remove item">
    <i class="fas fa-times text-primary" />
  </a>
</li>

<style>
  input[type="checkbox"]:checked + label {
    text-decoration: line-through;
  }
  label {
    cursor: pointer;
  }
</style>
