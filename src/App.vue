<template>
  <div class="wrapper">
    <div class="wrapper-content">

      <section>
        <div class="container">

          <button class="btn btnPrimary" @click="modalFirst = !modalFirst">Show First Modal</button>

          <Modals 
          title="First Modal" 
          v-show="modalFirst"
          @close="modalFirst = !modalFirst"
          >
          <div slot="body">
            <p>Text</p>
            <button class="btn btnPrimary" @click="modalFirst = !modalFirst">Well done!</button>
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
      modalFirst: false
    }
  }
}
</script>

<style scoped>


</style>
