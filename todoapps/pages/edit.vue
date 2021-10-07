<template>
  <div>
    <form @submit.prevent="edittask(id)" class="my-4">
      <div class="form-group">
        <label>Edit Task:</label>
        <input
          type="text"
          name="name"
          id=""
          placeholder="Enter task"
          v-model="taskName"
        />
      </div>
      <input type="submit" class="bg-info" value="Submit" />
    </form>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  name: 'Edit',
  props: ['id', 'name'],
  data() {
    return {
      taskName: '',
    }
  },
  methods: {
    async edittask(id) {
      console.log(this.taskName)
      const item = { item: { name: this.name, completed: true } }
      await axios.put(`http://127.0.0.1:8000/api/item/${id}`, item)
      window.location = '/'
    },
  },

  mounted() {
    this.taskName = this.name
    console.log(this.taskName)
  },
}
</script>
