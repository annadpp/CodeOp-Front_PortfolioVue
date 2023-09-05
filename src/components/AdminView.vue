<template>
  <div>
    <h2 class="text-center font-semibold mb-5">ADD NEW PROJECT</h2>
    <form class="flex flex-col justify-center" action="">
      <div class="flex gap-x-5">
        <div class="flex flex-col">
          Project Title <input v-model="title" class="border" />
        </div>
        <div class="flex flex-col">
          Image URL <input v-model="image" class="border" />
        </div>
      </div>
      <div class="flex flex-col my-5">
        Project Description <input v-model="description" class="border" />
      </div>
      <button @click="handleSubmit" class="border w-20 self-center">
        SUBMIT
      </button>
    </form>
  </div>
</template>

<script>
export default {
  name: "AdminView",
  data() {
    return {
      title: "",
      image: "",
      description: "",
    };
  },
  methods: {
    handleSubmit() {
      this.$emit("createProject", {
        title: this.title,
        image: this.image,
        description: this.description,
      });
    },
  },
};
</script>

<style></style>
