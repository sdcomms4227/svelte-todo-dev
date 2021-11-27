<script>
  export let todo;
  export let addTodo;
  export let handleKeyUp;
</script>

<div class="d-flex justify-content-center align-items-center mb-4">
  <div class="form-outline flex-fill">
    <input type="text" class="form-control" placeholder="할일을 입력하쇼" bind:value={todo} on:keyup={(e) => handleKeyUp(e)} />
  </div>
  <button type="submit" class="btn btn-primary ms-2" on:click={addTodo}>Add</button>
</div>
