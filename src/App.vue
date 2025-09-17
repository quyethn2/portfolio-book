<script setup>
import { onMounted, ref } from 'vue';
import HomeCover from './page/HomeCover.vue';
import Experience from './page/Experience.vue';
import Skill from './page/Skill.vue';
import Education from './page/Education.vue';
import Projects from './page/Projects.vue';
import Contact from './page/Contact.vue';
import Certificates from './page/Certificates.vue';

const pages = ref([
  { zIndex: 1, animating: true, componentFront: Experience, componentBack: Skill, turned: true },
  { zIndex: 2, animating: true, componentFront: Education, componentBack: Projects, turned: true },
  { zIndex: 3, animating: true, componentFront: Certificates, componentBack: Contact, turned: true },
  // Add more pages as needed
]);

const pageNumber = ref(0)
const totalPages = ref(pages.value.length)
const coverTurned = ref(false)
const coverZIndex = ref(100)

function togglePage(index) {
  if (pages.value[index].animating) return; // Chặn nếu đang lật
  pages.value[index].animating = true;
  if (pages.value[index].turned) {
    // back page
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

  } else {
    // next page
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
        <div class="book-page page-left">
          <HomeCover></HomeCover>
        </div>

        <!-- page right 1-2 turn -->
        <div v-for="(item, index) in pages" :key="index" class="book-page page-right" :class="{ turn: item.turned }"
          :style="{ zIndex: item.zIndex }">
          <div class="page-front">
            <component :is="item.componentFront" :togglePage="togglePage" :item="item" :index-page="index" />
          </div>
          <div class="page-back">
            <component :is="item.componentBack" :togglePage="togglePage" :item="item" :index-page="index"
              :backToHome="backProfile" />
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
  padding: 20px;
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
    }

    .page-front {
      transform: rotateY(0deg) translateZ(1px);
    }
  }
}
</style>
