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

        </div>
      </section>

    </div>
  </div>
</template>

<script>
import Modals from './components/Modal'

export default {
  components: {
    Modals
  },
  data() {
    return {
      modalFirst: false,
      modalSecond: {
        show: false,
        name: '',
        email: ''
      }
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
