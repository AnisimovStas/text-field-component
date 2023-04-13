<template>
  <div class="card">
    <div class="card-header">
      <div class="card-header--title">Текст перед полем</div>
      <div class="card-body">
        <div class="card-body--loader"></div>
        <div class="card-body--title">Название поля</div>
        <input class="card-body--input" type="textarea" v-model="inputText"/>
      </div>
      <div class="card-footer">
        <div class="card-footer--error" v-if="inputText.length>10"> Ошибка</div>
        <div class="card-footer--symbolsLength">
          {{ inputText.length }}/10
        </div>
        <div class="card-footer-clearInput" @click="inputText=''"> Очистить</div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const inputText = ref("");
</script>
