<template lang="pug">
  div
    nav.navbar.header.has-shadow.is-primary(role="navigation" aria-label="main navigation")
      .navbar-brand
        a.navbar-item(href="/")
          | SuperNote
        .navbar-burger
          span
          span
          span

    section.main-content.columns
      aside.column.is-2.section
        p.menu-label.is-hidden-touch
        ul.menu-list
          li(v-for="(route, key) of routes" :key="key")
            nuxt-link(:to="route.to" exact-active-class="is-active")
              b-icon(:icon="route.icon")
                | {{ route.title }}
      .container.column.is-10
        nuxt
</template>

<script>
export default {
  data () {
    return {
      routes: [
        {
          title: 'Home',
          icon: 'home',
          to: { name: 'index' }
        },
        {
          title: 'Inspire',
          icon: 'lightbulb',
          to: { name: 'inspire' }
        }
      ]
    }
  }
}
</script>
