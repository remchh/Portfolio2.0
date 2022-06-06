<template>
  <q-page >
    <div class="q-pa-md text-center text-h4 text-grey-9">
      Skills
    </div>
    <div 
        v-for="(skill, index) in skills"
        :key="skill.id"
        class="q-pa-md"
    >
      <q-card
        class="my-card"
        flat
        bordered

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
                width="150px"
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
  </q-page>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    const skills = ref([
      {id: 0, title: 'HTML/CSS', lorem: 'lorem lorem', pic: 'html-css.jpeg', url: 'http://www.augermiquel.com/wp-content/uploads/2019/10/html-css.png'},
      {id: 1, title: 'Vue JS', lorem: 'lorem lorem', pic: 'vuejs.png', url: 'https://assets.codepen.io/t-1003/internal/avatars/teams/default.png'},
      {id: 2, title: 'Firebase', lorem: 'lorem lorem', pic: 'firebase.jpg', url: 'https://www.shareicon.net/data/256x256/2016/07/08/117548_google_512x512.png'}
    ])
    /*const text = ref('lorem')
    const tittle = ref('HTML/CSS')
    const pic = ref('https://cdn.quasar.dev/img/parallax2.jpg')*/
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