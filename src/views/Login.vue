<template>
    <ion-page>
      <ion-header>
        <ion-toolbar>
          <ion-title>Login</ion-title>
        </ion-toolbar>
      </ion-header>
      <ion-content :fullscreen="true">
        <ion-header collapse="condense">
          <ion-toolbar>
            <ion-title size="large">Tab 4</ion-title>
          </ion-toolbar>
        </ion-header>
        <ExploreContainer name="Tab 4 page" />  
      
        <ion-input label="Solid input" label-placement="floating" fill="solid" placeholder="Enter text" v-model="usuario"></ion-input>

<br />

<ion-input label="Outline input" label-placement="floating" fill="outline" placeholder="Enter text" v-model="contra"></ion-input>

<ion-button @click.prevent="validar">Default</ion-button> 
        
      </ion-content>
    </ion-page>
  </template>

<script setup lang="ts">

import {ref} from "vue"
 let error = false;

import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent,IonButton,IonInput} from '@ionic/vue';
import ExploreContainer from '@/components/ExploreContainer.vue';
import router from '@/router';
import { getAuth, signInWithEmailAndPassword, createUserWithEmailAndPassword } from "firebase/auth";

const auth = getAuth();


const usuario = ref();
let contra = ref();




const validar = async () => {
  await signInWithEmailAndPassword(auth, "rab@ssa.gob.mx", "123xxx-")
    .then((userCredential) => {
      // Signed in
      const user = userCredential.user;
      console.log("login completo ", user)
      router.push("tab3");

      // ...
    })
    .catch((error) => {
      const errorCode = error.code;
      const errorMessage = error.message;
     
      console.log("error al hacer login", errorCode, errorMessage, error)
    });

}



function funcion1(){

  alert("dato us:" + usuario.value)
  router.push("tab3");

}

</script>