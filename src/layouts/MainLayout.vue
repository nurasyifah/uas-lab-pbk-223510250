<template>
  <q-layout view="hHh lpR fFf">
    <q-header class="bg-gradient-pink-blue" elevated>
      <q-toolbar>
        <q-toolbar-title class="text-black custom-title">UAS-LAB-PBK-NUR ASYIFAH-223510250</q-toolbar-title>
        <q-btn dense flat round icon="menu" @click="toggleRightDrawer" class="text-black" />
      </q-toolbar>
    </q-header>

    <q-drawer v-model="rightDrawerOpen" side="right" bordered class="custom-drawer">
      <!-- drawer content -->
      <q-list bordered padding>
        <q-item clickable v-ripple @click="goToTask(1)" class="custom-drawer-item">tugas 1</q-item>
        <q-item clickable v-ripple @click="goToTask(2)" class="custom-drawer-item">tugas 2</q-item>
        <q-item clickable v-ripple @click="goToTask(3)" class="custom-drawer-item">tugas 3</q-item>
        <q-item clickable v-ripple @click="goToTask(4)" class="custom-drawer-item">tugas 4</q-item>
        <q-item clickable v-ripple @click="goToTask(5)" class="custom-drawer-item">tugas 5</q-item>
        <q-item clickable v-ripple @click="goToTask(6)" class="custom-drawer-item">tugas 6</q-item>
        <q-item clickable v-ripple @click="goToTask(7)" class="custom-drawer-item">tugas 7</q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <footer class="bg-gradient-pink-blue text-black">
      <p>Nur Asyifah</p>
      <p>Informatics Engineering</p>
      <div class="social">
        <a href="https://www.instagram.com/nur__asyifah/"><i class='bx bxl-instagram-alt'></i></a>
        <a href="http://www.youtube.com/@nur__asyifah"><i class='bx bxl-youtube'></i></a>
        <a href="https://x.com/nurasyifah967"><i class='bx bxl-twitter'></i></a>
      </div>
      <p class="end">&copy; Copy right by ChocoCip</p>
    </footer>
  </q-layout>
</template>


<script>
import { ref } from 'vue'

export default {
  setup() {
    const rightDrawerOpen = ref(false)

    const goToTask = (taskNumber) => {
      const taskLinks = {
        1: 'https://cipa-project-cv.netlify.app/',
        2: 'https://cipa-project-tugas2.netlify.app/',
        3: 'https://cipa-project-tugas3.netlify.app/',
        4: 'https://cipa-project-tugas4.netlify.app/',
        5: 'https://cipa-project-tugas5.netlify.app/',
        6: 'https://cipa-project-tugas6.netlify.app/',
        7: 'https://cipa-project-tugas7.netlify.app/'
      }
      window.location.href = taskLinks[taskNumber]
    }

    const toggleRightDrawer = () => {
      rightDrawerOpen.value = !rightDrawerOpen.value
    }

    return {
      rightDrawerOpen,
      toggleRightDrawer,
      goToTask
    }
  }
}
</script>

<style>


.bg-pink {
  background-color: #FDB0C0 !important;
}

.text-white {
  color: #ffffff !important;
}

.text-black {
  color: #000000 !important;
}

.bg-gradient-pink-blue {
  background: linear-gradient(to right, #FDB0C0, #87CEEB) !important;
}

footer {
  position: relative;
  width: 100%;
  height: 230px;
  background: linear-gradient(to right, #FDB0C0, #87CEEB) !important;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding-top: 30px;
}

footer p:nth-child(1) {
  font-size: 30px;
  color: #000000 !important;
  margin-bottom: 5px;
  font-weight: bold;
}

footer p:nth-child(2) {
  color: #000000 !important;
  font-size: 17px;
  width: 500px;
  text-align: center;
  line-height: 26px;
}

.social {
  display: flex;
}

.social a {
  width: 45px;
  height: 45px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  background: #87CEEB;
  margin: 22px 10px;
  color: white !important;
  text-decoration: none;
  font-size: 20px;
}

.social a:hover {
  transition: 0.4s;
  transform: scale(1.3);
}

.end {
  position: absolute;
  color: white !important;
  margin-bottom: -6px;
  font-size: 14px;
}

.q-page-container {
  background-color: #87CEEB !important;
  min-height: calc(100vh - 230px);
  padding: 16px;
}

.custom-title {
  font-family: 'Lucida Calligraphy', sans-serif;
  font-size: 18px;
  color: #000000 !important;
}

p {
  font-family: 'Lucida Calligraphy', sans-serif;
  font-size: 18px;
  color: #000000 !important;
}

.custom-drawer {
  background: linear-gradient(to right, #FDB0C0, #87CEEB) !important;
  font-family: 'Century', sans-serif;
  font-size: 18px;
  color: #333333;
}

.custom-drawer-item {
  background: linear-gradient(to right, #FDB0C0, #87CEEB) !important;
  font-family: 'Century', sans-serif;
  font-size: 18px;
  color: #333333;
}

.bg-skyblue {
  background-color: #87CEEB !important;
}
</style>