<template>
  <div class="w-1/2">
    <div v-if="this.allProjects.length > 0" class="flex gap-x-4 w-full">
      <div class="w-full mb-5">
        <img :src="selectedProject.image" alt="" />
      </div>

      <div class="w-full">
        <h3>{{ selectedProject.title }}</h3>
        <p>{{ selectedProject.description }}</p>
      </div>
    </div>

    <div v-else class="flex gap-x-4 w-full">
      <div class="w-full mb-5">
        <img
          src="https://i.pinimg.com/564x/9f/8f/4c/9f8f4c2165f1df967864ee3de4d3b6ea.jpg"
          alt=""
        />
      </div>

      <div class="w-full">
        <h3>No hay proyectos que mostrar</h3>
      </div>
    </div>

    <div class="grid grid-cols-4 gap-4">
      <div v-for="(project, i) in allProjects" :key="i">
        <img
          :src="project.image"
          alt=""
          @click="openImg(i)"
          class="h-[200px] object-cover w-full"
        />
        <button @click="deleteImg(i)" class="btn btn-primary">Borrar</button>
      </div>
    </div>
  </div>

  <button
    v-if="this.allProjects.length > 0"
    @click="deleteAll"
    class="btn btn-danger"
  >
    Borrar todos
  </button>
</template>

<script>
export default {
  name: "UserView",
  props: ["allProjects"],
  data() {
    return {
      isOpen: true,
      selectedProject: this.allProjects[0],
      proj: true,
    };
  },
  methods: {
    openImg(i) {
      this.selectedProject = this.allProjects[i];
    },
    deleteImg(i) {
      this.allProjects.splice(i, 1);
    },
    deleteAll() {
      this.allProjects.splice(0, this.allProjects.length);
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
  opacity: 0;
}
</style>
