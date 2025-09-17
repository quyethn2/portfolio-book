<template>
  <div class="d-flex flex-column align-center justify-center w-100">

    <!-- header -->
    <div class="text-h5 text-grey-darken-3 font-weight-bold mt-2">Work Experience</div>

    <!-- body -->
    <div class="page-content mt-2">
      <v-timeline align="start" side="end">
        <v-timeline-item dot-color="red-darken-3" size="small">
          <template v-slot:opposite>
            <div class="text-body">07/2023 - 02/2025</div>
          </template>
          <div class="d-flex">
            <div>
              <strong>RIKKEI SOFT</strong>

              <div>
                <img src="../../static/images/RK.png" alt="RIKKEI" height="50">
              </div>
            </div>
          </div>
        </v-timeline-item>

        <v-timeline-item dot-color="blue" size="small">
          <template v-slot:opposite>
            <div class="text-body">05/2022 - 02/2023</div>
          </template>
          <div class="d-flex">
            <div>
              <strong>CMC GLOBAL</strong>
              <div class="mt-2">
                <img src="../../static/images/CMC.png" alt="CMC" height="50">
              </div>
            </div>
          </div>
        </v-timeline-item>

        <v-timeline-item dot-color="red-lighten-1" size="small">
          <template v-slot:opposite>
            <div class="text-body">08/2017 - 04/2022</div>
          </template>
          <div class="d-flex">
            <div>
              <strong>SITEN JSC</strong>
              <div class="">
                <img src="../../static/images/siten.svg" alt="SITEN" height="50">
              </div>
            </div>
          </div>
        </v-timeline-item>
      </v-timeline>
    </div>

    <!-- footer -->
    <div class="d-flex align-center mt-2 ga-2 justify-space-between w-100">
      <span class="hidden">&nbsp;</span>
      <!-- <span>1</span> -->
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
