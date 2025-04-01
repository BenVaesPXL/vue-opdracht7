<template>
  <div>
    <div class="row">
      <h5 v-if="isRead" @click="onPriorityClicked()" class="col-8">
        Prioriteit: {{ task.priority }}
      </h5>
      <input
        v-else
        type="text"
        v-model="newPriority"
        @keydown.enter="onEnterPressed()"
      />
      <p class="col-4 badge rounded-pill text-bg-info">
        {{ task.label }}
      </p>
    </div>
    <p>{{ task.description }}</p>
  </div>
</template>
<script>
export default {
  data() {
    return {
      isRead: true,
      newPriority: 0,
    };
  },
  emits: ["priorityChanged"],
  props: ["task"],
  methods: {
    onEnterPressed() {
      this.$emit("priorityChanged", this.task, this.newPriority);
      this.isRead = false;
    },
    onPriorityClicked() {
      this.isRead = true;
    },
  },
};
</script>
<style scoped></style>
