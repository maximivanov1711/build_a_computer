<template>
  <div class="top-panel">
    <div class="top-panel__restart-button" @click="restart">
      <img
        class="restart-button__icon"
        src="../assets/icons/restart.png"
        alt="restart icon"
      />
    </div>
    <TimeLine
      :activeStage="activeStage"
      :currentStage="currentStage"
      @changeCurrentStage="changeCurrentStage"
    />
  </div>
</template>

<script>
import TimeLine from "./top_panel/Timeline.vue";

export default {
  name: "Timeline",
  components: {
    TimeLine,
  },
  props: ["activeStage", "currentStage"],
  methods: {
    changeCurrentStage(stageId) {
      this.$emit("changeCurrentStage", stageId);
    },
    restart() {
      this.$emit("restart");
    },
  },
};
</script>

<style scoped>
.top-panel {
  margin: 30px;
  display: flex;
  align-items: center;
}

.top-panel__restart-button {
  margin-right: 25px;
  padding: 8px;
  border: 4px solid var(--red);
  border-radius: 1000px;
  background: #fee3e3;
}
.restart-button__icon {
  width: 38px;
  display: block;
}

.timeline {
  flex: 1;
}
</style>
