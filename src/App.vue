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

    <user-view
      v-if="!isAdmin"
      @createProject="addProject"
      :allProjects="allProjects"
    />
    <admin-view
      v-else
      @createProject="addProject"
      @verProyectos="verProyectos"
    />

    <div>
      <div id="objeto" @mostrar-objeto="mostrarObjeto" v-if="mostrarDiv">
        Hola
      </div>
    </div>
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
      allProjects: [
        {
          title: "Showerin'",
          image:
            "https://plus.unsplash.com/premium_photo-1661888521670-7dc228bcd78b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MXx8ZnVubnklMjBjYXR8ZW58MHx8MHx8fDA%3D&auto=format&fit=crop&w=1400&q=60",
          description: "A cat is showerin', and they're not likin'.",
        },
        {
          title: "Sleepin'",
          image:
            "https://images.unsplash.com/photo-1597237154674-1a0d2274cef4?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8OHx8ZnVubnklMjBjYXR8ZW58MHx8MHx8fDA%3D&auto=format&fit=crop&w=1400&q=60",
          description: "A cat is sleepin', and they're enjoyin'.",
        },
        {
          title: "Mockin'",
          image:
            "https://images.unsplash.com/photo-1641378588520-f30c0c36ef84?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8OXx8ZnVubnklMjBjYXR8ZW58MHx8MHx8fDA%3D&auto=format&fit=crop&w=1400&q=60",
          description: "A cat is mockin' tiy, and you're cryin'.",
        },
      ],
    };
  },
  methods: {
    addProject(project) {
      //project es el objeto que viene del emit createProject (AdminVue)
      this.allProjects.unshift(project); //unshift para que el último aparezca el primero
      //console.log(this.allProjects); se está enviando vía emit
    },
    verProyectos() {
      this.isAdmin = false; // Update the isAdmin data with the value emitted from AdminView
    },
  },
};
</script>

<style>
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0.5;
}
</style>
