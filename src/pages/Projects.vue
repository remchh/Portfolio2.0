<template>
  <q-page >
    <div class="q-pa-md text-center text-h4 text-grey-9">
      Projects
    </div>
    <div class="row justify-around">
      <div
        v-for="(project, index) in projects"
        class="q-pa-lg col-12 col-md-auto flex flex-center" 
        >
        <q-card class="my-card" flat bordered>
          <q-img
              loading
              :src="project.pic"
          />

          <q-card-section>
              <div class="text-h5 q-mt-sm q-mb-xs">{{project.title}}</div>
              <div class="text-subtitle2 text-weight-light text-grey-8">
                {{project.lorem}}
              </div>
          </q-card-section>

          <q-card-actions>
              <q-btn 
              flat color="primary" 
              label="CHECK IT OUT"
              :href="project.href"
              target="_blank"
              />

              <q-space />

              <q-btn
              color="grey"
              round
              flat
              dense
              :icon="project.expanded ? 'keyboard_arrow_up' : 'keyboard_arrow_down'"
              @click="project.expanded = !project.expanded"
              />
          </q-card-actions>

          <q-slide-transition>
              <div v-show="project.expanded">
              <q-separator />
              <q-card-section class="text-subitle2">
                  {{ project.lorem1 }}
              </q-card-section>
              </div>
          </q-slide-transition>
        </q-card>
      </div>
    </div>
  </q-page>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    const projects = ref([
      {id: 0, title: 'Quality Fountain Service', 
      lorem: 'A website for a real small business',
      lorem1: 'I made this website using a framework call Vuetify, then implemented a form backend from a third-party service, and lastly deployed it trough Netlify.', 
      pic:'https://i.ibb.co/dM0Tp8G/qualityfountain.jpg', expanded: false, href: 'https://quality-fountain-service.netlify.app'},
      {id: 1, title: 'Football Stadium App', 
      lorem: 'A web app using RESTful API', lorem1: 'This project was made with Quasar V2, and rapidAPI which help me to get a better understanding of how to work with API and JS. In this case I deployed it trough Heroku CLI.  ', 
      pic: 'https://images.unsplash.com/photo-1540747913346-19e32dc3e97e?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2805&q=80', expanded: false, href: 'https://football-stadium-app.herokuapp.com/#/'},
      {id: 2, title: 'New Project', 
      lorem: 'coming soon', lorem1: 'An increduble project coming soon', 
      pic:'https://cdn.quasar.dev/img/parallax2.jpg', expanded: false}
    ])
    return {
      projects
    }
  }
}
</script>

<style lang="sass" scoped>
.my-card
  width: 100%
  width: 350px
  max-width: 350px
</style>