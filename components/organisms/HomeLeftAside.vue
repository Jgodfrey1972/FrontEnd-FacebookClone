<template>
  <Aside :class="{ 'is-menu-active': isMenuActive }">
    <div class="content">
      <div class="profile-avatar">
        <img src="@/assets/img/profile-pic.png" alt="" />

        <p>Cataline S. Rocha</p>
        <BaseButton
          btn-link
          text="Ver Perfil"
          link="/123"
          @click.native="toggleMenuActive"
        />
      </div>
      <div class="aside-links">
        <AsideLink
          :image-u-r-l="'messenger-link.svg'"
          :text="'Messenger'"
          @click.native="toggleMenuActive"
        />
        <AsideLink
          :image-u-r-l="'followers-link.svg'"
          :text="'Seguidores'"
          @click.native="toggleMenuActive"
        />
        <AsideLink
          :image-u-r-l="'groups-link.svg'"
          :text="'Grupos'"
          @click.native="toggleMenuActive"
        />
        <AsideLink
          :image-u-r-l="'pages-link.svg'"
          :text="'Páginas'"
          @click.native="toggleMenuActive"
        />
        <AsideLink
          :image-u-r-l="'events-link.svg'"
          :text="'Eventos'"
          @click.native="toggleMenuActive"
        />
        <AsideLink
          :image-u-r-l="'foundations-link.svg'"
          :text="'Fundações'"
          @click.native="toggleMenuActive"
        />
        <AsideLink
          :image-u-r-l="'memories-link.svg'"
          :text="'Memórias'"
          @click.native="toggleMenuActive"
        />
        <AsideLink
          :image-u-r-l="'videos-link.svg'"
          :text="'Vídeos'"
          @click.native="toggleMenuActive"
        />
      </div>
    </div>

    <button class="btn-close" @click="toggleMenuActive">
      <fa :icon="['fas', 'times']" class="close" />
    </button>

    <li class="settings-link" @click="toggleMenuActive">
      <NuxtLink to="/account">
        <fa :icon="['fas', 'cog']" class="cog" />
      </NuxtLink>
    </li>
  </Aside>
</template>

<script lang="ts">
import Vue from 'vue'
import { mobile } from '@/store'

export default Vue.extend({
  computed: {
    isMenuActive() {
      return mobile.$isMenuActive
    }
  },
  methods: {
    toggleMenuActive() {
      const body = document.querySelector('body') as HTMLElement
      const html = document.querySelector('html') as HTMLElement
      const width = document.body.clientWidth

      if (width > 1200) return

      body.classList.toggle('overflow-hidden')
      html.classList.toggle('overflow-hidden')
      mobile.toggle()
    }
  }
})
</script>

<style lang="scss" scoped>
.aside {
  background: color(dark, shade1);
  @include screen('large', 'medium', 'small') {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 99999;
    height: 100vh;
    width: 100%;
    transform: translate3d(-100%, 0, 0);
    transition: all 300ms ease;
  }
  @include screen('infinity') {
    display: none;
  }
  &.is-menu-active {
    transform: translate3d(0, 0, 0);
    ::v-deep .wrapper {
      position: relative;
      top: 0;
      overflow: auto;
      max-height: unset;
      height: inherit;
      overflow-x: hidden;
    }
  }
}

.content {
  padding: 3rem 1.4rem;
  display: grid;
  grid-gap: 2rem;
  .profile-avatar {
    display: grid;
    grid-gap: 1rem;
    justify-items: center;
    img {
      width: 6.25rem;
      border-radius: 50%;
    }
    p {
      font-weight: bold;
      color: color(white);
      font-size: 1.25rem;
    }
  }
  .aside-links {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-gap: 1.2rem;
  }
}
.btn-close {
  position: absolute;
  top: 21px;
  right: 20px;
  background: none;
  outline: none;
  cursor: pointer;
  display: none;

  @include screen('large') {
    display: flex;
  }
  .close {
    font-size: 26px;
    color: white;
  }
}
.settings-link {
  position: absolute;
  top: 21px;
  left: 20px;
  background: none;
  outline: none;
  cursor: pointer;
  display: none;

  @include screen('large') {
    display: flex;
  }

  img {
    width: 1.125rem;
  }

  a {
    font-size: 22px;
    color: color(white);
    position: relative;
  }
}
</style>
