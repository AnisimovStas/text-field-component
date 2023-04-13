<template>
  <div class="card">
    <div class="card-header">
      <div class="card-header--title">Текст перед полем</div>
    </div>
    <div class="card-body">
      <div class="card-body-inner">
        <div
          :class="{
            'card-body--title smaller': !noText,
            'card-body--title__disabled bigger': noText,
          }"
        >
          Название поля
        </div>
        <textarea
          @focus="noText = false"
          @focusout="
            if (inputText == '') {
              noText = true;
            }
          "
          class="card-body--input"
          type="textarea"
          v-model="inputText"
        />
        <div class="card-body--loader" v-show="loader">
          <svg
            version="1.1"
            id="L3"
            xmlns="http://www.w3.org/2000/svg"
            xmlns:xlink="http://www.w3.org/1999/xlink"
            x="0px"
            y="0px"
            viewBox="0 0 100 100"
            enable-background="new 0 0 0 0"
            xml:space="preserve"
          >
            <circle
              fill="none"
              stroke="#00B6D0"
              stroke-width="4"
              cx="50"
              cy="50"
              r="44"
              style="opacity: 0.5"
            />
            <circle
              fill="#fff"
              stroke="#00B6D0"
              stroke-width="3"
              cx="8"
              cy="54"
              r="6"
            >
              <animateTransform
                attributeName="transform"
                dur="2s"
                type="rotate"
                from="0 50 48"
                to="360 50 52"
                repeatCount="indefinite"
              />
            </circle>
          </svg>
        </div>
      </div>
    </div>
    <div class="card-footer">
      <div class="card-footer--error" v-if="inputText.length > 1000">
        Ошибка
      </div>
      <div class="card-footer--symbolsLength">{{ inputText.length }}/1000</div>
      <div class="card-footer-clearInput" @click="inputText = ''">Очистить</div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref, watch } from "vue";

const inputText = ref("");
const noText = ref("true");
const loader = ref("true");
onMounted(() => {
  loader.value = false;
});
watch(inputText, () => {
  if (inputText.value == "") {
    noText.value = true;
  } else {
    noText.value = false;
  }
});
</script>
