<!-- Eddie Lee, u24843882 -->
<template>
    <div>
      <h1>Eddie Lee</h1>
      <img src="/Eddie.jpg" alt="Eddie Lee Photo" />
      <p>I’m a student at the University of Pretoria studying multimedia</p>
      <div v-if="weather">
        <h2>Current Weather in {{ weather.name }}</h2>
        <p>Temperature: {{ weather.main.temp }}°C</p>
        <p>Condition: {{ weather.weather[0].description }}</p>
        <p>Humidity: {{ weather.main.humidity }}%</p>
      </div>
      <div v-else-if="error">
        <p>Error fetching weather: {{ error.message || error }}</p>
      </div>
      <div v-else>
        <p>Loading weather...</p>
      </div>
    </div>
  </template>

  <script>
  export default {
    head() {
      return {
        title: 'Eddie Lee - Portfolio'
      }
    },
    async setup() {
      const config = useRuntimeConfig()
      const apiKey = 'e45c27c0c65beb058179a8d79e1da42b'
      console.log('API Key in setup:', apiKey) // Debug

      // If no API key, return early to avoid failed fetch
      if (!apiKey || apiKey === 'default_key') {
        return {
          weather: null,
          error: 'API key is missing or invalid'
        }
      }

      const city = 'Pretoria'
      const { data: weather, error } = await useFetch(
        `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`,
        {
          server: true // Ensure fetch happens server-side
        }
      )

      return { weather, error }
    }
  }
  </script>

<style>
.main-container {
  min-height: 100vh;
  background-color: #f0f0f0; /* Light gray background */
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 5rem 1rem 1rem; /* Extra padding-top for nav bar */
  font-family: Arial, sans-serif;
}

.card {
  background-color: white;
  max-width: 400px;
  width: 100%;
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  text-align: center;
}

h1 {
  font-size: 2.5rem;
  color: #1f2937; /* Dark gray */
  margin-bottom: 1.5rem;
}

h2 {
  font-size: 1.5rem;
  color: #374151; /* Slightly lighter gray */
  margin-bottom: 1rem;
}

p {
  font-size: 1.1rem;
  color: #4b5563; /* Medium gray */
  margin-bottom: 1rem;
}

img {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  margin: 0 auto 1.5rem;
  border: 4px solid #3b82f6; /* Blue border */
  display: block;
}

.weather-info {
  margin-top: 1.5rem;
}

.error {
  margin-top: 1.5rem;
}

.error p {
  color: #ef4444; /* Red for errors */
}
</style>