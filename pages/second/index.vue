<template>
  <div class="box">
    <h3>Hey there. I'm a bird.</h3>
    <div class="blcok">
      <!-- <span class="demonstration"></span> -->
      <el-image style="width: 600px; height: 500px" :src="url"></el-image>
    </div>
    <el-button @click="goBack">Go Back</el-button>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      // src: "../../assets/hotsummer.JPG",
      // fit: "contain",
      url:
        "https://fuss10.elemecdn.com/e/5d/4a731a90594a4af544c0c25941171jpeg.jpeg"
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

h3 {
  padding: 2em 0;
}

.block {
  margin-left: -1em;
}
</style>