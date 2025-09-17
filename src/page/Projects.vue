<template>
  <div class="d-flex flex-column align-center justify-center w-100">

    <!-- header -->
    <div class="text-h5 text-grey-darken-3 font-weight-bold mt-2">Latest Project</div>

    <!-- body -->
    <div class="page-content mt-2">

      <v-card color="teal-darken-1" variant="outlined" class="mx-auto">
        <v-card-item>
          <div class="text-center">
            <img src="../../static/images/samsung.jpg" alt="samsung" height="180">
          </div>
        </v-card-item>
      </v-card>

      <div class="font-weight-bold mt-4 text-teal-darken-1 align-center">
        <v-icon color="teal-darken-1" icon="mdi-calendar" size="small"></v-icon>
        06/2024 - 02/2025
      </div>
      <div class="text-h6 font-weight-bold">
        SamsungSDS Management System
      </div>
      <div class="text-caption">
        Develop features for device network management
        software. Mainly used for internal company software.
      </div>
      <div class="text-body-2">
        Frontend: Vuejs, Vuex, internal component library.
      </div>

    </div>

    <!-- footer -->
    <div class="d-flex align-center mt-2 ga-2 justify-space-between w-100">
      <v-btn class="ma-2" size="x-small" color="teal-darken-1" variant="outlined"
        @click.prevent="props.togglePage(props.indexPage)" :disabled="!!props.item?.animating" icon="mdi-arrow-left">
      </v-btn>
      <span>4</span>
      <!-- <v-btn class="ma-2" size="x-small" color="teal-darken-1" variant="outlined"
        @click.prevent="props.togglePage(props.indexPage)" :disabled="!!props.item?.animating" icon="mdi-arrow-right">
      </v-btn> -->
      <span>&nbsp;</span>
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
