<template>
  <div class="login-container">
    <div class="login-box">
      <h1 class="title">Welcome!</h1>
      <p class="subtitle">Get busy living, or get busy dying</p>
      <form @submit.prevent="handleLogin">
        <div class="form-group">
          <input
            type="text"
            id="username"
            v-model="username"
            placeholder="Enter your username"
            class="input-field"
            required
          />
        </div>
        <div class="form-group">
          <input
            type="password"
            id="password"
            v-model="password"
            placeholder="Enter your password"
            class="input-field"
            required
          />
        </div>
        <button type="submit" class="login-button">Login</button>
      </form>
      <div class="footer">
        <p class="forgot-password">Forgot your password? <a href="#">Reset it</a></p>
        <p class="signup">Don't have an account? <a href="#">Sign up</a></p>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'LoginPage',
  setup() {
    const username = ref('');
    const password = ref('');

    const handleLogin = () => {
      if (username.value && password.value) {
        alert(`Logging in with Username: ${username.value}`);
      } else {
        alert('Please fill in both fields.');
      }
    };

    return {
      username,
      password,
      handleLogin,
    };
  },
};
</script>

<style scoped>
body {
  margin: 0;
  font-family: 'Poppins', sans-serif;
  background: linear-gradient(135deg, #ff9a9e, #fad0c4);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.login-container {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}

.login-box {
  background: linear-gradient(145deg, #ffffff, #f8f9fa);
  border-radius: 20px;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
  padding: 40px;
  max-width: 450px;
  text-align: center;
}

.title {
  font-size: 32px;
  font-weight: 700;
  color: #333;
  margin-bottom: 15px;
}

.subtitle {
  font-size: 16px;
  color: #555;
  margin-bottom: 25px;
}

.form-group {
  margin-bottom: 25px;
}

.input-field {
  width: 100%;
  padding: 15px;
  border: none;
  border-radius: 10px;
  font-size: 16px;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

.input-field:focus {
  box-shadow: 0 0 10px rgba(0, 123, 255, 0.5);
  outline: none;
}

.login-button {
  width: 100%;
  padding: 15px;
  border: none;
  border-radius: 10px;
  background: linear-gradient(90deg, #36d1dc, #5b86e5);
  color: white;
  font-size: 18px;
  font-weight: bold;
  cursor: pointer;
  transition: transform 0.2s;
}

.login-button:hover {
  transform: scale(1.05);
}

.footer {
  margin-top: 20px;
}

.forgot-password,
.signup {
  font-size: 14px;
  color: #666;
}

.forgot-password a,
.signup a {
  color: #36d1dc;
  text-decoration: none;
  font-weight: 600;
}

.forgot-password a:hover,
.signup a:hover {
  text-decoration: underline;
}
</style>
