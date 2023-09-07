<template>
  <div class="w-1/2">
    <Transition>
      <div v-if="isOpen" class="flex gap-x-4 w-full">
        <div class="w-full mb-5">
          <img :src="selectedProject.image" alt="" />
        </div>

        <div class="w-full">
          <button @click="isOpen = false">Cerrar</button>
          <h3>{{ selectedProject.title }}</h3>
          <p>{{ selectedProject.description }}</p>
        </div>
      </div></Transition
    >
    <div class="grid grid-cols-4 gap-x-4">
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
</template>

<script>
export default {
  name: "UserView",
  props: ["allProjects"],
  data() {
    return {
      isOpen: false,
      selectedProject: null, // Guarda info de cada proyecto
    };
  },
  methods: {
    openImg(i) {
      this.isOpen = true;
      this.selectedProject = this.allProjects[i]; // Guarda info de cada proyecto
    },
    deleteImg(i) {
      this.allProjects.splice(i, 1);
      this.isOpen = false;
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
