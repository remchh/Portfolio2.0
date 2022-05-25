<template>
  <q-page >
    <div class="q-pa-md text-center text-h4 text-grey-9">
      Projects
    </div>
    <div
      v-for="(project, index) in projects"
      class="q-pa-md row items-start q-gutter-md" 
    >
      <q-card class="my-card" flat bordered>
        <q-img
            :src="project.pic"
        />

        <q-card-section>
            <div class="text-h5 q-mt-sm q-mb-xs">{{project.title}}</div>
            <div class="text-caption text-grey">
              {{project.lorem}}
            </div>
        </q-card-section>

        <q-card-actions>
            <q-btn flat color="primary" label="CHECK OUT" />

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
  </q-page>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    const projects = ref([
      {id: 0, title: 'Quality Fountain Service', 
      lorem: 'lorem lorem', lorem1: 'lorem lorem', 
      pic:'https://cdn.quasar.dev/img/parallax2.jpg', expanded: false},
      {id: 1, title: 'Quality Fountain Service', 
      lorem: 'lorem lorem', lorem1: 'lorem lorem', 
      pic: 'https://cdn.quasar.dev/img/parallax2.jpg', expanded: false},
      {id: 2, title: 'Quality Fountain Service', 
      lorem: 'lorem lorem', lorem1: 'lorem lorem', 
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