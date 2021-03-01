<template>
  <div>
    <div v-show="loading" class="loader">
      Loading...
    </div>
    <div v-show="!loading">
      <Navbar />
      <section id="hero" class="hero text-gray-300 body-font bg-secondary">
        <div class="container mx-auto flex px-5 py-24 items-center justify-center flex-col">
          <img class="object-contain h-64 w-full " src="~/assets/code-for-yay-square.png" alt="">
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
          <div class="flex flex-wrap justify-center">
            <div v-for="member in members" :key="member.id" class="p-4 lg:w-1/4 md:w-1/2">
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
      <section class="text-gray-600 body-font">
        <div class="container px-5 py-24 mx-auto">
          <div class="flex flex-col text-center w-full mb-10">
            <h1 class="text-2xl font-medium title-font text-gray-900">
              News
            </h1>
          </div>
          <div class="flex flex-wrap -m-4">
            <div v-for="article in articles" :key="article.id" class="p-4 md:w-1/3">
              <div class="h-full shadow-lg rounded-lg overflow-hidden">
                <img class="lg:h-56 md:h-48 w-full object-cover object-center" :src="article.thumbnail.url" alt="blog">
                <div class="p-6">
                  <h1 class="title-font text-lg font-medium text-gray-900 mb-3">
                    <a :href="`/articles/${ article.id }`">{{ article.title }}</a>
                  </h1>
                  <p class="leading-relaxed mb-3">
                    {{ article.descriptions }}
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import axios from 'axios'

export default Vue.extend({
  name: 'Index',
  components: {
  },
  data () {
    return {
      members: [],
      articles: [],
      error: null,
      loading: true
    }
  },
  async mounted () {
    try {
      const membersRes = await axios.get('https://strapi.code4yay.dev/members')
      this.members = membersRes.data
      const articlesRes = await axios.get('https://strapi.code4yay.dev/articles')
      this.articles = articlesRes.data

      this.loading = false
    } catch (error) {
      this.error = error
    }
  }
})
</script>

<style>
  .loader {
    color: #39e991;
    font-size: 90px;
    text-indent: -9999em;
    overflow: hidden;
    width: 1em;
    height: 1em;
    border-radius: 50%;
    margin: 40vh auto;
    position: relative;
    -webkit-transform: translateZ(0);
    -ms-transform: translateZ(0);
    transform: translateZ(0);
    -webkit-animation: load6 1.7s infinite ease, round 1.7s infinite ease;
    animation: load6 1.7s infinite ease, round 1.7s infinite ease;
  }
  @-webkit-keyframes load6 {
    0% {
      box-shadow: 0 -0.83em 0 -0.4em, 0 -0.83em 0 -0.42em, 0 -0.83em 0 -0.44em, 0 -0.83em 0 -0.46em, 0 -0.83em 0 -0.477em;
    }
    5%,
    95% {
      box-shadow: 0 -0.83em 0 -0.4em, 0 -0.83em 0 -0.42em, 0 -0.83em 0 -0.44em, 0 -0.83em 0 -0.46em, 0 -0.83em 0 -0.477em;
    }
    10%,
    59% {
      box-shadow: 0 -0.83em 0 -0.4em, -0.087em -0.825em 0 -0.42em, -0.173em -0.812em 0 -0.44em, -0.256em -0.789em 0 -0.46em, -0.297em -0.775em 0 -0.477em;
    }
    20% {
      box-shadow: 0 -0.83em 0 -0.4em, -0.338em -0.758em 0 -0.42em, -0.555em -0.617em 0 -0.44em, -0.671em -0.488em 0 -0.46em, -0.749em -0.34em 0 -0.477em;
    }
    38% {
      box-shadow: 0 -0.83em 0 -0.4em, -0.377em -0.74em 0 -0.42em, -0.645em -0.522em 0 -0.44em, -0.775em -0.297em 0 -0.46em, -0.82em -0.09em 0 -0.477em;
    }
    100% {
      box-shadow: 0 -0.83em 0 -0.4em, 0 -0.83em 0 -0.42em, 0 -0.83em 0 -0.44em, 0 -0.83em 0 -0.46em, 0 -0.83em 0 -0.477em;
    }
  }
  @keyframes load6 {
    0% {
      box-shadow: 0 -0.83em 0 -0.4em, 0 -0.83em 0 -0.42em, 0 -0.83em 0 -0.44em, 0 -0.83em 0 -0.46em, 0 -0.83em 0 -0.477em;
    }
    5%,
    95% {
      box-shadow: 0 -0.83em 0 -0.4em, 0 -0.83em 0 -0.42em, 0 -0.83em 0 -0.44em, 0 -0.83em 0 -0.46em, 0 -0.83em 0 -0.477em;
    }
    10%,
    59% {
      box-shadow: 0 -0.83em 0 -0.4em, -0.087em -0.825em 0 -0.42em, -0.173em -0.812em 0 -0.44em, -0.256em -0.789em 0 -0.46em, -0.297em -0.775em 0 -0.477em;
    }
    20% {
      box-shadow: 0 -0.83em 0 -0.4em, -0.338em -0.758em 0 -0.42em, -0.555em -0.617em 0 -0.44em, -0.671em -0.488em 0 -0.46em, -0.749em -0.34em 0 -0.477em;
    }
    38% {
      box-shadow: 0 -0.83em 0 -0.4em, -0.377em -0.74em 0 -0.42em, -0.645em -0.522em 0 -0.44em, -0.775em -0.297em 0 -0.46em, -0.82em -0.09em 0 -0.477em;
    }
    100% {
      box-shadow: 0 -0.83em 0 -0.4em, 0 -0.83em 0 -0.42em, 0 -0.83em 0 -0.44em, 0 -0.83em 0 -0.46em, 0 -0.83em 0 -0.477em;
    }
  }
  @-webkit-keyframes round {
    0% {
      -webkit-transform: rotate(0deg);
      transform: rotate(0deg);
    }
    100% {
      -webkit-transform: rotate(360deg);
      transform: rotate(360deg);
    }
  }
  @keyframes round {
    0% {
      -webkit-transform: rotate(0deg);
      transform: rotate(0deg);
    }
    100% {
      -webkit-transform: rotate(360deg);
      transform: rotate(360deg);
    }
  }
</style>
