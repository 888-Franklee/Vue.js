<script setup>
import { reactive } from 'vue';

const state = reactive({
  cart: [
    { name: 'goodsA', price: 100, quantity: 1 },
    { name: 'goodsB', price: 200, quantity: 2 }
  ]
});

const increaseQuantity = (item) => {
  item.quantity++;
};

const decreaseQuantity = (item) => {
  if (item.quantity > 1) item.quantity--;
};

const totalPrice = () => {
  return state.cart.reduce((sum, item) => sum + item.price * item.quantity, 0);
};
</script>

<template>
  <div class="cart-container">
    <h3 class="cart-title">Shopping Cart</h3>
    <ul class="cart-list">
      <li v-for="item in state.cart" :key="item.name" class="cart-item">
        <span class="item-name">{{ item.name }}</span>
        <span class="item-price">￥{{ item.price }}</span>
        <span class="item-quantity">× {{ item.quantity }}</span>
        <button class="btn btn-increase" @click="increaseQuantity(item)">+</button>
        <button class="btn btn-decrease" @click="decreaseQuantity(item)">-</button>
      </li>
    </ul>
    <p class="cart-total">Total Price: ￥{{ totalPrice() }}</p>
  </div>
</template>

<style scoped>
.cart-container {
  font-family: Arial, sans-serif;
  margin: 20px auto;
  max-width: 400px;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  background-color: #f9f9f9;
}

.cart-title {
  font-size: 24px;
  margin-bottom: 20px;
  text-align: center;
  color: #333;
}

.cart-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.cart-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 0;
  border-bottom: 1px solid #eee;
}

.item-name {
  flex: 1;
  font-size: 16px;
  color: #555;
}

.item-price {
  margin: 0 10px;
  font-weight: bold;
  color: #333;
}

.item-quantity {
  margin-right: 10px;
  color: #666;
}

.btn {
  padding: 5px 10px;
  border: none;
  border-radius: 5px;
  font-size: 14px;
  cursor: pointer;
  transition: background-color 0.3s, transform 0.2s;
}

.btn-increase {
  background-color: #4caf50;
  color: white;
}

.btn-increase:hover {
  background-color: #45a049;
}

.btn-decrease {
  background-color: #f44336;
  color: white;
}

.btn-decrease:hover {
  background-color: #e53935;
}

.btn:active {
  transform: scale(0.95);
}

.cart-total {
  margin-top: 20px;
  text-align: center;
  font-size: 20px;
  font-weight: bold;
  color: #333;
}
</style>
