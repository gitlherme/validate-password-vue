<template>
  <PasswordValidate />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { PasswordValidate } from "@/components";

export default defineComponent({
  name: "App",
  components: {
    PasswordValidate,
  },
});
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@300;600;900&display=swap");

* {
  margin: 0;
  padding: 0;
}

#app {
  background-color: rgb(0, 7, 31);
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
