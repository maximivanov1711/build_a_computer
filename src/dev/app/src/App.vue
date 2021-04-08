<template>
  <div class="header">
    <img class="header__logo" src="./assets/images/logo.png" alt="logo" />
    <span class="header__text">Build a computer - Собери компьютер</span>
  </div>
  <Timeline
    :activeStage="activeStage"
    :currentStage="currentStage"
    @changeCurrentStage="changeCurrentStage"
    @restart="restart"
  />
  <MainPanel
    ref="mainPanel"
    :activeStage="activeStage"
    :currentStage="currentStage"
    @nextStage="nextStage"
    @complete="restart"
  />
</template>

<script>
import Timeline from "./components/Timeline.vue";
import MainPanel from "./components/MainPanel.vue";

export default {
  name: "App",
  components: {
    Timeline,
    MainPanel,
  },
  data() {
    return {
      activeStage: 0,
      currentStage: 0,
    };
  },
  methods: {
    restart() {
      this.activeStage = 0;
      this.currentStage = 0;

      this.$refs.mainPanel.reset();
    },
    nextStage() {
      this.activeStage += 1;
      // ? this.currentStage += 1;
      this.currentStage = this.activeStage;
    },
    changeCurrentStage(stageId) {
      this.currentStage = stageId;

      if (this.currentStage !== this.activeStage) {
        this.$refs.mainPanel.currentStep = 0;
        return;
      }

      this.$refs.mainPanel.currentStep = this.$refs.mainPanel.activeStep;
    },
  },
};
</script>

<style>
:root {
  --pale-light-green: #e8f7d2;
  --light-green: #a9f340;
  --main-green: #94d637;
  --dark-green: #85bf34;

  --pale-red: #fee3e3;
  --red: #ec2525;

  --pale-light-yellow: #f7f4d2;
  --light-yellow: #f5eb52;
  --yellow: #efe543;

  --light-gray: #f7f7f7;
  --gray: #ededed;
  --dark-gray: #e9e9e9;
  --very-dark-gray: #333333;
}

* {
  box-sizing: border-box;
}

html,
body,
#app {
  margin: 0;
  padding: 0;
  min-width: 1200px;
  height: 100vh;
  font-family: Rubik;
}

#app {
  display: flex;
  flex-direction: column;
}

.header {
  height: 90px;
  display: flex;
  align-items: stretch;
  color: white;
  background: var(--main-green);
}
.header__logo {
  margin: 6px;
}
.header__text {
  margin-top: auto;
  font-size: 35px;
  font-family: "Roboto mono";
}

.main-panel {
  margin: 30px;
  margin-top: 0;
  flex: 1;
}
</style>
