<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Galeria</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-grid>
        <ion-row>
          <ion-col size="6" :key="photo" v-for="photo in photos">
            <ion-img :src="photo.webviewPath"></ion-img>
            <ion-button color="primary" @click="showActionSheet(photo)">
              <ion-icon :icon="list"></ion-icon>
            </ion-button>
          </ion-col>
        </ion-row>
      </ion-grid> 
      <div class="cameraicon">
        <ion-fab vertical="bottom" horizontal="center">
          <ion-fab-button @click="takePhoto()">
            <ion-icon :icon="camera" class="iconCamera"></ion-icon>
          </ion-fab-button>
        </ion-fab>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { camera, trash, close, list } from "ionicons/icons";
import {
  actionSheetController,
  IonPage,
  IonHeader,
  IonFab,
  IonFabButton,
  IonIcon,
  IonToolbar,
  IonTitle,
  IonContent,
  IonImg,
  IonGrid,
  IonRow,
  IonCol,
} from "@ionic/vue";
import { usePhotoGallery, UserPhoto } from "../composables/usePhotoGallery";
import { defineComponent } from "vue";


export default defineComponent ({
  name: 'Galeria',
  components: { 
    IonHeader,
    IonFab,
    IonIcon,
    IonFabButton,
    IonToolbar,
    IonTitle,
    IonContent,
    IonPage,
    IonGrid,
    IonRow,
    IonCol,
    IonImg,
   },
   setup() {
    const { photos, takePhoto, deletePhoto } = usePhotoGallery();
    const showActionSheet = async (photo: UserPhoto) => {
      const actionSheet = await actionSheetController.create({
        header: "Opções",
        buttons: [
          {
            text: "Deletar",
            role: "destructive",
            icon: trash,
            handler: () => {
              deletePhoto(photo);
            },
          },
          {
            text: "Cancelar",
            icon: close,
            role: "cancel",
            handler: () => {
              // Nothing to do, action sheet is automatically closed
            },
          },
        ],
      });
      await actionSheet.present();
    };
    return {
      photos,
      takePhoto,
      showActionSheet,
      camera,
      trash,
      close,
      list
    };
  },
})
</script>
<style scoped>
#container {
  text-align: center;

  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;

  color: #8c8c8c;

  margin: 0;
}

#container a {
  
  text-decoration: none;
}

ion-fab {
  vertical-align: bottom;
  position:fixed;

}

ion-grid {
        font-family: Avenir, Helvetica, Arial, sans-serif;
    background: #FFF !important;
    color: #eeeeee;
    height: 100vh;
}


</style>