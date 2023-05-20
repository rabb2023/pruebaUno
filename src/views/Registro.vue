<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Registro de estudiantes</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab 1</ion-title>
        </ion-toolbar>
      </ion-header>
    

      <ExploreContainer name="Tab 1 page" />

      <ion-button @click.prevent="registro">registrar</ion-button>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent,IonButton } from '@ionic/vue';
import ExploreContainer from '@/components/ExploreContainer.vue';
import { getAuth, signInWithEmailAndPassword, createUserWithEmailAndPassword } from "firebase/auth";

const auth = getAuth();
/*
const login = async () => {
  await signInWithEmailAndPassword(auth, email.value, password.value)
    .then((userCredential) => {
      // Signed in
      const user = userCredential.user;
      console.log("login completo ", user)
      // ...
    })
    .catch((error) => {
      const errorCode = error.code;
      const errorMessage = error.message;

      console.log("error al hacer login", errorCode, errorMessage, error)
    });

}

*/
const registro = async () => {

  await createUserWithEmailAndPassword(auth, "rab@ssa.gob.mx", "123xxx-")
    .then((userCredential) => {
      // Signed in
      const user = userCredential.user;
      console.log("registo completo", user)
      // ...
    })
    .catch((error) => {
      const errorCode = error.code;
      const errorMessage = error.message;
      console.log("error al registrar", errorCode, "mensaje", errorMessage, "todo el error", error)
      // ..
    });
}

</script>
