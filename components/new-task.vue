<template>
  <div>
      <input name="task" id="task" v-model="task" class="input" type="text" placeholder="New Task">
      <button @click="submit" class="button is-primary">Add</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      task: ''
    }
  },
  methods: {
    submit() {
      this.$store.commit('notification/clear')
      if (!this.task) {
        this.$store.commit('notification/show', {
          text: 'Task is required.',
          style: 'is-danger'
        })
      } else {
        this.$emit('submitted', this.task)
      }
    }
  }
}
</script>






