<template>
  <div class="container">
    <div>
      <!-- <logo /> -->
      <h1 class="title">
        nuxt-ui-element
      </h1>
      <h2 class="subtitle">
        My prime Nuxt.js project
        <el-popover
          placement="right-start"
          title="Dingding"
          width="200"
          trigger="hover"
          content="How do you feel when you see this is page not dope what's so ever"
        >
          <el-button slot="reference"><i class="el-icon-bell"></i></el-button>
        </el-popover>
      </h2>
      <div class="links">
        <a href="https://nuxtjs.org/" target="_blank" class="button--green">
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
        <el-button @click="open"
          >This is a button supported by element-ui</el-button
        >
        <el-select
          @change="showFruit"
          v-model="value1"
          name="source"
          placeholder="favorite fruit"
        >
          <el-option
            v-for="item in options"
            :key="item.value"
            :label="item.label"
            :value="item.value"
          >
          </el-option>
        </el-select>
        <el-input
          v-model="value2"
          placeholder="please give me some money"
          clearable
          @focus="showMeTheMoney($event)"
          ref="inputRef"
        ></el-input>
        <el-input-number
          v-model="value5"
          @change="handleChange"
          :min="1"
          :max="10"
          label="描述文字"
        ></el-input-number>
        <el-badge :value="100" class="item" type="primary"
          ><el-button @click="countComments(100)" size="small"
            >Comments</el-button
          ></el-badge
        >
        <el-rate
          v-model="value6"
          show-text
          :texts="moods"
          @change="fantastic"
        ></el-rate>
      </div>
      <div class="block">
        <el-slider
          v-model="value3"
          :marks="marks"
          :format-tooltip="formatTooltip"
          vertical
          height="100px"
        ></el-slider>
        <el-calendar
          class="calendar"
          v-model="value4"
          :range="['2020-06-22', '2020-06-28']"
        ></el-calendar>
        <div class="tip-tool">
          <el-tooltip
            class="item"
            effect="light"
            content="Let's ride this cute boat to his heart TODAY`"
            placement="left-end"
          >
            <el-button>🛶</el-button>
          </el-tooltip>
        </div>
        <el-breadcrumb separator-class="el-icon-arrow-right">
          <el-breadcrumb-item :to="{ path: '/' }">Maybe</el-breadcrumb-item>
          <el-breadcrumb-item><a href="/">Today</a></el-breadcrumb-item>
          <el-breadcrumb-item class="no">Not</el-breadcrumb-item>
          <el-breadcrumb-item><a href="/">The</a></el-breadcrumb-item>
          <el-breadcrumb-item class="day">Day</el-breadcrumb-item>
        </el-breadcrumb>
      </div>
    </div>
  </div>
</template>

<script>
import Logo from "~/components/Logo.vue";

export default {
  components: {
    Logo
  },
  data() {
    return {
      options: [
        {
          value: "apple",
          label: "🍎"
        },
        {
          value: "peach",
          label: "🍑"
        },
        {
          value: "avocado",
          label: "🥑"
        }
      ],
      value1: "",
      value2: "💴💴💴",
      value3: 48,
      value4: new Date(),
      marks: {
        0: "0%",
        100: {
          style: {
            color: "#1989FA"
          },
          label: this.$createElement("strong", "100%")
        }
      },
      value5: 1,
      value6: null,
      moods: ["lonely", "sad", "happy", "creative", "fantastic"]
    };
  },

  mounted() {
    this.$refs.inputRef.$el.children[0].focus();
  },
  methods: {
    showFruit(value) {
      this.$confirm(`Is this your favorite ` + value + "?", "Check", {
        distinguishCancelAndClose: true,
        confirmButtonText: "Yess",
        cancelButtonText: "Noo"
      })
        .then(() => {
          this.$message({
            type: "success",
            message: "Nice choice"
          });
        })
        .catch(action => {
          this.$message({
            type: "info",
            message: action === "cancel" ? "Not sure yet" : "Leave it there"
          });
        });
    },
    showMeTheMoney(e) {
      // @focus is a input events
      e.target.style.borderColor = "teal";
    },
    formatTooltip(val) {
      return val / 100;
    },
    open() {
      const h = this.$createElement;
      this.$notify({
        title: "Hey Guys",
        message: h(
          "i",
          { style: "color: teal" },
          "Button supported by element-ui, you should check it out"
        )
      });
    },
    handleChange(value) {
      console.log(value);
    },
    fantastic(text) {
      this.value2 = text + ` times more 💴`;
    },
    countComments(sum) {
      console.log("Give sum to slider");
      this.value3 = sum;
    }
  }
};
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
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
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
  display: flex;
  margin-top: 1rem;
}
.block {
  margin: 1rem 1rem 1rem 0;
  display: flex;
}
/* TODO el-calendar select doesn't work */
.calendar {
  width: 50%;
}
.tip-tool button {
  border-style: none;
  border-radius: 16px;
  font-size: 30px;
  padding: 1px;
}
.tip-tool button:hover {
  background: #fff;
}
.el-tooltip__popper.is-light {
  border: 1px teal solid;
}
.el-input-number input {
  width: 180px;
}
.el-breadcrumb {
  margin: 0.5rem 0 0 2em;
}
.no .el-breadcrumb__inner {
  color: red;
  font-weight: bolder;
}
/* TODO: why not work */
.day .el-breadcrumb__inner {
  color: teal;
  font-weight: bolder;
}
.el-button.el-button--default.el-popover__reference {
  padding: 0;
  border: none;
  font-size: 20px;
}
.el-icon-bell:hover {
  color: teal;
}
.el-input.el-input--suffix {
  width: 300px;
}
.el-rate {
  margin-left: 2rem;
}
.el-badge > button {
  height: 40px;
}
</style>
