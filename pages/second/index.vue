<template>
  <div class="box">
    <div class="blcok">
      <h3>Hey there. I'm a bird.</h3>
      <!-- <span class="demonstration"></span> -->
      <el-image style="width: 600px; height: 500px" :src="url"></el-image>
    </div>
    <el-form ref="form" :model="form" label-width="80px">
      <el-form-item label="name">
        <el-input v-model="form.name"></el-input>
      </el-form-item>
      <el-form-item label="region">
        <el-select v-model="form.region" placeholder="please pick up a region">
          <el-option label="Beijing" value="bj"></el-option>
          <el-option label="Shanghai" value="sh"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item label="delivery">
        <el-switch v-model="form.delivery"></el-switch>
      </el-form-item>
      <el-form-item label="type">
        <el-checkbox-group v-model="form.type">
          <el-checkbox label="food" name="type"></el-checkbox>
          <el-checkbox label="streetVendor" name="type"></el-checkbox>
          <el-checkbox label="offline" name="type"></el-checkbox>
          <el-checkbox label="branding" name="type"></el-checkbox>
        </el-checkbox-group>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit">Confirm</el-button>
        <el-button>Cancel</el-button>
      </el-form-item>
    </el-form>
    <el-button @click="goBack">⬅️</el-button>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      // src: "../../assets/hotsummer.JPG",
      // fit: "contain",
      url:
        "https://fuss10.elemecdn.com/e/5d/4a731a90594a4af544c0c25941171jpeg.jpeg",
      form: {
        name: "",
        region: "",
        delivery: false,
        type: ["food"]
      }
    };
  },

  methods: {
    goBack() {
      this.$router.go("-1");
    },

    onSubmit() {
      console.log("submit!");
    }
  }
};
</script>

<style scoped>
.box {
  display: flex;
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