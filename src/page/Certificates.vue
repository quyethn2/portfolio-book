<template>
  <div class="d-flex flex-column align-center justify-center w-100">

    <!-- header -->
    <div class="text-h5 text-grey-darken-3 font-weight-bold mt-2">Certificates</div>

    <!-- body -->
    <div class="page-content mt-2">

      <div class="d-flex ga-2">

        <v-card color="teal-darken-1" variant="outlined" class="mx-auto">
          <v-card-item>
            <div>
              <a href="https://www.educative.io/verify-certificate/r0w3pLt61RjnJLNrxTxoq7m6m8wlh6" target="_blank"
                title="View Certificate: Educative - Vue 3 Fundamentals">
                <img src="../../static/images/vue3.png" alt="vue3" height="100">
              </a>
            </div>
          </v-card-item>
        </v-card>

        <v-card color="teal-darken-1" variant="outlined" class="mx-auto">
          <v-card-item>
            <div>
              <a href="https://www.educative.io/verify-certificate/pg03nJFvOj6NGJqVZTvOrPB3BKwgs2" target="_blank"
                title="View Certificate: Educative - Performance Enhancements in Vue.js">
                <img src="../../static/images/vue.png" alt="vue" height="100">
              </a>
            </div>
          </v-card-item>
        </v-card>
      </div>

      <div class="d-flex ga-2 mt-4">
        <v-card color="teal-darken-1" variant="outlined" class="mx-auto">
          <v-card-item>
            <div>
              <a href="https://www.educative.io/verify-certificate/qjv3oKCJw1xy9n3qLHpK0ZWoWVPJTK" target="_blank"
                title="View Certificate: Educative - git for Developers">
                <img src="../../static/images/git.png" alt="git" height="100">
              </a>
            </div>
          </v-card-item>
        </v-card>

        <v-card color="teal-darken-1" variant="outlined" class="mx-auto">
          <v-card-item>
            <div>
              <a href="https://www.educative.io/verify-certificate/VQkXJZyOlNEhX1VWqVwE1JsMPKGgNg3ZDCr" target="_blank"
                title="View Certificate: Educative - testing">
                <img src="../../static/images/testing.png" alt="testing" height="100">
              </a>
            </div>
          </v-card-item>
        </v-card>
      </div>

    </div>

    <!-- footer -->
    <div class="d-flex align-center mt-2 ga-2 justify-space-between w-100">
      <span class="hidden">&nbsp;</span>
      <span>5</span>
      <v-btn class="ma-2" size="x-small" color="teal-darken-1" variant="outlined"
        @click.prevent="props.togglePage(props.indexPage)" :disabled="!!props.item?.animating" icon="mdi-arrow-right">
      </v-btn>
    </div>
  </div>

</template>

<script setup>
defineOptions({ name: 'ExperiencePage' });

const props = defineProps(['togglePage', 'item', 'indexPage']);

</script>

<style scoped lang="scss">
.page-content {
  height: 60vh;
  max-height: 60vh;
  overflow-y: auto;
  width: 100%;
}
</style>
