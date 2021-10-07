<template>
  <div class="text-center mb-4">
    <h4>Create a to-do list.</h4>
    <form @submit.prevent="addtask" class="my-4">
      <div class="form-group">
        <label>Enter Task:</label>
        <input
          type="text"
          name="name"
          id=""
          placeholder="Enter task"
          v-model="item.name"
        />
      </div>
      <input type="submit" class="bg-info" value="Submit" />
    </form>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data() {
    return {
      item: {
        name: '',
      },
    }
  },
  methods: {
    async addtask() {
      const item = { item: { name: this.item.name } }
      await axios.post('http://127.0.0.1:8000/api/item/store', item)
      this.item.name = ''
      await this.$router.push('/')
    },
  },
}
</script>
