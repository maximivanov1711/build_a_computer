<template>
  <div class="timeline">
    <StageCircle
      v-for="stage in stages"
      :key="stage.id"
      :stage="stage"
      :currentStage="currentStage"
      @click="changeCurrentStage(stage.id)"
    />
    <div class="timeline__line timeline__line-gray"></div>
  </div>
</template>

<script>
import StageCircle from "./timeline/StageCircle.vue";

import stages from "../../data/stages.json";

export default {
  name: "TimeLine",
  props: ["activeStage", "currentStage"],
  components: {
    StageCircle,
  },
  methods: {
    changeCurrentStage(stageId) {
      if (stageId <= this.activeStage) {
        this.$emit("changeCurrentStage", stageId);
      }
    },
  },
  computed: {
    stages() {
      return stages.map((stage) => {
        return {
          ...stage,
          isCompleted: stage.id <= this.activeStage,
        };
      });
    },
  },
};
</script>

<style scoped>
.timeline {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.timeline__line {
  height: 4px;
  position: absolute;
  top: 50%;
  transform: translate(0, -50%);
}
.timeline__line-green {
  z-index: 1;
  background: var(--main-green);
}
.timeline__line-gray {
  width: 100%;
  background: var(--dark-gray);
}
</style>
