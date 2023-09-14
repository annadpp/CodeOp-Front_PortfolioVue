<template>
  <div class="w-full">
    <div
      v-if="this.allProjects.length > 0"
      class="fixed flex flex-col-reverse justify-between sm:flex-row w-full h-[50vh] sm:h-[43vh] mt-[14vh] sm:mt-[15vh] bg-zinc-50 z-50 gap-x-10 px-8 overflow-x-hidden"
    >
      <div class="w-full flex flex-col justify-between text-right mt-5">
        <div class="flex flex-col sm:justify-end sm:h-[12vh] h-[15vh]">
          <h3 class="font-bold mb-3 sm:mb-5 text-lg max-w-fit self-end">
            {{ selectedProject.title }}
          </h3>
          <p class="text-lg leading-4 sm:leading-7">
            {{ selectedProject.description }}
          </p>
        </div>
        <div class="flex gap-x-5 items-center h-[5vh]">
          <div
            v-if="this.allProjects.length > 4"
            @click="deleteAll"
            class="w-1/4 text-center mb-10"
          >
            <p class="bouncing text-sm">⬇ Scroll for more ⬇</p>
          </div>
          <button
            v-if="this.allProjects.length > 0"
            @click="deleteAll"
            class="w-full bg-black hover:bg-zinc-700 text-white mt-1 mb-[2vh] sm:mb-[5vh] py-2 sm:py-4"
          >
            Delete all projects
          </button>
        </div>
      </div>
      <div class="w-full mb-5">
        <img
          :src="selectedProject.image"
          class="h-[20vh] sm:h-[40vh] object-cover w-full"
        />
      </div>
    </div>

    <div
      v-else
      class="flex flex-col px-8 justify-between w-full mt-[15vh] h-[80vh]"
    >
      <div
        class="flex flex-col gap-x-5 justify-center lg:flex-row px-30 h-[70vh] self-center :w-[0vw]"
      >
        <div class="flex items-center justify-center">
          <img
            src="../sadcat.png"
            alt=""
            class="object-cover w-[70vw] sm:h-[70vw] md:max-w-[60vh] md:min-w-[55vh] md:max-h-[60vh] md:min-h-[50vh]"
          />
        </div>
        <div class="flex justify-center items-center w-full mt-8 lg:mt-0">
          <h3 class="font-bold text-center text-lg">No projects to show</h3>
        </div>
      </div>

      <div class="w-full">
        <p class="w-full sm:mt-10 border-t-2 border-black pt-4 text-center">
          © Anna de Pablo Puig
        </p>
      </div>
    </div>

    <div
      v-if="this.allProjects.length > 0"
      class="justify-end mt-[68vh] sm:mt-[59vh] z-0 pt-[4.5vh] sm:pt-[4.25vh] sm:mb-[5vh] h-[28vh] sm:h-[36vh] overflow-auto px-8 border-t-2 border-black"
    >
      <div class="grid grid-cols-4 gap-2 sm:gap-5">
        <div v-for="(project, i) in allProjects" :key="i">
          <img
            :src="project.image"
            alt=""
            @click="openImg(i)"
            class="h-[8vh] sm:h-[19vh] object-cover w-full cursor-pointer grayscale hover:grayscale-0"
          />
          <button
            @click="deleteImg(i)"
            class="bg-black text-white hover:bg-zinc-700 w-full py-1"
          >
            Delete
          </button>
        </div>
      </div>
      <div class="flex flex-col justify-end h-[10.5vh] sm:h-[9vh]">
        <p
          class="mt-[3.5vh] sm:mt-[5vh] border-t-2 border-black pt-4 text-center"
        >
          © Anna de Pablo Puig
        </p>
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
      this.selectedProject = this.allProjects[0];
    },
    deleteAll() {
      this.allProjects.splice(0, this.allProjects.length);
    },
  },
};
</script>

<style>
@keyframes bounce {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}

.bouncing {
  animation: bounce 1s infinite;
}
</style>
