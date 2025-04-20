<!-- Eddie Lee, u24843882 -->
<template>
    <div>
      <h1>Contact Me</h1>
      <form name="contact" method="POST" data-netlify="true">
        <input type="hidden" name="form-name" value="contact" />
        <input type="text" name="name" placeholder="Name" required />
        <input type="email" name="email" placeholder="Email" required />
        <textarea name="message" placeholder="Message" required></textarea>
        <button type="submit">Send</button>
      </form>
    </div>
  </template>

  <script>
  export default {
    head() {
      return {
        title: 'Eddie Lee - Contact'
      }
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
      color: #1f2937;
      margin-bottom: 1.5rem;
    }

    .contact-form {
      display: flex;
      flex-direction: column;
      gap: 1rem;
    }

    .contact-form input,
    .contact-form textarea {
      width: 100%;
      padding: 0.75rem;
      border: 1px solid #d1d5db;
      border-radius: 5px;
      font-size: 1rem;
      outline: none;
      transition: border-color 0.3s ease;
    }

    .contact-form input:focus,
    .contact-form textarea:focus {
      border-color: #3b82f6; /* Blue border on focus */
    }

    .contact-form textarea {
      height: 120px;
      resize: none;
    }

    .contact-form button {
      width: 100%;
      padding: 0.75rem;
      background-color: #3b82f6;
      color: white;
      border: none;
      border-radius: 5px;
      font-size: 1rem;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }

    .contact-form button:hover {
      background-color: #2563eb;
    }
  </style>