<template>
  <div>
    <Menu title="Reveal" side="start" type="reveal" menu-id="reveal" content-id="menu-page" />
    <Menu title="Left" side="start" menu-id="first" content-id="menu-page" />
    <Menu
      title="Custom"
      side="start"
      menu-id="custom"
      class="my-custom-menu"
      color="tertiary"
      content-id="menu-page"
    />
    <Menu title="Push" side="end" type="push" content-id="menu-page" />

    <IonVuePage :title="'Menu'" id="menu-page">
      <ion-button @click="openLeftMenu">Open left menu</ion-button>
      <br />
      <ion-button @click="openCustomMenu">Open custom menu</ion-button>
      <br />
      <ion-button @click="openRevealMenu">Open reveal menu</ion-button>
      <br />
      <ion-button @click="openPushMenu">Open push menu</ion-button>
    </IonVuePage>
  </div>
</template>

<script>
import { menuController } from '@ionic/core'
export default {
  components: {
    Menu: () => import('@/components/menu/index.vue'),
  },
  mounted() {
    this.$on('close', data => {
      menuController.close(data.menuId)
    })
  },
  methods: {
    openLeftMenu() {
      menuController.enable(true, 'first')
      menuController.open('first')
    },
    openCustomMenu() {
      menuController.enable(true, 'custom')
      menuController.open('custom')
    },
    openRevealMenu() {
      menuController.enable(true, 'reveal')
      menuController.open('reveal')
    },
    openPushMenu() {
      menuController.open('end')
    },
  },
}
</script>

<style>
.my-custom-menu {
  --width: 500px;
}
</style>
