<template>
  <div class="char-desc-modal">
    <h2>{{ charName }}:</h2>
    <p>{{ charDesc }}</p>
    <div class="close-modal-button" @click="toggleModal">Понятно</div>
  </div>
</template>

<script>
export default {
  name: "CharDescModal",
  props: ["charName", "charDesc"],
  methods: {
    toggleModal() {
      document.querySelector(".char-desc-modal").classList.toggle("show");
    },
  },
};
</script>

<style scoped>
.char-desc-modal {
  display: none;
  width: 400px;
  border-radius: 25px;
  overflow: hidden;
  background: #fff;
}

.char-desc-modal h2 {
  margin: 0;
  padding: 20px;
  border-bottom: 4px solid var(--gray);
  background: var(--light-gray);
}

.char-desc-modal p {
  margin: 0;
  padding: 20px;
  font-size: 20px;
}

.char-desc-modal.show {
  display: block;
}
</style>
