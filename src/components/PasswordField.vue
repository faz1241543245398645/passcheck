<template>
    <div>
      <p>Your password strength is: {{ difficulty }}</p>
      <input v-model="password" @input="checkPassword" type="password" placeholder="Enter your password">
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        password: '',
        difficulty: 'Weak'
      };
    },
    methods: {
      checkPassword() {
        const password = this.password;
        let strength = 0;
  
        // Check for length
        if (password.length >= 8) {
          strength++;
        }
  
        // Check for uppercase and lowercase letters
        if (/[a-z]/.test(password) && /[A-Z]/.test(password)) {
          strength++;
        }
  
        // Check for numbers
        if (/\d/.test(password)) {
          strength++;
        }
  
        // Check for special characters
        if (/[!@#$%^&*(),.?":{}|<>]/.test(password)) {
          strength++;
        }
  
        // Update the difficulty based on strength level
        if (strength <= 1) {
          this.difficulty = 'Weak';
        } else if (strength === 2) {
          this.difficulty = 'Moderate';
        } else if (strength === 3) {
          this.difficulty = 'Strong';
        } else {
          this.difficulty = 'Very Strong';
        }
      }
    }
  };
  </script>
  
  <style>
  /* Your CSS styles can go here */
  </style>
  