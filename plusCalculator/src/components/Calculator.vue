<template>
    <div class="calculator">
      <div class="display">{{ displayValue }}</div>
      <div class="buttons">
        <div v-for="number in numbers" :key="number">
          <Button @click="handleNumberClick(number)">{{ number }}</Button>
        </div>
        <Button class="operate-btns" @click="handleOperatorClick('+')">+</Button>
        <Button class="operate-btns" @click="handleEqualClick">=</Button>
        <Button class="operate-btns" @click="handleClearClick">C</Button>
      </div>
    </div>
</template>

  <script setup>
  import { ref } from 'vue';

  const displayValue = ref('0');
  const operator = ref(null);
  const firstNumber = ref(null);
  
  const numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
  
  const handleNumberClick = (number) => {
    if (displayValue.value === '0') {
      displayValue.value = String(number);
    } else {
      displayValue.value += String(number);
    }
  };
  
  const handleOperatorClick = (op) => {
    operator.value = op;
    firstNumber.value = Number(displayValue.value);
    displayValue.value = '0';
  };
  
  const handleEqualClick = () => {
    if (operator.value === '+') {
      displayValue.value = String(firstNumber.value + Number(displayValue.value));
      operator.value = null;
      firstNumber.value = null;
    }
  };
  
  const handleClearClick = () => {
    displayValue.value = '0';
    operator.value = null;
    firstNumber.value = null;
  };
  </script>
  

  <style>
  .calculator {
    width: 320px;
    margin: 0 auto;
    border: 1px solid #ccc;
    border-radius: 10px;
    padding: 15px;
    background: #1a7388;
  }
  
  .display {
    font-size: 30px;
    text-align: right;
    padding: 8px;
    background-color: #f5f5f5;
    border-radius: 8px;
    margin-bottom: 15px;
  }
  
  .buttons {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    grid-gap: 15px;
  }
  
  button {
    font-size: 20px;
    padding: 14px 20px;
    border: none;
    border-radius: 8px;
    background-color: #f5f5f5;
    cursor: pointer;
    color: #333;
  }
  
  button:hover {
    background-color: #e0e0e0;
  }
  
  button:active {
    background-color: #ccc;
  }
  
  .operate-btns{
    background: #c6e8ef;
  }
  </style>