<template>
  <h1>{{ title }}</h1>
  <p>Welcome ...</p>
  <teleport to="#modals" v-if="showModal">
    <!-- Slots -->
    <Modal theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">login</a>
        <a href="#">logout</a>
      </template>
      <h1>{{ modalHeader }}</h1>
      <p>{{ modalText }}</p>
    </Modal>
  </teleport>

  <teleport  to="#modals" v-if="showModalTwo">
    <!-- Slots -->
    <Modal theme="login" @close="toggleModalTwo">
      <template v-slot:contetnt>
        <div>
          <p>Content two</p>
        </div>
      </template>
      <h1>Header text two</h1>
    </Modal>
  </teleport>
  <!-- click event modifier -->
  <button @click.alt="toggleModal">open modal (alt)</button>
  <button @click="toggleModalTwo">open modal two</button>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: {
    Modal
  },
  data() {
    return {
      title: 'My first vue app!!!',
      modalHeader: "Header text slot",
      modalText: "Content text slot",
      showModal: false,
      modalHeaderTwo: "",
      modalTextTwo: "Content text two",
      showModalTwo: false
    }
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    },

  }
}
</script>

<style>
#app, #modals {
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
  padding-bottom: 10px;
}
</style>
