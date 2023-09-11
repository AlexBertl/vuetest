<template>
  <div class="slider-outer-wrapper">
    <div class="slides" ref="sliderRef">
      <div class="slide" ref="slide">
        <Card></Card>
      </div>
      <div class="slide">
        <Card></Card>
      </div>
      <div class="slide">
        <Card></Card>
      </div>
    </div>
    <div class="controls">
      <button class="prev" @click="prevSlide">Back</button>
      <button class="next" @click="nextSlide">Next</button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Card from "./Card.vue";
const sliderRef = ref(HTMLDivElement);
const slide = ref(HTMLDivElement)

function prevSlide() {
  if (sliderRef.value instanceof HTMLDivElement && slide.value instanceof HTMLDivElement) {
    sliderRef.value.scrollLeft -= slide.value.offsetWidth + 30;
  }
};

function nextSlide(){
  if (sliderRef.value instanceof HTMLDivElement && slide.value instanceof HTMLDivElement) {
    sliderRef.value.scrollLeft += slide.value.offsetWidth + 30;
  }
};

</script>

<style scoped>
.slider-outer-wrapper {
  max-width: 1000px;
  overflow: hidden;
  position: relative;
  height: fit-content;
}

.slides {
  display: flex;
  overflow-x: scroll;
  scroll-behavior: smooth;
  -webkit-overflow-scrolling: touch;
  scroll-snap-type: x mandatory;
  gap: 20px;
}

.slide {
  width: 270px;
  scroll-snap-align: start;
}

button {
  background-color: gray;
  color: #fff;
  border: none;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  box-sizing: border-box;
  padding: 5px;
}

.prev{
  position: absolute;
  left: 3%;
  top: 50%;
  transform: translateY(-50%);
}

.next{
  position: absolute;
  right: 3%;
  top: 50%;
  transform: translateY(-50%);
}

.slides {
  scrollbar-width: none;
  -ms-overflow-style: none;
}

.slides::-webkit-scrollbar {
  display: none;
}
</style>
