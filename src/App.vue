<template>
  <ion-app>
    <ion-router-outlet />
  </ion-app>
</template>

<script setup lang="ts">
import { IonApp, IonRouterOutlet } from '@ionic/vue';

import { initializeApp } from 'firebase/app';

import { getAuth, signOut } from "firebase/auth";
import firebaseConfig from "./firebaseConfig";

const firebase = initializeApp(firebaseConfig);
</script>
