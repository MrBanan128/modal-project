<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <teleport to=".modals" v-if="showModal">
    <Modal :header="header" :text="text" theme="" @close="toggleModal">
      <template v-slot:links>
        <a href="#">sign up now </a>
        <a href="#">more info </a>
      </template>
      <h1>Ninja Giveaway</h1>
      <p>Grab your ninja swaf for half price!</p>
    </Modal>
  </teleport>
  <teleport to=".modals" v v-if="showModal2">
    <Modal @close="toggleModal2">
      <h1>Sign up to the newsletter</h1>
      <p>For updates and promo codes</p>
    </Modal>
  </teleport>
  <button @click.alt="toggleModal">Open modal (alt)</button>
  <button @click.shift="toggleModal2">Open modal (shift)</button>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: {
    Modal,
  },

  data() {
    return {
      title: "My first view app",
      header: "Sign up for giveaway!",
      text: "Grab your ninja swag for half price",
      showModal: false,
      showModal2: false,
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.add("active");
      this.$refs.name.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModal2() {
      this.showModal2 = !this.showModal2;
    },
  },
};
</script>

<style>
#app,
.modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
}
.modal.sale {
  background: crimson;
  color: white;
}
.modal.sale h1 {
  color: white;
}
</style>
