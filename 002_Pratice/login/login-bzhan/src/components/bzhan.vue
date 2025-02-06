<template>
    <div class="auth-container">
      <!-- 登录/注册切换 -->
      <div class="tabs">
        <button 
          :class="{ active: isLogin }"
          @click="isLogin = true"
        >登录</button>
        <button 
          :class="{ active: !isLogin }"
          @click="isLogin = false"
        >注册</button>
      </div>
  
      <!-- 登录表单 -->
      <form v-if="isLogin" @submit.prevent="handleLogin">
        <div class="form-group">
          <input
            type="tel"
            placeholder="手机号"
            v-model="loginForm.phone"
            required
          />
        </div>
        
        <div class="form-group remember">
          <label>
            <input type="checkbox" v-model="loginForm.remember" />
            记住我
          </label>
          <a href="#" class="forgot-password">忘记密码？</a>
        </div>
  
        <button type="submit" class="submit-btn">登录</button>
  
        <div class="qrcode-login">
          <span>扫描二维码登录</span>
        </div>
  
        <div class="agreement">
          登录即代表你同意
          <a href="#">用户协议</a>和<a href="#">隐私政策</a>
        </div>
      </form>
  
      <!-- 注册表单 -->
      <form v-else @submit.prevent="handleRegister">
        <div class="form-group">
          <div class="region">中国大陆</div>
          <input
            type="tel"
            placeholder="填写常用手机号"
            v-model="registerForm.phone"
            required
          />
        </div>
  
        <div class="form-group">
          <input
            type="text"
            placeholder="手机验证码"
            v-model="registerForm.code"
          />
          <button 
            type="button" 
            class="get-code"
            :disabled="codeCountdown > 0"
            @click="getVerifyCode"
          >
            {{ codeCountdown ? `${codeCountdown}s` : '点击获取' }}
          </button>
        </div>
  
        <div class="form-group">
          <input
            type="text"
            placeholder="昵称"
            v-model="registerForm.nickname"
            required
          />
        </div>
  
        <div class="form-group">
          <input
            type="password"
            placeholder="密码（6-16位字符组成，区分大小写）"
            v-model="registerForm.password"
            required
          />
        </div>
  
        <div class="agreement-check">
          <label>
            <input 
              type="checkbox" 
              v-model="registerForm.agreed"
              required
            />
            我已同意
            <a href="#">《用户使用协议》</a>和<a href="#">《隐私政策》</a>
          </label>
        </div>
  
        <button type="submit" class="submit-btn">注册</button>
      </form>
    </div>
  </template>
  
  <script setup>
  import { ref, reactive } from 'vue';
  
  const isLogin = ref(true);
  
  // 登录表单数据
  const loginForm = reactive({
    phone: '',
    remember: false
  });
  
  // 注册表单数据
  const registerForm = reactive({
    phone: '',
    code: '',
    nickname: '',
    password: '',
    agreed: false
  });
  
  const codeCountdown = ref(0);
  
  // 获取验证码
  const getVerifyCode = () => {
    if (!registerForm.phone) {
      alert('请输入手机号');
      return;
    }
    
    codeCountdown.value = 60;
    const timer = setInterval(() => {
      codeCountdown.value--;
      if (codeCountdown.value <= 0) {
        clearInterval(timer);
      }
    }, 1000);
  };
  
  // 提交登录
  const handleLogin = () => {
    console.log('登录提交', loginForm);
    // 这里添加登录API调用
  };
  
  // 提交注册
  const handleRegister = () => {
    console.log('注册提交', registerForm);
    // 这里添加注册API调用
  };
  </script>
  
  <style scoped>
  .auth-container {
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
  }
  
  .tabs {
    display: flex;
    margin-bottom: 20px;
  }
  
  .tabs button {
    flex: 1;
    padding: 12px;
    border: none;
    background: #f0f0f0;
    cursor: pointer;
  }
  
  .tabs button.active {
    background: #fff;
    border-bottom: 2px solid #00a1d6;
  }
  
  .form-group {
    margin-bottom: 15px;
    position: relative;
  }
  
  input {
    width: 100%;
    padding: 12px;
    border: 1px solid #ddd;
    border-radius: 4px;
    box-sizing: border-box;
  }
  
  .remember {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .forgot-password {
    color: #00a1d6;
    text-decoration: none;
  }
  
  .submit-btn {
    width: 100%;
    padding: 12px;
    background: #00a1d6;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .qrcode-login {
    text-align: center;
    margin: 20px 0;
    color: #666;
  }
  
  .agreement {
    text-align: center;
    color: #666;
    font-size: 12px;
  }
  
  .agreement a {
    color: #00a1d6;
  }
  
  .get-code {
    position: absolute;
    right: 5px;
    top: 50%;
    transform: translateY(-50%);
    padding: 5px 10px;
    background: #f0f0f0;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .region {
    position: absolute;
    left: 12px;
    top: 50%;
    transform: translateY(-50%);
    color: #666;
    z-index: 1;
  }
  
  .agreement-check {
    margin: 15px 0;
    font-size: 12px;
  }
  </style>