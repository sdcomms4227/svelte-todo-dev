<script>
  import Input from "./components/Input.svelte";
  import Todos from "./components/Todos.svelte";

  let todo = ""; // input에 입력될 값!
  let todoList = [
    {
      id: 1,
      text: "할일이 산더미다",
      completed: false,
    },
    {
      id: 2,
      text: "할일이 없나",
      completed: false,
    },
    {
      id: 3,
      text: "할일을 미루고싶다",
      completed: true,
    },
  ];

  let lastId = todoList[todoList.length - 1]["id"];

  // 할일을 추가하는 함수
  let addTodo = () => {
    if (todo) {
      let newTodo = {
        id: ++lastId,
        text: todo,
        completed: false,
      };

      todoList[todoList.length] = newTodo;
      todo = "";
    }
  };

  // todo값을 업데이트 하면서, 엔터키를 누르면 할일이 추가되도록 하는 함수
  let handleKeyUp = (e) => {
    todo = e.target.value;
    if (e.keyCode === 13) {
      addTodo();
    }
  };

  let deleteTodo = (id) => {
    todoList = todoList.filter((todo) => todo.id !== id);
  };

  let handleComplete = (id) => {
    const index = todoList.findIndex((todo) => todo.id === id);
    todoList[index]["completed"] = !todoList[index]["completed"];
  };
</script>

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css" />
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" />

<section class="min-vh-100">
  <div class="container py-5 h-100">
    <div class="row d-flex justify-content-center align-items-center h-100">
      <div class="col col-xl-10">
        <div class="card">
          <div class="card-body p-5">
            <h6 class="mb-3">Todo List</h6>
            <Input {todo} {addTodo} {handleKeyUp} />
            <Todos {todoList} {deleteTodo} {handleComplete} />
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<style>
  :global(body) {
    padding: 0;
  }
  section {
    background-color: skyblue;
  }
</style>
