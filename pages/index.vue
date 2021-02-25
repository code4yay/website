<template>
  <div>
    <Navbar />
    <section id="hero" class="hero text-gray-300 body-font bg-secondary">
      <div class="container mx-auto flex px-5 py-24 items-center justify-center flex-col">
        <div class="text-center lg:w-2/3 w-full">
          <h1 class="title-font sm:text-4xl text-3xl mb-4 font-medium text-primary">
            We make something fun, by the fun, for the fun.
          </h1>
          <p class="mb-8 leading-relaxed">
            Code for Yay は楽しいものを楽しむために楽しく作るクリエイターグループです。
          </p>
        </div>
      </div>
    </section>
    <section id="members" class="text-gray-600 body-font bg-gray-100">
      <div class="container px-5 py-24 mx-auto">
        <div class="flex flex-col text-center w-full mb-10">
          <h1 class="text-2xl font-medium title-font text-gray-900">
            Members
          </h1>
        </div>
        <div class="flex flex-wrap -m-4">
          <div v-for="member in members" :key="member.id" class="p-4 lg:w-1/4 md:w-1/2 ">
            <img alt="team" class="flex-shrink-0 rounded-t-lg w-full h-56 object-cover object-center" :src="member.profile.url">
            <div class="p-6 bg-white rounded-b-lg shadow-lg">
              <div class="h-full bg-white flex flex-col items-center text-center">
                <div class="w-full">
                  <h2 class="title-font font-medium text-lg text-gray-900">
                    {{ member.name }}
                  </h2>
                  <h3 class="text-gray-500 mb-3">
                    {{ member.role }}
                  </h3>
                  <div class="socials">
                    <a v-if="member.twitter" :href="`https://twitter.com/${ member.twitter }`">
                      <font-awesome-layers class="fa-2x">
                        <font-awesome-icon :icon="['fab', 'twitter']" />
                      </font-awesome-layers>
                    </a>
                    <a v-if="member.github" :href="`https://github.com/${ member.github }`">
                      <font-awesome-layers class="fa-2x">
                        <font-awesome-icon :icon="['fab', 'github']" />
                      </font-awesome-layers>
                    </a>
                    <a v-if="member.link" :href="member.link">
                      <font-awesome-layers class="fa-2x">
                        <font-awesome-icon icon="link" />
                      </font-awesome-layers>
                    </a>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section id="works" class="text-gray-600 body-font bg-gray-300">
      <div class="container px-5 py-24 mx-auto">
        <div class="flex flex-wrap w-full mb-10">
          <div class="flex flex-col text-center w-full">
            <h1 class="text-2xl font-medium title-font text-gray-900">
              Works
            </h1>
          </div>
        </div>
        <div class="flex flex-wrap -m-4">
          <div class="xl:w-1/4 md:w-1/2 p-4">
            <div class="bg-white p-6 rounded-lg shadow-lg">
              <img class="h-40 rounded w-full object-cover object-center mb-6" src="https://dummyimage.com/720x400" alt="content">
              <h3 class="tracking-widest text-indigo-500 text-xs font-medium title-font">
                SUBTITLE
              </h3>
              <h2 class="text-lg text-gray-900 font-medium title-font mb-4">
                Chichen Itza
              </h2>
              <p class="leading-relaxed text-base">
                Fingerstache flexitarian street art 8-bit waistcoat. Distillery hexagon disrupt edison bulbche.
              </p>
            </div>
          </div>
          <div class="xl:w-1/4 md:w-1/2 p-4">
            <div class="bg-white p-6 rounded-lg shadow-lg">
              <img class="h-40 rounded w-full object-cover object-center mb-6" src="https://dummyimage.com/721x401" alt="content">
              <h3 class="tracking-widest text-indigo-500 text-xs font-medium title-font">
                SUBTITLE
              </h3>
              <h2 class="text-lg text-gray-900 font-medium title-font mb-4">
                Colosseum Roma
              </h2>
              <p class="leading-relaxed text-base">
                Fingerstache flexitarian street art 8-bit waistcoat. Distillery hexagon disrupt edison bulbche.
              </p>
            </div>
          </div>
          <div class="xl:w-1/4 md:w-1/2 p-4">
            <div class="bg-white p-6 rounded-lg shadow-lg">
              <img class="h-40 rounded w-full object-cover object-center mb-6" src="https://dummyimage.com/722x402" alt="content">
              <h3 class="tracking-widest text-indigo-500 text-xs font-medium title-font">
                SUBTITLE
              </h3>
              <h2 class="text-lg text-gray-900 font-medium title-font mb-4">
                Great Pyramid of Giza
              </h2>
              <p class="leading-relaxed text-base">
                Fingerstache flexitarian street art 8-bit waistcoat. Distillery hexagon disrupt edison bulbche.
              </p>
            </div>
          </div>
          <div class="xl:w-1/4 md:w-1/2 p-4">
            <div class="bg-white p-6 rounded-lg shadow-lg">
              <img class="h-40 rounded w-full object-cover object-center mb-6" src="https://dummyimage.com/723x403" alt="content">
              <h3 class="tracking-widest text-indigo-500 text-xs font-medium title-font">
                SUBTITLE
              </h3>
              <h2 class="text-lg text-gray-900 font-medium title-font mb-4">
                San Francisco
              </h2>
              <p class="leading-relaxed text-base">
                Fingerstache flexitarian street art 8-bit waistcoat. Distillery hexagon disrupt edison bulbche.
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import axios from 'axios'

export default Vue.extend({
  name: 'Index',
  data () {
    return {
      members: [],
      error: null
    }
  },
  async mounted () {
    try {
      const response = await axios.get('https://code4yay-strapi.herokuapp.com/members')
      this.members = response.data
    } catch (error) {
      this.error = error
    }
  }
})
</script>

<style>
</style>
