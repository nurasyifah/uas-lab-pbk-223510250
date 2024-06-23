<template>
  <q-page class="flex flex-center page-container">
    <div class="card-container">
      <h1>ヽ(o´3`o)ﾉhallo welcome to weather widget by ChocoCip(^з^)-☆</h1>
      <q-btn label="Go To Weather" @click="goToWeather" class="go-btn" />
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'HomePage',
  methods: {
    goToWeather() {
      this.$router.push('/weather')
    }
  }
}
</script>

<style scoped>
.page-container {
  background-color: #87CEEB; 
  min-height: 100vh; 
  display: flex;
  align-items: center;
  justify-content: center;
}

.card-container {
  background-color: #FDB0C0; 
  padding: 40px; 
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  text-align: center;
  width: 90%; 
  max-width: 800px; 
}

h1 {
  font-family: 'Century', sans-serif;
  font-size: 20px; 
  margin-bottom: 20px;
  color: #333333; 
}

.go-btn {
  font-family: 'Century', sans-serif;
  background-color: #87CEEB !important; 
  color: #ffffff !important; 
  border-radius: 5px;
  --q-btn-padding: 10px 20px;
  text-transform: lowercase;
}

.go-btn:hover {
  background-color: #FDB0C0 !important; 
}
</style>
