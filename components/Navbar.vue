<template>
  <nav class="relative flex flex-wrap items-center justify-between px-2 py-3 navbar-expand-lg bg-secondary">
    <div class="container px-4 mx-auto flex flex-wrap items-center justify-between">
      <div class="w-full relative flex justify-between lg:w-auto  px-4 lg:static lg:block lg:justify-start">
        <a class="text-xl font-bold leading-relaxed inline-block mr-4 py-2 whitespace-no-wrap uppercase text-primary" href="/">
          Code for Yay
        </a>
        <button class="text-white cursor-pointer text-xl leading-none px-3 py-1 border border-solid border-transparent rounded bg-transparent block lg:hidden outline-none focus:outline-none" type="button" @click="toggleNavbar()">
          <font-awesome-icon icon="bars" />
        </button>
      </div>
      <div :class="{'hidden': !showMenu, 'flex': showMenu}" class="lg:flex lg:flex-grow items-center">
        <ul class="flex flex-col lg:flex-row list-none ml-auto">
          <li class="nav-item">
            <a class="px-3 py-2 flex items-center text-xs uppercase font-bold leading-snug text-white hover:opacity-75" href="#pablo">
              <span class="ml-2">Share</span>
            </a>
          </li>
          <li class="nav-item">
            <a class="px-3 py-2 flex items-center text-xs uppercase font-bold leading-snug text-white hover:opacity-75" href="#pablo">
              <span class="ml-2">Tweet</span>
            </a>
          </li>
          <li class="nav-item">
            <a class="px-3 py-2 flex items-center text-xs uppercase font-bold leading-snug text-white hover:opacity-75" href="#pablo">
              <span class="ml-2">Pin</span>
            </a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
  </header>
</template>

<script>
export default {
  name: 'GrayNavbar',
  data () {
    return {
      showMenu: false
    }
  },
  methods: {
    toggleNavbar () {
      this.showMenu = !this.showMenu
    }
  }
}
</script>
