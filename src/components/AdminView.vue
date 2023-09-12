<template>
  <h2 class="text-center font-semibold mb-5">ADD NEW PROJECT</h2>
  <div class="w-1/2">
    <!--Add form validation-->
    <form
      class="flex flex-col justify-center w-full"
      action=""
      :class="{ 'opacity-20': submitted }"
    >
      <div class="flex gap-x-5">
        <div class="flex flex-col w-full">
          Project Title <input v-model="title" class="border" />
        </div>
        <div class="flex flex-col w-full">
          Image URL <input v-model="image" class="border" />
        </div>
      </div>
      <div class="flex flex-col my-5">
        Project Description <input v-model="description" class="border" />
      </div>
      <button
        @click.prevent="handleSubmit"
        class="border w-20 self-center mb-3"
      >
        SUBMIT
      </button>
      <button @click.prevent="resetForm" class="border w-20 self-center mb-3">
        RESET
      </button>
    </form>

    <div
      v-if="submitted"
      class="absolute top-1/4 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-1/3 h-[150px] bg-blue-400 flex flex-col justify-center items-center"
    >
      <p>New project "{{ this.title }}" submitted!</p>
      <button @click.prevent="resetForm">Añadir más proyectos</button>
      <button @click="verProyectos">Ver mis proyectos</button>
    </div>
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
    };
  },
  methods: {
    handleSubmit() {
      this.$emit("createProject", {
        //queremos recoger info, pasarla al padre (App) y de allí a UserView (hermano)
        title: this.title,
        image: this.image,
        description: this.description,
      });
      this.submitted = true;
    },
    resetForm() {
      this.title = "";
      this.image = "";
      this.description = "";
      this.submitted = false;
    },
    verProyectos() {
      this.$emit("verProyectos", false); // Emit the custom event with the value false
    },
  },
};
</script>

<style></style>
