<template>
  <div class="container bg-light">
    <h4 class="m-auto">List of all task..</h4>
    <div class="row">
      <div class="col-2"></div>
      <div class="col-5 border">
        <ul>
          <li class="m-2 text-left" v-for="task in tasks" :key="task.id">
            {{ task.name }}
            <button class="btn btn-success btn-sm m-1" @click="editForm(task)">
              edit
            </button>
            <button
              class="btn btn-danger btn-sm m-1"
              @click="deleteTask(task.id)"
            >
              delete
            </button>
          </li>
        </ul>
      </div>
      <div class="col-3" v-if="edit">
        <Edit :id="task.id" :name="task.name" />
      </div>
    </div>
  </div>
</template>
<script>
import axios from 'axios'
import Edit from '../pages/edit.vue'
export default {
  components: {
    Edit,
  },
  data() {
    return {
      name: '',
      id: '',
      completed: '',
      completed_at: '',
      tasks: [],
      edit: false,
      task: {},
    }
  },
  async created() {
    const res = await axios.get('http://127.0.0.1:8000/api/items')
    const { data } = res
    this.tasks = data
  },
  methods: {
    async deleteTask(id) {
      await axios.delete(`http://127.0.0.1:8000/api/item/${id}`)
      alert('Successfully deleted')
      window.location = '/'
    },
    editForm(task) {
      this.edit = true
      this.task = task
    },
  },
}
</script>
