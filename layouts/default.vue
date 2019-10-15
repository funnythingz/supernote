<template lang="pug">
section
  nav.navbar.header.has-shadow.is-primary(role="navigation" aria-label="main navigation")
    .navbar-brand
      a.navbar-item(href="/")
        | SuperNote
    b-navbar-item(v-for="(route, key) of routes" :key="key" :href="route.to" :class="active(route.to)")
      b-icon(:icon="route.icon")
        | {{ route.title }}
  .container
    nuxt
</template>

<script>
export default {
  data () {
    return {
      currentRoute: this.$router.currentRoute.path,
      routes: [
        {
          title: 'Home',
          icon: 'home',
          to: '/'
        },
        {
          title: 'About',
          icon: 'information-outline',
          to: '/about'
        }
      ]
    }
  },

  methods: {
    active(name) {
      return (this.currentRoute === name) ? 'is-active' : ''
    }
  }
}
</script>
