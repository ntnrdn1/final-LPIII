<template>
  <ion-page>
    <ion-tabs>
      <ion-router-outlet></ion-router-outlet>
      <slot name="fixed">
      <ion-tab-bar vertical="bottom">
        <ion-tab-button tab="galeria" href="/tabs/galeria">
          <ion-icon :icon="images" />
          <ion-label>Galeria</ion-label>
        </ion-tab-button>
          
        <ion-tab-button tab="home" href="/tabs/home">
          <ion-icon :icon="home" />
          <ion-label>Home</ion-label>
        </ion-tab-button>
        
        <ion-tab-button tab="consulta" href="/tabs/consulta">
          <ion-icon :icon="location" />
          <ion-label>Consulta Local</ion-label>
        </ion-tab-button>
      </ion-tab-bar>
      </slot>
    </ion-tabs>
  </ion-page>
</template>

<script lang="ts">
import { IonTabBar, IonTabButton, IonTabs, IonLabel, IonIcon, IonPage, IonRouterOutlet } from '@ionic/vue';
import { ellipse, square, triangle } from 'ionicons/icons';
import { camera, home, images, location } from "ionicons/icons";

export default {
  name: 'Tabs',
  components: { IonLabel, IonTabs, IonTabBar, IonTabButton, IonIcon, IonPage, IonRouterOutlet },
  setup() {
    return {
      ellipse, 
      square, 
      triangle,
      camera,
      home, 
      images,
      location
    }
  }
}
</script>

<style scoped>
ion-tab-button {
      font-family: Avenir, Helvetica, Arial, sans-serif;
    color: #28b4d2;
    background-color: #364253;
    }

ion-tab-button:active {
    background-color: #eeeeee;
}
</style>