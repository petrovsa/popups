<template>
  <div>
    <button @click="openPopup">Відкрити вікно</button>
    <PopupModal
      :is-open="isPopupOpen"
      @close="isPopupOpen = false"
      @ok="popupConfirmed"
    >
      Ви дійсно хочете освоїти правильні підходи?
      <template #actions="{ ok }">
        Напишіть
        <input
          v-model="confirmation"
          :placeholder="$options.CONFIRMATION_TEXT"
        />
        &nbsp;
        <button :disabled="!isConfirmationCerrect" @click="ok">Ok</button>
      </template>
    </PopupModal>
  </div>
</template>

<script>
import PopupModal from "./components/PopupModal.vue";
export default {
  name: "App",
  components: {
    PopupModal,
  },
  data() {
    return {
      isPopupOpen: false,
      confirmation: "",
    };
  },
  methods: {
    popupConfirmed() {
      alert("confirmed");
      this.isPopupOpen = false;
    },
    openPopup() {
      this.confirmation = "";
      this.isPopupOpen = true;
    },
  },
  CONFIRMATION_TEXT: "ПІДТВЕРДЖУЮ",
  computed: {
    isConfirmationCerrect() {
      return this.confirmation === this.$options.CONFIRMATION_TEXT;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
