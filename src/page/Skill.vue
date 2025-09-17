<template>
  <div class="d-flex flex-column align-center justify-center w-100">

    <!-- header -->
    <div class="text-h5 text-grey-darken-3 font-weight-bold mt-2">My Skills</div>

    <!-- body -->
    <div class="page-content mt-2">
      <div class="d-flex ga-2">

        <v-card color="teal-darken-1" variant="outlined" class="mx-auto">
          <v-card-item>
            <div>
              <v-icon color="teal-darken-1" icon="mdi-language-html5" size="50px"></v-icon>
              <div class="text-caption text-center text-teal-darken-1">HTML5</div>
            </div>
          </v-card-item>
        </v-card>

        <v-card color="teal-darken-1" variant="outlined" class="mx-auto">
          <v-card-item>
            <div>
              <v-icon color="teal-darken-1" icon="mdi-language-css3" size="50px"></v-icon>
              <div class="text-caption text-center text-teal-darken-1">CSS3</div>
            </div>
          </v-card-item>
        </v-card>

        <v-card color="teal-darken-1" variant="outlined" class="mx-auto">
          <v-card-item>
            <div>
              <v-icon color="teal-darken-1" icon="mdi-language-javascript" size="50px"></v-icon>
              <div class="text-caption text-center text-teal-darken-1">Javascript</div>
            </div>
          </v-card-item>
        </v-card>

        <v-card color="teal-darken-1" variant="outlined" class="mx-auto">
          <v-card-item>
            <div>
              <v-icon color="teal-darken-1" icon="mdi-language-typescript" size="50px"></v-icon>
              <div class="text-caption text-center text-teal-darken-1">Typescript</div>
            </div>
          </v-card-item>
        </v-card>
      </div>
      <div class="d-flex ga-2 mt-2">
        <v-card color="teal-darken-1" variant="outlined" class="mx-auto">
          <v-card-item>
            <div>
              <v-icon color="teal-darken-1" icon="mdi-vuejs" size="50px"></v-icon>
              <div class="text-caption text-center text-teal-darken-1">Vuejs</div>
            </div>
          </v-card-item>
        </v-card>

        <v-card color="teal-darken-1" variant="outlined" class="mx-auto">
          <v-card-item>
            <div>
              <v-icon color="teal-darken-1" icon="mdi-react" size="50px"></v-icon>
              <div class="text-caption text-center text-teal-darken-1">Reactjs</div>
            </div>
          </v-card-item>
        </v-card>

        <v-card color="teal-darken-1" variant="outlined" class="mx-auto">
          <v-card-item>
            <div>
              <v-icon color="teal-darken-1" icon="mdi-angular" size="50px"></v-icon>
              <div class="text-caption text-center text-teal-darken-1">Angular</div>
            </div>
          </v-card-item>
        </v-card>

        <v-card color="teal-darken-1" variant="outlined" class="mx-auto">
          <v-card-item>
            <div>
              <v-icon color="teal-darken-1" icon="mdi-vuetify" size="50px"></v-icon>
              <div class="text-caption text-center text-teal-darken-1">Vuetify</div>
            </div>
          </v-card-item>
        </v-card>
      </div>

      <div class="d-flex ga-2 mt-2">
        <v-card color="teal-darken-1" variant="outlined" class="mx-auto">
          <v-card-item>
            <div>
              <v-icon color="teal-darken-1" icon="mdi-material-ui" size="50px"></v-icon>
              <div class="text-caption text-center text-teal-darken-1">Material UI</div>
            </div>
          </v-card-item>
        </v-card>

        <v-card color="teal-darken-1" variant="outlined" class="mx-auto">
          <v-card-item>
            <div>
              <v-icon color="teal-darken-1" icon="mdi-tailwind" size="50px"></v-icon>
              <div class="text-caption text-center text-teal-darken-1">Tailwind CSS</div>
            </div>
          </v-card-item>
        </v-card>

        <v-card color="teal-darken-1" variant="outlined" class="mx-auto">
          <v-card-item>
            <div>
              <v-icon color="teal-darken-1" icon="mdi-git" size="50px"></v-icon>
              <div class="text-caption text-center text-teal-darken-1">Git</div>
            </div>
          </v-card-item>
        </v-card>

        <v-card color="teal-darken-1" variant="outlined" class="mx-auto">
          <v-card-item>
            <div>
              <v-icon color="teal-darken-1" icon="mdi-microsoft-visual-studio-code" size="50px"></v-icon>
              <div class="text-caption text-center text-teal-darken-1">VS code</div>
            </div>
          </v-card-item>
        </v-card>
      </div>

    </div>

    <!-- footer -->
    <div class="d-flex align-center mt-2 ga-2 justify-space-between w-100">
      <v-btn class="ma-2" size="x-small" color="teal-darken-1" variant="outlined"
        @click.prevent="props.togglePage(props.indexPage)" :disabled="!!props.item?.animating" icon="mdi-arrow-left">
      </v-btn>
      <!-- <span>2</span> -->
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
