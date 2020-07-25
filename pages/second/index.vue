<template>
  <div>
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