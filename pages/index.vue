<template>
  <div class="container">
    <div>
      <logo />
      <h1 class="title">
        nuxt-ui-element
      </h1>
      <h2 class="subtitle">
        My prime Nuxt.js project
      </h2>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          class="button--green"
        >
          Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          class="button--grey"
          style="pointer-events: none"          
        >
          GitHub
        </a>
      </div>
      <div class="new-div">
        <el-button>This is a button supported by element-ui</el-button>
        <el-select v-model="value" name="source" placeholder="favorite fruit">
          <el-option
            v-for="item in options"
            :key="item.value"
            :label="item.label"
            :value="item.value">
          </el-option>
        </el-select>
      </div>
    </div>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'

//TODO: How to change element-ui theme
// import '../static/element-variables.scss'

export default {
  components: {
    Logo
  },
  data() {
    return {
      options: [{
        value: 'apple',
        label: '🍎'
      },{
        value: 'peach',
        label: '🍑'
      },{
        value: 'avocado',
        label: '🥑'
      }],
      value: ''
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

.new-div {
  margin-top: 1rem;
}
</style>
