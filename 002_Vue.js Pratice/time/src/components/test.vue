<template>
    <div class="date-time-picker">
      <div class="calendar">
        <div class="header">
          <button @click="prevMonth">&lt;</button>
          <span>{{ currentMonth }} {{ currentYear }}</span>
          <button @click="nextMonth">&gt;</button>
        </div>
        <div class="days">
          <div v-for="day in daysOfWeek" :key="day" class="day-header">{{ day }}</div>
          <div v-for="day in days" :key="day" class="day" :class="{ selected: day === selectedDay }" @click="selectDay(day)">
            {{ day }}
          </div>
        </div>
      </div>
      <div class="time-picker">
        <input type="time" v-model="selectedTime" />
      </div>
      <div class="actions">
        <button @click="cancel">取消</button>
        <button @click="schedule">安排发送时间</button>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue';
  
  const currentDate = ref(new Date());
  const selectedDay = ref(null);
  const selectedTime = ref('23:54');
  
  const daysOfWeek = ['一', '二', '三', '四', '五', '六', '日'];
  
  const currentYear = computed(() => currentDate.value.getFullYear());
  const currentMonth = computed(() => currentDate.value.toLocaleString('default', { month: 'long' }));
  
  const days = computed(() => {
    const year = currentDate.value.getFullYear();
    const month = currentDate.value.getMonth();
    const firstDay = new Date(year, month, 1);
    const lastDay = new Date(year, month + 1, 0);
    const daysInMonth = lastDay.getDate();
    const startingDay = firstDay.getDay() || 7;
  
    const daysArray = [];
    for (let i = 1; i < startingDay; i++) {
      daysArray.push('');
    }
    for (let i = 1; i <= daysInMonth; i++) {
      daysArray.push(i);
    }
    return daysArray;
  });
  
  const prevMonth = () => {
    currentDate.value = new Date(currentDate.value.getFullYear(), currentDate.value.getMonth() - 1, 1);
  };
  
  const nextMonth = () => {
    currentDate.value = new Date(currentDate.value.getFullYear(), currentDate.value.getMonth() + 1, 1);
  };
  
  const selectDay = (day) => {
    if (day) {
      selectedDay.value = day;
    }
  };
  
  const cancel = () => {
    selectedDay.value = null;
    selectedTime.value = '23:54';
  };
  
  const schedule = () => {
    if (selectedDay.value && selectedTime.value) {
      const scheduledDate = new Date(currentDate.value.getFullYear(), currentDate.value.getMonth(), selectedDay.value);
      const [hours, minutes] = selectedTime.value.split(':');
      scheduledDate.setHours(hours);
      scheduledDate.setMinutes(minutes);
      alert(`Scheduled for: ${scheduledDate}`);
    } else {
      alert('Please select a date and time.');
    }
  };
  </script>
  
  <style scoped>
  .date-time-picker {
    max-width: 300px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 8px;
  }
  
  .calendar .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 10px;
  }
  
  .calendar .days {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 5px;
  }
  
  .calendar .day-header, .calendar .day {
    text-align: center;
    padding: 10px;
  }
  
  .calendar .day {
    cursor: pointer;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  .calendar .day.selected {
    background-color: #4285f4;
    color: white;
  }
  
  .time-picker {
    margin-top: 20px;
    text-align: center;
  }
  
  .actions {
    margin-top: 20px;
    display: flex;
    justify-content: space-between;
  }
  
  button {
    padding: 10px 20px;
    background-color: #4285f4;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #357ab8;
  }
  </style>