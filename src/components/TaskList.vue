<template>
  <div class="task-list-title">
    <h1>Список задач</h1>
  </div>
  <div class="task-list">
    <TaskForm @add-item="addItem" />
    <div>
      <TaskItem
        v-for="task in tasks"
        :key="task.id"
        :task="task"
        @delete-event="deleteTodo(task.id)"
        @update-completed="updateCompleted"
      />
    </div>
  </div>
  <div class="total">
    <p>Количество задач: {{ totalTask }}</p>
    <p>Количество выполненных задач: {{ totalCompletedTask }}</p>
  </div>
</template>

<script>
import TaskItem from "@/components/TaskItem.vue";
import TaskForm from "@/components/TaskForm.vue";
export default {
  components: { TaskItem, TaskForm },
  name: "TaskList",
  data() {
    return {
      tasks: [
        {
          id: "1",
          title: "Домашнее задание",
          description: "Сделать домашнее заданее по Frontend",
          completed: false,
        },
        {
          id: "2",
          title: "Планшет",
          description: "Купить в магазине планшет",
          completed: false,
        },
      ],
    };
  },
  methods: {
    addItem(task) {
      this.tasks.push(task);
    },
    deleteTodo(id) {
      this.tasks = this.tasks.filter((task) => {
        return task.id !== id;
      });
    },
    updateCompleted(itemId) {
      this.tasks = this.tasks.map((task) => {
        if (task.id === itemId) {
          task.completed = !task.completed;
        }
        return task;
      });
    },
  },
  computed: {
    totalTask() {
      return this.tasks.length;
    },
    totalCompletedTask() {
      return this.tasks.filter((task) => task.completed).length;
    },
  },
};
</script>

<style lang="scss">
body {
  background: rgb(248, 247, 245);
  padding: 20px;
}
.task-list-title {
  margin-bottom: 30px;
  h1 {
    font-size: 40px;
    text-align: center;
  }
}
.task-list {
  width: 600px;
  margin: 0 auto;
}
.total {
  width: 300px;
  box-shadow: 0px 5px 10px 0px rgba(45, 139, 183, 0.5);
  padding: 15px;
  border: 1px solid rgb(83, 176, 176);
  border-radius: 15px;
  margin: 0 auto;
  p {
    font-size: 16px;
    font-weight: 700;
  }
}
</style>
