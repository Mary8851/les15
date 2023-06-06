<template>
  <div class="task-item">
    <input type="checkbox" id="done" v-model="isCompleted" @change="onChange" />
    <div class="task-item-name" :class="{ completed: task.completed }">
      <h1>{{ task.title }}</h1>
      <p>{{ task.description }}</p>
    </div>
    <button @click="showModalWindow" class="more">Подробнее</button>
    <div @click="$emit('deleteEvent')" class="delete">&#10006;</div>
    <ModalWindow v-if="isModal" @closeWindow="closeWindow">{{
      task.description
    }}</ModalWindow>
  </div>
</template>

<script>
import ModalWindow from "./ModalWindow.vue";
export default {
  components: { ModalWindow },
  name: "TaskItem",
  data() {
    return {
      isCompleted: this.task.completed,
      isModal: false,
    };
  },
  props: {
    task: {
      type: Object,
    },
  },
  emits: ["deleteEvent", "updateCompleted"],
  methods: {
    onChange() {
      this.$emit("updateCompleted", this.task.id);
    },
    showModalWindow() {
      this.isModal = true;
    },
    closeWindow() {
      this.isModal = false;
    },
  },
};
</script>

<style lang="scss">
.task-item {
  width: 600px;
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  width: 100%;
  margin: 30px 0;
  box-shadow: 0px 5px 10px 0px rgba(42, 191, 193, 0.5);
  border-radius: 15px;
  background: white;
  padding: 15px;
  input {
    width: 20px;
    height: 20px;
  }
  &-name {
    width: 300px;
    border-radius: 5px;
    text-align: center;
    box-shadow: 0px 5px 10px 0px rgba(45, 139, 183, 0.5);
    h1 {
      margin-bottom: 5px;
    }
    p {
      font-style: italic;
    }
  }
}
.more {
  padding: 10px;
  border-radius: 10px;
  border: 1px solid rgb(123, 164, 198);
  padding: 10px;
  cursor: pointer;
}
.delete {
  color: rgb(35, 163, 189);
  font-size: 30px;
  cursor: pointer;
}
.completed {
  background: rgb(117, 198, 176);
}
</style>
