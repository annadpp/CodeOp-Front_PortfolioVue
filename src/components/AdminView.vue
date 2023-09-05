<template>
  <div>
    Title
    <input v-model="title" class="border" />
    <button @click="handleSubmit" class="border">SUBMIT</button>
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
