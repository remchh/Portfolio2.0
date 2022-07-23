<template>
  <q-layout view="lHh Lpr lFf">
    <q-header style="height: 150px">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          Welcome!
        </q-toolbar-title>


      </q-toolbar>
      <template v-if="weatherData">
        <div class="row items-center text-white text-center">
          <div class="col">
            <div class="text-h6 text-weight-light">
              {{weatherData.name}}
            </div>
            <div class="text-h6 text-weight-light ">
              {{weatherData.weather[0].main}}
            </div>
          </div>
          <div class="text-h4 text-weight-thin q-my-lg relative-position">
            <span>{{Math.round(weatherData.main.temp)}}</span>
            <span class="text-h4 text-weight-thin relative-position degree">&deg;C</span>
          </div>
          <div class="text-center">
            <img :src="`http://openweathermap.org/img/wn/${weatherData.weather[0].icon}@2x.png`">
          </div>
        </div>
      </template>
      
      <div v-if="!weatherData" class="col q-pt-xl q-px-md">
        <q-input
          v-model="search"
          placeholder="Enter your city location"
          @keyup.enter="getWeatherBySearch"
          dark
          borderless
          >
          <template v-slot:before>
            <q-icon
              name="my_location" 
            />
          </template>

          <template v-slot:append>
            <q-btn
            @click="getWeatherBySearch"
              round
              dense
              flat
              icon="search" 
              />
          </template>
        </q-input>
      </div>
    </q-header>

     <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="200"
        :breakpoint="700"
      >
        <q-scroll-area style="height: calc(100% - 150px); margin-top: 150px; border-right: 1px solid #ddd">
          <q-list padding>
            <q-item
              to="/"
              clickable
              v-ripple
              exact  
            >
              <q-item-section avatar>
                <q-icon name="inbox" />
              </q-item-section>

              <q-item-section>
                About me
              </q-item-section>
            </q-item>

            <q-item
              to="/Projects"
              clickable
              v-ripple
              exact
            >
              <q-item-section avatar>
                <q-icon name="star" />
              </q-item-section>

              <q-item-section>
                Projects
              </q-item-section>
            </q-item>

            <q-item
              to="/Skills"
              clickable
              v-ripple
              exact
            >
              <q-item-section avatar>
                <q-icon name="send" />
              </q-item-section>

              <q-item-section>
                Skills
              </q-item-section>
            </q-item>


          </q-list>

            <q-separator inset />

            <q-list>
            <div class="column flex-center" >

              <q-item
                href="https://github.com/remchh"
                target="_blank"
                clickable
                v-ripple
                exact
              >
                <q-item-section avatar >
                  <q-icon right name="fa-brands fa-github" />
                </q-item-section>

              </q-item>

              <q-item
                href="https://t.me/remch13"
                target="_blank"
                clickable
                v-ripple
                exact
              >
                <q-item-section avatar >
                  <q-icon right name="fa-brands fa-telegram" />
                </q-item-section>
              </q-item>

              <q-item
                href="https://www.linkedin.com/in/rafael-mejia-chevez-820494176"
                target="_blank"
                clickable
                v-ripple
                exact
              >  
                <q-item-section avatar >
                  <q-icon right name="fa-brands fa-linkedin-in" />
                </q-item-section>
              </q-item>

            </div>
            </q-list>
 
            <q-separator inset />

            <!-- <q-btn color="amber" text-color="black" dense round icon="fa-brands fa-linkedin-in" /> -->

        </q-scroll-area>

        <q-img class="absolute-top bg-primary" style="height: 150px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="https://cdn.quasar.dev/img/boy-avatar.png">
            </q-avatar>
            <div class="text-weight-bold">Rafael Mejia</div>
            <div>@remchh</div>
          </div>
        </q-img>
      </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { ref } from 'vue'
import axios from 'axios'
import { useQuasar } from 'quasar'

export default {

  setup () {
    const leftDrawerOpen = ref(false)
    const $q = useQuasar()
    const search = ref('')
    const weatherData = ref(null)
    const apiKey = ref('52e8e4553c2d6e62aea2c8e174025ad7')
    const baseUrl = ref('https://api.openweathermap.org/data/2.5/weather')
    const getWeatherBySearch = () => {
      $q.loading.show()
      axios(`${baseUrl.value}?q=${ search.value }&appid=${apiKey.value}&units=metric`)
      .then(response => {
        weatherData.value = response.data
        search.value = ''
        $q.loading.hide()
      })
    }

    return {
      search,
      weatherData,
      getWeatherBySearch,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
}

//CHATBOT
//DARKMODE
//AVATAR

</script>

<style lang="sass" scoped>
  .q-item__section--side
    padding-right: 0px
</style>
