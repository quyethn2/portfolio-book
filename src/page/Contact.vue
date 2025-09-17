<template>
  <div class="d-flex flex-column align-center justify-center w-100">

    <!-- header -->
    <div class="text-h5 text-grey-darken-3 font-weight-bold mt-2">Contact</div>

    <!-- body -->
    <div class="page-content mt-2">
      <v-card class="mx-auto" max-width="400">
        <v-img class="align-end text-white" height="200" src="../../static/images/ava2.jpg" cover>
          <v-card-title>Nguyen Van Quyet</v-card-title>
        </v-img>

        <v-card-subtitle class="pt-4">
          Frontend Developer
        </v-card-subtitle>

        <v-card-text>
          <div><v-icon icon="mdi-phone" size="14"></v-icon> (+84) 336 496 292</div>
          <div><v-icon icon="mdi-email" size="14"></v-icon> Quyethn2@gmail.com</div>
        </v-card-text>


      </v-card>
    </div>

    <!-- footer -->
    <div class="d-flex align-center mt-2 ga-2 justify-space-between w-100">
      <v-btn class="ma-2" size="x-small" color="teal-darken-1" variant="outlined"
        @click.prevent="props.togglePage(props.indexPage)" :disabled="!!props.item?.animating" icon="mdi-arrow-left">
      </v-btn>
      <span>6</span>
      <v-btn class="ma-2" size="x-small" color="teal-darken-1" variant="outlined" @click.prevent="props.backToHome()"
        :disabled="!!props.item?.animating" icon="mdi-home">
      </v-btn>
    </div>
  </div>

</template>

<script setup>
defineOptions({ name: 'ExperiencePage' });

const props = defineProps(['togglePage', 'item', 'indexPage', 'backToHome']);

</script>

<style scoped lang="scss">
.page-content {
  height: 60vh;
  max-height: 60vh;
  overflow-y: auto;
  width: 100%;
}
</style>
