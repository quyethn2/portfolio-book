<template>
  <div class="d-flex flex-column align-center justify-center w-100">

    <!-- header -->
    <div class="text-h5 text-grey-darken-3 font-weight-bold mt-2">Education</div>

    <!-- body -->
    <div class="page-content mt-2">
      <div class="font-weight-bold mt-1 text-teal-darken-1 align-center">
        <v-icon color="teal-darken-1" icon="mdi-calendar" size="small"></v-icon>
        2014 - 2017
      </div>
      <div class="text-h6 font-weight-bold mt-2">
        HaNoi Institute Of Technology
      </div>
      <div class="text-subtitle-2">
        Major: Information Technology
      </div>
      <div class="text-subtitle-2">
        Graduated: August 2017
      </div>
      <div class="text-subtitle-2">
        Degree classification: Good
      </div>
      <div class="text-subtitle-2">
        GPA: 2.87/4.0
      </div>

      <v-card color="teal-darken-1" variant="outlined" class="mx-auto">
        <v-card-item>
          <div class="text-center">
            <img src="../../static/images/associte.png" alt="associte" height="160">
          </div>
        </v-card-item>
      </v-card>
    </div>

    <!-- footer -->
    <div class="d-flex align-center mt-2 ga-2 justify-space-between w-100">
      <span class="hidden">&nbsp;</span>
      <!-- <span>3</span> -->
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
