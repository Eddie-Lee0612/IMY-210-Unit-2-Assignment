<!-- Eddie Lee, u24843882 -->
<template>
    <div>
      <h1>My Projects</h1>
      <ul>
        <li>Project 1: VIO comic drawing</li>
        <li>Project 2: IMY211 blender room design</li>
        <li>Project 3: IMY210 Jamstack project</li>
      </ul>
      <div>
        <h2>Random Cat Fact</h2>
        <button @click="fetchCatFact">Get New Fact</button>
        <div v-if="catFact">
          <p>{{ catFact }}</p>
        </div>
        <div v-else-if="error">
          <p>Error fetching cat fact: {{ error }}</p>
        </div>
        <div v-else>
          <p>Click the button to get a cat fact!</p>
        </div>
      </div>
    </div>
  </template>

  <script>
  export default {
    head() {
      return {
        title: 'Eddie Lee - Projects'
      }
    },
    setup() {
      const catFact = ref(null)
      const error = ref(null)

      const fetchCatFact = async () => {
        const { data, error: fetchError } = await useFetch(
          'https://meowfacts.herokuapp.com/'
        )
        if (data.value && data.value.data && data.value.data[0]) {
          catFact.value = data.value.data[0]
          error.value = null
        } else {
          catFact.value = null
          error.value = fetchError.value ? fetchError.value.message : 'No data available'
        }
      }

      return { catFact, error, fetchCatFact }
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
  max-width: 600px;
  width: 100%;
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  text-align: center;
}

h1 {
  font-size: 2.5rem;
  color: #1f2937;
  margin-bottom: 1.5rem;
}

h2 {
  font-size: 1.5rem;
  color: #374151;
  margin-bottom: 1rem;
}

p {
  font-size: 1.1rem;
  color: #4b5563;
  margin-bottom: 1rem;
}

.project-list {
  list-style: disc inside;
  margin-bottom: 2rem;
  text-align: left;
}

.project-list li {
  font-size: 1.1rem;
  color: #4b5563;
  margin-bottom: 0.5rem;
}

button {
  display: block;
  width: 150px;
  margin: 0 auto 1rem;
  padding: 0.75rem;
  background-color: #3b82f6;
  color: white;
  border: none;
  border-radius: 5px;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #2563eb; /* Darker blue on hover */
}

.cat-fact {
  background-color: #f9fafb; /* Very light gray */
  padding: 1rem;
  border-radius: 5px;
  margin-top: 1rem;
}

.error {
  margin-top: 1rem;
}

.error p {
  color: #ef4444;
}
</style>