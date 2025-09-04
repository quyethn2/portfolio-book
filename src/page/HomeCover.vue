<template>
  <div class="home-cover d-flex flex-column align-center justify-center w-100">
    <img src="../../static/images/ava1.jpg" alt="Avatar" class="avatar" />
    <div class="text-h5 text-grey-darken-3 font-weight-bold mt-2">Nguyen Van Quyet</div>
    <div class="text-h6 text-teal-darken-1 font-weight-bold mt-1">Frontend Developer</div>

    <div class="d-flex mt-2 ga-2">
      <v-btn variant="outlined" size="x-small" color="teal-darken-1" icon="mdi-facebook"
        @click="handleLink('https://facebook.com/quyethn2',)"></v-btn>
      <v-btn variant="outlined" size="x-small" color="teal-darken-1" icon="mdi-instagram"
        @click="handleLink('https://instagram.com/quyethn22',)"></v-btn>
      <v-btn variant="outlined" size="x-small" color="teal-darken-1" icon="mdi-linkedin"
        @click="handleLink('https://www.linkedin.com/in/quyet-nguyen-0838a2137',)"></v-btn>
      <v-btn variant="outlined" size="x-small" color="teal-darken-1" icon="mdi-github"
        @click="handleLink('https://github.com/quyethn2',)"></v-btn>

    </div>
    <div class="flex text-center text-body-2 mt-2">
      Frontend Developer (Vue/React/Angular) with more than 7 years of experience delivering high-performance web apps.
      Passionate about architecting scalable solutions with JavaScript, TypeScript, and modern CSS frameworks.
    </div>
    <div class="d-flex mt-2 ga-2">
      <v-btn class="ma-2" color="teal-darken-1">
        <v-icon icon="mdi-download" start></v-icon>
        Download CV
      </v-btn>
      <v-btn class="ma-2" color="teal-darken-1" variant="outlined" @click="contactMe">
        Contact Me!
      </v-btn>
    </div>

  </div>

</template>

<script setup>

function handleLink(url) {
  window.open(url, '_blank');
}

function contactMe() {
  // Handle contact me action
}

</script>

<style scoped lang="scss">
.avatar {
  width: 146px;
  height: 146px;
  border-radius: 50%;
  object-fit: cover;
  border: 2px solid #26A69A;
}
</style>
