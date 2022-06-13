<template>
  <q-page >
    <div class="q-pa-md text-center text-h4 text-grey-9">
      Projects
    </div>
    <div class="row">
      <div
        v-for="(project, index) in projects"
        class="q-pa-md col-12 col-md-4 flex flex-center" 
        >
        <q-card class="my-card" flat bordered>
          <q-img
              loading
              :src="project.pic"
          />

          <q-card-section>
              <div class="text-h5 q-mt-sm q-mb-xs">{{project.title}}</div>
              <div class="text-caption text-grey">
                {{project.lorem}}
              </div>
          </q-card-section>

          <q-card-actions>
              <q-btn 
              flat color="primary" 
              label="CHECK OUT"
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
      lorem: 'My first real project',
      lorem1: 'I made this website using a framework call Vuetify, then implemented a form backend from a third-party that works just fine, and lastly deployed it trough netlify', 
      pic:'https://i.ibb.co/dM0Tp8G/qualityfountain.jpg', expanded: false, href: 'https://quality-fountain-service.netlify.app'},
      {id: 1, title: 'New Project', 
      lorem: 'coming soon', lorem1: 'An incredible project coming soon', 
      pic: 'https://cdn.quasar.dev/img/parallax2.jpg', expanded: false},
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
  max-width: 350px
</style>