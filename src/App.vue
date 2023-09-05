<template>
  <div class="flex flex-col items-center mt-5">
    <div class="flex justify-end w-1/2 gap-x-4 mb-5">
      <button
        @click="isAdmin = true"
        class="font-bold"
        :class="{ 'text-red-500': isAdmin == true }"
      >
        ADMIN
      </button>
      <button
        @click="isAdmin = false"
        class="font-bold"
        :class="{ 'text-red-500': isAdmin != true }"
      >
        USER
      </button>
    </div>

    <h1 class="font-bold mb-5 text-2xl">MY PORTFOLIO</h1>
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
