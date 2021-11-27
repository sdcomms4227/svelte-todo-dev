<script>
  import TodoItem from "./TodoItem.svelte";
  export let todoList;
  export let deleteTodo;
  export let handleComplete;
</script>

<ul class="list-group mb-0">
  {#each todoList as todo}
    <TodoItem {todo} {deleteTodo} {handleComplete} />
  {/each}
</ul>
