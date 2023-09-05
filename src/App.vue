<template>
  <div class="flex flex-col items-center mt-5">
    <div class="flex justify-end w-1/2 gap-x-4 mb-5">
      <button
        @click="isAdmin = true"
        class="font-bold"
        :class="{ 'text-red-500': isAdmin, 'hover:text-red-200': !isAdmin }"
      >
        ADMIN
      </button>
      <button
        @click="isAdmin = false"
        class="font-bold"
        :class="{ 'text-red-500': !isAdmin, 'hover:text-red-200': isAdmin }"
      >
        USER
      </button>
    </div>

    <h1 class="font-bold mb-5 text-2xl">MY PORTFOLIO</h1>
    <admin-view v-if="isAdmin" @createProject="addProject" />
    <user-view v-else @createProject="addProject" :allProjects="allProjects" />
    <!--enviar props allprojects-->
  </div>
</template>

<script>
import AdminView from "./components/AdminView.vue";
import UserView from "./components/UserView.vue";

export default {
  name: "App",
  components: {
    UserView,
    AdminView,
  },
  data() {
    return {
      isAdmin: true,
      allProjects: [],
    };
  },
  methods: {
    addProject(project) {
      //project es el objeto que viene del emit createProject (AdminVue)
      this.allProjects.push(project);
      //console.log(this.allProjects); se está enviando vía emit
    },
  },
};
</script>

<style></style>
