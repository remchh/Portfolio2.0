<template>
  <q-page >
    <div class="q-pa-md text-center text-h4 text-grey-9">
      Skills
    </div>
    <div class="row justify-around">
      <div 
          v-for="(skill, index) in skills"
          :key="skill.id"
          class="q-pa-lg col-12 col-md-auto flex flex-center"
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
              <div class="text-subtitle2 text-weight-light text-grey-4">
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
                  width="200px"
                  height="200px"
                  fit
                  class="rounded-borders"
              />
              </q-card-section>
          </q-card-section>

          <q-separator />

          <q-card-actions>
              <q-btn 
              :href="skill.href"
              target="_blank"
              flat 
              color="primary">
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
      url: 'http://www.augermiquel.com/wp-content/uploads/2019/10/html-css.png',
      href: 'https://freecodecamp.com'
      },

      {id: 1, title: 'Vue JS', 
      lorem: 'After learning the basics of javascript, I chose Vuejs framework as the way to go, I took some courses from vuemastery and vueschool to learn from basic to intermidiate level skills such as components, vue-router, composition api and pinia.', 
      url: 'https://cdn.iconscout.com/icon/free/png-256/vue-282497.png',
      href: 'https://vuejs.org'
      },

      {id: 2, title: 'Firebase', 
      lorem: 'One of the last technologies I have learned or at least learned the basics to use as a quickly and easy to implement backend for my projects.', 
      url: 'https://www.shareicon.net/data/256x256/2016/07/08/117548_google_512x512.png',
      href: 'https://www.firebase.com'
      },

      {id: 3, title: 'Quasar', 
      lorem: 'I found quasar the easiest way not just to develop web applications but also multi platform web applications using basically the same code, which is incredible! ', 
      url: 'https://v0-17.quasar-framework.org/images/quasar-logo-big.png',
      href: 'https://quasar.dev'
      }
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