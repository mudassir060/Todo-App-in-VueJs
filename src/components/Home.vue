<template>
  <div class="container">
    <h1><strong>My Vue Todo App</strong></h1>
    <br /><br />
    <div class="d-flex">
      <input
        type="text"
        name="Todo"
        v-model="task"
        class="form-control"
        placeholder="Enter Email"
        aria-label="Username"
        aria-describedby="basic-addon1"
      />
      <button class="btn btn-warning" type="button" @click="submintTask">
        SUBMIT
      </button>
    </div>
    <table class="table table-bordered mt-5">
      <thead>
        <tr>
          <th scope="col">Task</th>
          <th scope="col">Status</th>
          <th scope="col" class="text-center">Edit</th>
          <th scope="col" class="text-center">Delete</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <th><span :class="{'finished' : task.status === 'finished'}">{{ task.name }}</span></th>
          <td><span class="pointer" @click="changeStatuses(index)">
              {{ firstCharUpper(task.status) }}</span></td>
          <td>
            <div class="text-center" @click="editTask(index)">
              <span class="fa fa-pen"></span>
            </div>
          </td>
          <td>
            <div class="text-center" @click="deleteTask(index)">
              <span class="fa fa-trash"></span>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
    <font-awesome-icom icon="pen"></font-awesome-icom>
  </div>
</template>
<script>
export default {
  name: "Home-Page",
  data() {
    return {
      task: "",
      editedTask: null,
      availableStatuses:["to-do","in-progress", "finished"],
      tasks: [
      ],
    };
  },
  methods: {
    submintTask() {
      if (this.task.length === 0) return;
      if (this.editedTask === null) {
        this.tasks.push({
          name: this.task,
          status: "to-do",
        });
      } else {
        this.tasks[this.editedTask].name = this.task;
        this.editedTask = null;
      }
      this.task = "";
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
    editTask(index) {
      this.task = this.tasks[index].name;
      this.editedTask = index;
    },
    changeStatuses(index){
       let newIndex= this.availableStatuses.indexOf(this.tasks[index].status);
       if (++newIndex>2) newIndex = 0;
       this.tasks[index].status = this.availableStatuses[newIndex]
    },
    firstCharUpper(str){
        return str.charAt(0).toUpperCase() + str.slice(1);
    }
  },
};
</script>
<style>
.pointer{
    cursor: pointer;
}
.finished{
    text-decoration: line-through;
}
</style>