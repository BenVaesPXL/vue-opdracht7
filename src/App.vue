<template>
  <div class="w-25 m-auto">
    <div class="container-fluid my-3 border rounded py-3">
      <div class="row my-1">
        <div class="col">
          <h4>Nieuwe taak:</h4>
        </div>
      </div>
      <div class="row my-1">
        <div class="col">
          <input
            class="form-control"
            id="taak"
            v-model="newPrio"
            placeholder="Prioriteit"
            type="text"
          />
        </div>
      </div>
      <div class="row my-1">
        <div class="col">
          <input
            class="form-control"
            id="taak"
            v-model="newLabel"
            placeholder="Label"
            type="text"
          />
        </div>
      </div>
      <div class="row my-1">
        <div class="col">
          <textarea
            class="form-control"
            id="taak"
            v-model="newDescription"
            placeholder="Omschrijving"
            type="text"
          />
        </div>
      </div>
      <div class="row my-1">
        <div class="col d-flex justify-content-end">
          <button class="btn btn-primary" @click="addTask()">Toevoegen</button>
        </div>
      </div>
    </div>
    <div class="container-fluid" v-show="tasks.length > 0">
      <ul class="row list-unstyled">
        <li
          v-for="(task, index) in tasks"
          v-bind:key="task"
          @click="removeTask(index)"
          class="my-2 p-3 border rounded"
        >
          <TaskComponent :task="task" />
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
import TaskComponent from "./components/TaskComponent.vue";
export default {
  components: {
    TaskComponent,
  },
  data() {
    return {
      newPrio: "",
      newLabel: "",
      newDescription: "",
      tasks: [],
    };
  },
  methods: {
    addTask() {
      const newTask = {
        priority: this.newPrio,
        label: this.newLabel,
        description: this.newDescription,
      };
      this.tasks.push(newTask);

      this.newPrio = "";
      this.newLabel = "";
      this.newDescription = "";
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>
<style lang="scss"></style>
