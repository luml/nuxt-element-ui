<template>
  <div class="box">
    Hey there. I'm second.
    <el-button @click="goBack">Go Back</el-button>
  </div>
</template>

<script lang="ts">
export default {
  methods: {
    goBack() {
      this.$router.go("-1");
    }
  }
};
</script>

<style scoped>
.box {
  margin: 2rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.12), 0 0 6px rgba(0, 0, 0, 0.04);
}
</style>