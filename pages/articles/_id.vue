<template>
  <div>
    <div v-show="loading" class="loader">
      Loading...
    </div>
    <div v-show="!loading">
      <Navbar />
      <div class="bg-gray-200 h-screen py-32">
        <div class="container max-w-screen-lg px-8 py-12 mx-auto bg-white rounded-lg shadow">
          <div class="flex flex-col text-center w-full mb-3">
            <h1 class="text-2xl font-medium title-font text-gray-900">
              {{ article.title }}
            </h1>
          </div>
          <hr class="border-dashed border-4 max-w-lg mx-auto my-5 border-primary">
          <div class="flex flex-row">
            <p class="text-gray-600 mr-4">
              公開: {{ dateformat(article.published_at) }}
            </p>
            <p class="text-gray-600 mr-4">
              更新: {{ dateformat(article.updated_at) }}
            </p>
          </div>
          <div class="body" v-html="$md.render(article.body)" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import axios from 'axios'

export default Vue.extend({
  name: 'Index',
  components: {
  },
  data () {
    return {
      article: {
        body: 'c4y',
        published_at: '2021-03-01T10:01:18.166Z',
        updated_at: '2021-03-01T10:01:18.166Z'
      },
      error: null,
      loading: true
    }
  },
  async mounted () {
    try {
      const articlesRes = await axios.get(`https://strapi.code4yay.dev/articles/${this.$route.params.id}`)
      this.article = articlesRes.data
      this.loading = false
    } catch (error) {
      this.error = error
    }
  },
  methods: {
    dateformat (date) {
      return this.$dateformat(new Date(date), 'yyyy年mm月dd日 HH:MM')
    }
  }
})
</script>

<style lang="scss">
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
  .body {
    @apply text-gray-800;
    h1 {
      @apply text-2xl;
      @apply font-bold;
      @apply my-2;
    }
    h2 {
      @apply text-xl;
      @apply font-bold;
      @apply my-2;
    }
    h3 {
      @apply text-lg;
      @apply font-bold;
      @apply my-2;
    }
    h4 {
      @apply font-bold;
      @apply my-2;
    }
    p {
      @apply mb-3;
    }

    a {
      @apply text-denim-600;
    }
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
