<template>
  <div>{{ title }}</div>
  <div v-for="project in allProjects">
    <img :src="project.image" alt="" />
    <p>{{ project.title }}</p>
    <p>{{ project.description }}</p>
  </div>
</template>

<script>
export default {
  name: "UserView",
  props: ["allProjects"],
  data() {
    return {
      title: "User View component",
    };
  }, // añadir props [allprojects]
};
</script>

<style></style>
