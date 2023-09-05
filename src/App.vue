<template>
  <div>
    <h1>Hello World</h1>
    <button @click="isAdmin = true" class="border">ADMIN</button>
    <button @click="isAdmin = false" class="border">USER</button>
    <admin-view v-if="isAdmin" @createProject="addProject" />
    <user-view v-else @createProject="addProject" />
  </div>
</template>

<script>
import AdminView from "./components/AdminView.vue";
import UserView from "./components/UserView.vue";

export default {
  name: "App",
  components: {
    userView: UserView,
    adminView: AdminView,
  },
  data() {
    return {
      isAdmin: true,
      allProjects: [],
    };
  },
  methods: {
    addProject(project) {
      this.allProjects.push(project);
    },
  },
};
</script>

<style></style>
