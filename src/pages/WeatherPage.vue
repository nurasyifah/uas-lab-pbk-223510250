<template>
  <q-page class="flex flex-center bluesky-container">
    <div class="weather-card-container">
      <q-card>
        <q-card-section>
          <h2 class="text-center">Weather</h2>
        </q-card-section>
        <q-card-section>
          <div class="q-row justify-end">
            <div class="q-col">
              <q-input v-model="city" label="Enter the city" />
            </div>
            <div class="q-col">
              <q-btn class="bg-pink" label="Search" @click="handleSearch" color="primary" style="text-transform: none;" />
            </div>
          </div>
        </q-card-section>
        <q-card-section v-if="status === 'loading'" class="text-center">
          <p>Loading data...</p>
        </q-card-section>
        <q-card-section v-else-if="weather" class="text-center">
          <h3>Location: {{ weather.name }}</h3>
          <p class="text-red-5">Temperature: {{ weather.main.temp }}°C</p>
          <p>Description: {{ weather.weather[0].description }}</p>
        </q-card-section>
        <q-card-section v-else-if="error" class="text-center">
          <p class="text-red-5">{{ error }}</p>
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script>
import axios from 'axios'

export default {
  name: 'WeatherPage',
  data() {
    return {
      city: '',
      weather: null,
      error: '',
      status: ''
    }
  },
  methods: {
    async fetchWeather() {
      const apiKey = '94bf6d59f86ae95e8071e78240546056'
      const url = `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=${apiKey}`
      try {
        const response = await axios.get(url)
        this.weather = response.data
        this.error = ''
        console.log(this.weather)
      } catch (error) {
        this.weather = null;  
        this.error = 'City not found'
        console.error(error)
      } finally {
        this.status = ''
      }
    },
    async handleSearch() {
      this.status = 'loading';
      this.weather = null; 
      this.error = '';     
      setTimeout(async () => {
        await this.fetchWeather();
      }, 2000);
    }
  }
}
</script>

<style scoped>
.bluesky-container {
  background-color: #87CEEB; 
  height: 100vh; 
  display: flex;
  justify-content: center;
  align-items: center;
}

.weather-card-container {
  background-color: #FDB0C0;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  max-width: 600px; 
  width: 90%; 
  margin: 20px; 
}

.text-red-5 {
  color: #f44336;
}

.bg-pink {
  background-color: #FDB0C0 !important;
  color: white !important;
}

h2 {
  font-family: 'Algerian', sans-serif;
  font-size: 50px; 
  margin-bottom: 20px;
  color: #333333; 
}

h3, p {
  font-family: 'Century', sans-serif;
  font-size: 20px; 
  margin-bottom: 20px;
  color: #333333; 
}
</style>
