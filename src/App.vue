<script setup>
import { onMounted, ref } from 'vue';

// const currentPage = ref(2);

const pages = ref([
  { front: 'Page 1 Front', back: 'Page 1 Back', turned: true, zIndex: 1, animating: true },
  { front: 'Page 2 Front', back: 'Page 2 Back', turned: true, zIndex: 2, animating: true },
  { front: 'Page 3 Front', back: 'Page 3 Back', turned: true, zIndex: 3, animating: true },
  { front: 'Page 4 Front', back: 'Page 4 Back', turned: true, zIndex: 4, animating: true },
  // Add more pages as needed
]);

const pageNumber = ref(0)
const totalPages = ref(pages.value.length)
const coverTurned = ref(false)
const coverZIndex = ref(100)

function togglePage(index) {
  if (pages.value[index].animating) return; // Chặn nếu đang lật
  pages.value[index].animating = true;
  debugger
  if (pages.value[index].turned) {
    // back
    // reverseIndex()
    // for (let i = 0; i < pages.value.length; i++) {
    //   reverseIndex()
    pages.value[index].turned = false;

    // Tìm zIndex lớn nhất hiện tại
    const maxZ = Math.max(...pages.value.map(p => p.zIndex));
    setTimeout(() => {
      if (pages.value[index].zIndex < maxZ) {
        pages.value[index].zIndex = 2 + maxZ;
      } else {
        pages.value[index].zIndex = 2 - index;
      }

      pages.value[index].animating = false;
    }, 500);
    // }

  } else {
    // next
    debugger
    pages.value[index].turned = true;
    // Tìm zIndex lớn nhất hiện tại
    const maxZ = Math.max(...pages.value.map(p => p.zIndex));
    setTimeout(() => {


      if (pages.value[index].zIndex < maxZ) {
        pages.value[index].zIndex = 2 + maxZ;
      } else {
        pages.value[index].zIndex = 2 + index;
      }
      pages.value[index].animating = false;
    }, 500);
  }
}

// create reverse index function


async function reverseIndex() {
  pageNumber.value--;
  if (pageNumber.value < 0) {
    pageNumber.value = totalPages.value - 1
  }
}

function backProfile() {
  for (let i = 0; i < pages.value.length; i++) {
    setTimeout(() => {
      reverseIndex()

      pages.value[pageNumber.value].turned = false

      setTimeout(() => {
        reverseIndex()
        pages.value[pageNumber.value].zIndex = 10 + i
        pages.value[pageNumber.value].animating = false
      }, 800)
    }, (i + 1) * 200 + 100)
  }
}


// open animation (cover right animation)
onMounted(() => {
  setTimeout(() => {
    coverTurned.value = true
  }, 2100)

  setTimeout(() => {
    coverZIndex.value = -1
  }, 2800)

  for (let i = 0; i < pages.value.length; i++) {
    setTimeout(() => {
      reverseIndex()
      pages.value[pageNumber.value].turned = false
      pages.value[pageNumber.value].animating = false
      setTimeout(() => {
        reverseIndex()
        pages.value[pageNumber.value].zIndex = 10 + i

      }, 800)
    }, (i + 1) * 200 + 2100)
  }
})
</script>

<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <div class="book-cover cover-left"></div>
      <div class="book-cover cover-right" :class="{ turn: coverTurned }" :style="{ zIndex: coverZIndex }"></div>

      <div class="book">
        <!-- page 0 -->
        <div class="book-page page-left">page 0 - num {{ pageNumber }}</div>

        <!-- page right 1-2 turn -->
        <div v-for="(item, index) in pages" :key="index" class="book-page page-right" :class="{ turn: item.turned }"
          :style="{ zIndex: item.zIndex }">
          <div class="page-front">{{ item.front }}
            <v-btn class="ma-2" color="orange-darken-2" @click.prevent="togglePage(index)" :disabled="item.animating">
              <v-icon icon="mdi-arrow-right" start></v-icon>
              Next
            </v-btn>
          </div>
          <div class="page-back">{{ item.back }}
            <v-btn class="ma-2" color="orange-darken-2" @click.prevent="togglePage(index)" :disabled="item.animating">
              <v-icon icon="mdi-arrow-left" start></v-icon>
              Back
            </v-btn>
            <v-btn class="ma-2" color="orange-darken-2" @click="backProfile" v-if="index == totalPages - 1">
              <v-icon icon="mdi-home" start></v-icon>
              Back Home
            </v-btn>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
$bg-color: #151f28;
$main-color: #26A69A;
$text-color: #333;
$second-text-color: #555;
$cover-color: #26A69A;
$pages-color: linear-gradient(90deg, #fff, #ddd);
$box-shadow: 0 0 12px rgba(0, 0, 0, 0.2);


.wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: $bg-color;
  overflow: hidden;
}

.wrapper-content {
  position: relative;
  width: 1024px;
  height: 90vh;
  padding: 32px;
  perspective: 250rem;
  animation: show-animate 2s forwards;
}

@keyframes show-animate {

  0%,
  30% {
    opacity: 0;
    transform: rotate(-20deg);
  }

  100% {
    opacity: 1;
    transform: rotate(0deg);
  }
}

// book-cover
.book-cover {
  position: absolute;
  top: 0;
  left: 0;
  width: 50%;
  height: 100%;
  background-color: $cover-color;
  box-shadow: $box-shadow;
  border-top-left-radius: 0.6rem;
  border-bottom-left-radius: 0.6rem;
  transform-origin: right;
}

.cover-left {
  z-index: -1;
}

.cover-right {
  transition: transform 1s cubic-bezier(.645, .045, .355, 1);
}

.cover-right.turn {
  transform: rotateY(180deg);
}

// book
.book {
  position: relative;
  width: 100%;
  height: 100%;
  display: flex;
  perspective: 250rem;

  .book-page {
    position: absolute;
    width: 50%;
    height: 100%;
    background: $pages-color;

    display: flex;
    padding: 2rem;
  }

  .page-left {
    box-shadow: -0.6rem 0.6rem 0.6rem rgba(0, 0, 0, 0.1);
  }

  .page-right.turn {
    transform: rotateY(-180deg);
  }

  .page-right {
    position: absolute;
    right: 0;
    transform-style: preserve-3d; // transform-style 3D;
    transform-origin: left;
    transition: transform 1s cubic-bezier(.645, .045, .355, 1);
    // transition-duration: 3s;
    box-shadow: 0 0 .6rem rgba(0, 0, 0, 0.1);

    .page-front,
    .page-back {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: $pages-color;
      padding: 1.5rem 2rem;
      transform: rotateY(180deg) translateZ(1px);
      // backface-visibility: hidden;
    }

    .page-front {
      transform: rotateY(0deg) translateZ(1px);
    }

    .page-back {}
  }
}
</style>
