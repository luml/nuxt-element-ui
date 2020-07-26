<template>
  <div class="box">
    Hey there. I'm second.
    <div class="blcok">
      <span class="demonstration">Hot Summer</span>
      <el-image :src="src"></el-image>
    </div>
    <el-button @click="goBack">Go Back</el-button>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      src: "../../assets/hotsummer.JPG"
    };
  },

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