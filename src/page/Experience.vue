<template>
  <div class="d-flex flex-column align-center justify-center w-100">

    <!-- header -->
    <div class="text-h5 text-grey-darken-3 font-weight-bold mt-2">Experience</div>

    <!-- body -->
    <div class="page-content mt-2">
      <div class="text-h6 text-teal-darken-1 font-weight-bold mt-1">Lorem ipsum dolor sit amet consectetur adipisicing
        elit. Animi facilis odio accusamus sequi quasi consectetur placeat assumenda officia voluptas illo? Nisi quas
        deleniti fugiat ipsum distinctio aperiam quisquam quia aspernatur?</div>
    </div>

    <!-- footer -->
    <div class="d-flex align-center mt-2 ga-2 justify-space-between w-100">
      <span class="hidden">&nbsp;</span>
      <span>1</span>
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
}
</style>
