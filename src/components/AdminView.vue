<template>
  <div
    class="flex items-start mt-[15vh] sm:mt-[18vh]"
    :class="{ 'opacity-10': submitted }"
  >
    <h2 class="text-center font-semibold text-lg">Add new project</h2>
  </div>
  <div class="mt-5 sm:mt-0 px-8 flex justify-center items-center w-full h-full">
    <!--Add form validation-->
    <form
      ref="myForm"
      class="flex flex-col justify-center w-full"
      action=""
      :class="{ 'opacity-10': submitted }"
    >
      <div class="flex flex-col sm:flex-row gap-x-10">
        <div class="flex flex-col w-full mb-4 sm:mb-0">
          <p class="text-lg">Project Title</p>
          <input
            v-model="title"
            class="border-2 rounded border-black sm:mt-5 p-1 sm:p-2 text-zinc-700"
            required
          />
          <div class="h-2">
            <p v-if="!this.title && submitFalse" class="text-red-500">
              Required for submission
            </p>
          </div>
        </div>
        <div class="flex flex-col w-full my-5 sm:my-0">
          <p class="text-lg">Image URL</p>
          <input
            v-model="image"
            class="border-2 rounded border-black sm:mt-5 p-1 sm:p-2 text-zinc-700"
            required
          />
          <div class="h-2">
            <p v-if="!this.image && submitFalse" class="text-red-500">
              Required for submission
            </p>
          </div>
        </div>
      </div>
      <div class="flex flex-col my-4 sm:my-14">
        <p class="text-lg">Project Description</p>
        <input
          v-model="description"
          class="border-2 rounded border-black h-16 sm:h-28 sm:mt-5 p-2 text-zinc-700"
        />
      </div>
      <div class="flex justify-center gap-x-4 sm:gap-x-10 mt-5 sm:mt-0">
        <button
          @click.prevent="resetForm"
          class="border w-1/4 self-center mb-3 h-14 bg-black text-white hover:bg-zinc-700"
        >
          Clear form
        </button>

        <button
          @click.prevent="handleSubmit"
          class="border w-3/4 self-center mb-3 h-14 bg-black text-zinc-50 hover:bg-zinc-700"
        >
          Submit
        </button>
      </div>
    </form>

    <div
      v-if="submitted"
      class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-[80vw] h-[50vh] 2xl:w-[65vw] bg-black text-white flex flex-col justify-around items-center"
    >
      <p class="text-2xl mt-10 sm:mt-6 mx-8 text-center">
        New project "<span class="font-bold inline-block">{{ this.title }}</span
        >" submitted!
      </p>

      <div
        class="flex flex-col justify-center sm:flex-row items-center gap-x-10 gap-y-5 w-full px-8 sm:mb-4"
      >
        <button
          @click.prevent="resetForm"
          class="w-4/5 sm:w-2/5 bg-zinc-700 hover:bg-zinc-50 hover:text-black text-zinc-50 py-4"
        >
          Add more projects
        </button>
        <button
          @click="verProyectos"
          class="w-4/5 sm:w-2/5 bg-zinc-700 hover:bg-zinc-50 hover:text-black text-zinc-50 py-4"
        >
          See my projects
        </button>
      </div>
    </div>
  </div>

  <div class="px-8 w-full">
    <p class="mb-[5vh] w-full mt-10 border-t-2 border-black pt-4 text-center">
      © Anna de Pablo Puig
    </p>
  </div>
</template>

<script>
export default {
  emits: ["createProject", "putapatata"],
  name: "AdminView",
  data() {
    return {
      title: "",
      image: "",
      description: "",
      submitted: false,
      info: true,
      submitFalse: false,
    };
  },
  methods: {
    handleSubmit() {
      if (!this.title || !this.image) {
        this.submitFalse = true;
      } else {
        this.$emit("createProject", {
          title: this.title,
          image: this.image,
          description: this.description,
        });
        this.submitted = true;
      }
    },
    resetForm() {
      this.title = "";
      this.image = "";
      this.description = "";
      this.submitted = false;
      this.submitFalse = false;
    },
    verProyectos() {
      this.$emit("verProyectos", false);
    },
  },
};
</script>

<style>
span {
  background: url("../../src/wave-white.svg");
  background-repeat: repeat-x;
  background-size: 20px 20px;
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
