<template>
  <div class="container">
    <div>
      <b-navbar type="light" variant="light">
        <nuxt-link class="navbar-brand" to="/">To-Do List</nuxt-link>
        <b-navbar-nav>
          <li class="nav-item">
            <nuxt-link class="nav-link" to="/addtask">Add Task</nuxt-link>
          </li>
        </b-navbar-nav>
      </b-navbar>
    </div>
  </div>
</template>
<script>
export default {}
</script>