<template>
  <div class="wrapper">
    <div class="wrapper-content">

      <section>
        <div class="container">

          <!-- first modal -->
          <button class="btn btnPrimary" @click="modalFirst = !modalFirst">Show First Modal</button>
          <Modals 
          title="First Modal" 
          v-show="modalFirst"
          @close="modalFirst = false"
          >
          <div slot="body">
            <p>Text</p>
            <button class="btn btnPrimary" @click="modalFirst = !modalFirst">Well done!</button>
          </div>
          </Modals>

          <!-- second modal -->
          <button class="btn btnPrimary" @click="modalSecond.show = !modalSecond.show">Show Second Modal</button>
          <Modals 
          title="Second Modal" 
          v-show="modalSecond.show"
          @close="modalSecond.show = false"
          >
          <div slot="body">
            <!-- <p>Text</p> -->
            <form @submit.prevent="submitSecondForm">
            <label>Name:</label>
            <input type="text" required v-model="modalSecond.name">
            <label>E-mail:</label>
            <input type="email" required v-model="modalSecond.email">
            <button class="btn btnPrimary">Submit!</button>

            </form>
          </div>
          </Modals>

          <!-- modal with validation -->
          <button class="btn btnPrimary" @click="modalValidate = !modalValidate">Show Modal Validate</button>
          <ModalValidate v-show="modalValidate"  @close="modalValidate = false"/>

        </div>
      </section>

    </div>
  </div>
</template>

<script>
import Modals from './components/Modal'
import ModalValidate from './components/ModalValidate'

export default {
  components: {
    Modals, ModalValidate
  },
  data() {
    return {
      modalFirst: false,
      modalSecond: {
        show: false,
        name: '',
        email: ''
      },
      modalValidate: false
    }
  },
  methods: {
    submitSecondForm() {
      console.log({
        name: this.modalSecond.name,
        email: this.modalSecond.email
      });
      this.modalSecond.name = ''
      this.modalSecond.email = ''
      this.modalSecond.show = false
    }
  }
}
</script>

<style scoped>


</style>
