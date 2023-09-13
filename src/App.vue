<template>
  <div class="flex flex-col items-center h-[100vh]">
    <div
      class="fixed flex justify-between items-center w-screen border-b-2 border-black pl-8"
    >
      <h1 class="font-bold text-2xl hidden sm:block">MY PORTFOLIO.vue</h1>
      <h1 class="font-bold text-xl leading-4 visible sm:hidden">
        MY PORT- <br />FOLIO
      </h1>
      <div class="flex justify-end">
        <button
          @click="isAdmin = true"
          class="font-bold, w-[75px] md:w-[150px] py-4"
          :class="{
            'bg-black': isAdmin,
            'text-zinc-50': isAdmin,
            'hover:bg-zinc-700': !isAdmin,
            'hover:text-zinc-50': !isAdmin,
          }"
        >
          Admin
        </button>
        <button
          @click="isAdmin = false"
          class="font-bold, w-[75px] md:w-[150px] py-4"
          :class="{
            'bg-black': !isAdmin,
            'text-zinc-50': !isAdmin,
            'hover:bg-zinc-700': isAdmin,
            'hover:text-zinc-50': isAdmin,
          }"
        >
          User
        </button>
      </div>
    </div>

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
          description: "A cat is mockin' you, and you're cryin'.",
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
html {
  background-color: rgb(250 250 250);
  font-family: "Syne";
}

h2,
h3 {
  background: url("../../src/wave.svg");
  background-repeat: repeat-x;
  background-size: 15px 10px;
  animation: move 25s linear infinite;
  -webkit-animation: move 25s linear infinite;
}

@keyframes move {
  from {
    background-position: 2px 19px;
  }
  to {
    background-position: 500px 19px;
  }
}
</style>
