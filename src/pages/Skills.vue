<template>
  <q-page >
    <div class="q-pa-md text-center text-h4 text-grey-9">
      Skills
    </div>
    <div class="row">
      <div 
          v-for="(skill, index) in skills"
          :key="skill.id"
          class="q-pa-md col-12 col-md-auto flex flex-center"
      >
        <q-card
          class="my-card"
          flat
          bordered
          dark
        >
          <q-card-section horizontal>
              <q-card-section class="q-pt-xs col">
              <div class="text-h5 q-mt-sm q-mb-xs ">{{ skill.title }}</div>
              <div class="text-caption text-grey">
                {{ skill.lorem }}
              </div>
              </q-card-section>

              <q-card-section class="col flex justify-end">
            <!-- <q-img
                  :src="'~assets/' + skill.pic"
                  width="150px"
                  class="rounded-borders"
                  
              /> -->
              <q-img
                  :src="skill.url"
                  fit
                  class="rounded-borders"
              />
              </q-card-section>
          </q-card-section>

          <q-separator />

          <q-card-actions>
              <q-btn flat color="primary">
              See more
              </q-btn>
          </q-card-actions>
          </q-card>
      </div>
    </div>
  </q-page>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    const skills = ref([
      {id: 0, title: 'HTML/CSS', 
      lorem: 'I got my first web certification from freecodecamp, learning html, css grid and flexbox, responsive web design.', 
      pic: 'html-css.jpeg', 
      url: 'http://www.augermiquel.com/wp-content/uploads/2019/10/html-css.png'},

      {id: 1, title: 'Vue JS', 
      lorem: 'After learning the basics of javascript, I chose Vuejs framework as the way to go, just because I find it easy to learn and implement, I took some courses from vuemastery and vueschool to learn from basic to intermidiate level skills such as components, vue-router, composition api, and pinia as a state managment.', 
      pic: 'vuejs.png', 
      url: 'https://cdn.iconscout.com/icon/free/png-256/vue-282497.png'},

      {id: 2, title: 'Firebase', 
      lorem: 'One of the last technologies I have learn or at least learned the basics to implement as a backend for quick and scalable projects.', 
      pic: 'firebase.jpg', 
      url: 'https://www.shareicon.net/data/256x256/2016/07/08/117548_google_512x512.png'}
    ])

    return {
      skills
    }
  }
}
</script>

<style lang="sass" scoped>
.my-card
  width: 100%
  max-width: 350px
  //background-color: $indigo-2
</style>