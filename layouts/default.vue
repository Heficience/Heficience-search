<template>
  <div>
    <nav
      class="navbar header has-shadow is-dark"
      role="navigation"
      aria-label="main navigation"
    >
      <div class="navbar-brand">
        <a
          class="navbar-item"
          href="/"
        >
          <LogoLarge />
        </a>

      </div>
    </nav>

    <section class="main-content columns">
      <aside class="column is-2 section">
        <p class="menu-label is-hidden-touch">
          Heficience Search
        </p>
        <ul class="menu-list">
          <li
            v-for="(item, key) of items"
            :key="key"
          >
            <NuxtLink
              :to="item.to"
              exact-active-class="is-active"
            >
              <b-icon :icon="item.icon" /> {{ item.title }}
            </NuxtLink>
          </li>
        </ul>
      </aside>

      <div class="container column is-10">
        <Nuxt />
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data () {
    return {
      items: [
        {
          title: 'Recherche',
          icon: 'book',
          to: { name: 'index' }
        },
        {
          title: 'Heficience',
          icon: 'lightbulb',
          to: { name: 'projet' }
        }
      ]
    }
  }
}
</script>
<style>
html{
  background-color: #d7d8da
}
body{
  font-family: 'Roboto', sans-serif;
  font-size: 16px;
  color: #333;
}
</style>