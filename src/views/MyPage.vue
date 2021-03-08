<template>
  <div>
    <MyPageFace />
    <router-view />
  </div>
</template>

<script>
import MyPageFace from "../components/MyPageFace.vue"
export default {
  components: { MyPageFace },
}
</script>
