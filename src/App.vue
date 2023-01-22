<template>
  <h1>{{title}}</h1>
  <!-- <input type="text" ref="name"> -->
  <!-- <button @click="handleClick">click me</button> -->
  <p>Welcome...</p>
  <teleport to="#modals" v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <template v-slot:links> 
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>{{header}}</h1>
      <p>{{text}}</p>
    </Modal>
  </teleport>
  <button @click.alt="toggleModal">open modal (alt)</button>

  <teleport to="#modals" v-if="showModal2">
    <Modal @close="toggleModal2">
      <template v-slot:links> 
        <a href="#">Check here</a>
        <a href="#">Research here</a>
      </template>
      <h1>This is Modal number 2</h1>
      <p>Want to know how this is created?</p>
    </Modal>
  </teleport>
  <button @click="toggleModal2">open modal 2</button>
</template>

<script>

import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: { Modal },
  data() {
    return{
      title: 'Tims Vue App :)',
      header: 'Sign up for the Giveaway!',
      text: 'Grab your timmy swag for half price',
      showModal: false,
      showModal2: false
    }
  },
  methods: {
    // handleClick(){
    //   console.log(this.$refs.name)
    //   this.$refs.name.classList.add('active')
    //   this.$refs.name.focus()
    // }
    toggleModal () {
      this.showModal = !this.showModal
    },
    toggleModal2 () {
      this.showModal2 = !this.showModal2
    }
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