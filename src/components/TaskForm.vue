<template>
  <div class="task-form">
    <input type="text" v-model="title" />
    <textarea
      name="description"
      id="description"
      cols="30"
      rows="10"
      v-model="description"
      placeholder="Описание задачи"
    ></textarea>
    <button @click="addItem">Добавить задачу</button>
  </div>
</template>

<script>
export default {
  name: "TaskForm",
  data() {
    return {
      title: "",
      description: "",
    };
  },
  methods: {
    addItem() {
      const task = {
        id: Math.floor(Math.random() * 100) + 1,
        title: this.title,
        description: this.description,
        completed: false,
      };
      this.$emit("addItem", task);
      this.title = "";
      this.description = "";
    },
  },
};
</script>

<style lang="scss">
.task-form {
  width: 300px;
  box-shadow: 0px 5px 10px 0px rgba(45, 139, 183, 0.5);
  padding: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  border-radius: 10px;
  margin: auto;
  background: linear-gradient(
    90deg,
    rgb(164, 197, 177) 30%,
    rgb(66, 122, 122) 100%
  );
  input {
    width: 100%;
    padding: 10px;
    border-radius: 5px;
    border: none;
    outline: none;
  }
  textarea {
    width: 100%;
    margin: 20px;
    border-radius: 10px;
    outline: none;
    padding: 10px;
    border: none;
  }
  button {
    width: 150px;
    padding: 10px;
    border-radius: 25px;
    border: none;
    font-weight: 700;
    cursor: pointer;
  }
  button:hover {
    background: radial-gradient(
      circle,
      rgba(204, 244, 238, 1) 30%,
      rgba(149, 215, 217, 1) 100%
    );
  }
}
</style>
