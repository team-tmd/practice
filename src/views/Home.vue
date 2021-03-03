<template>
  <div>
    <SubmitForm />
    <router-view />
  </div>
</template>

<script>
import SubmitForm from "../components/SubmitForm.vue"
export default {
  components: { SubmitForm },
}
</script>

<style scoped>
.home__wrapper {
  margin: 0 auto;
  max-width: 600px;
  background-color: #ccc;
}
</style>
