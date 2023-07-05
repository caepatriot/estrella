<template>
  <v-app>
    <v-card>
      <v-container fluid>
        <v-row class="justify-center">
          <!-- <v-btn-toggle v-model="alignment" variant="outlined" divided>
            <v-btn>
              <v-icon icon="mdi-format-align-center"></v-icon>
            </v-btn>

            <v-btn>
              <v-icon icon="mdi-format-align-left"></v-icon>
            </v-btn>

            <v-btn>
              <v-icon icon="mdi-format-align-right"></v-icon>
            </v-btn>
          </v-btn-toggle>

          <v-btn-toggle v-model="alignment" variant="outlined" divided>
            <v-btn @click="imgWidth -= 2">
              <v-icon icon="mdi-minus"></v-icon>
            </v-btn>

            <v-btn @click="imgWidth += 2">
              <v-icon icon="mdi-plus"></v-icon>
            </v-btn>
          </v-btn-toggle> -->
        </v-row>
        <v-row>
          <v-col>
            <v-card-title>
              <v-btn-toggle v-model="alignment" variant="outlined" divided>
                <v-btn>
                  <v-icon icon="mdi-format-align-center"></v-icon>
                </v-btn>

                <v-btn>
                  <v-icon icon="mdi-format-align-left"></v-icon>
                </v-btn>

                <v-btn>
                  <v-icon icon="mdi-format-align-right"></v-icon>
                </v-btn>
              </v-btn-toggle>

              <v-btn-toggle v-model="alignment" variant="outlined" divided>
                <v-btn @click="imgWidth -= 2">
                  <v-icon icon="mdi-minus"></v-icon>
                </v-btn>

                <v-btn @click="imgWidth += 2">
                  <v-icon icon="mdi-plus"></v-icon>
                </v-btn>
              </v-btn-toggle>
            </v-card-title>
            <v-card-text>
              <div class="d-flex flex-column productMainContainer">
                <div class="d-flex flex-column">
                  <div class="pa-2">
                    <!-- <v-slider
                      track-size="2px"
                      v-model="imgWidth"
                      :min="10"
                      :max="50"
                      :step="2"
                    ></v-slider> -->
                  </div>
                  <div
                    class="productPreviewContainer d-flex flex-row align-center"
                  >
                    <canvas
                      id="drawCanvas"
                      class=""
                      ref="canvas"
                      @mousedown="startDrawing"
                      @mousemove="draw"
                      @mouseup="stopDrawing"
                      @mouseout="stopDrawing"
                    >
                    </canvas>
                    <v-img
                      aspect-ratio="1"
                      class="productPreview"
                      :src="imgurl"
                      lazy-src="https://picsum.photos/id/11/10/6"
                      :width="imgWidth + 'vw'"
                    ></v-img>
                    <v-img
                      aspect-ratio="1"
                      class="productPreview"
                      :src="image"
                      lazy-src="https://picsum.photos/id/11/10/6"
                    ></v-img>
                  </div>
                </div>

                <v-file-input
                  v-model="image"
                  accept="image/png, image/jpeg, image/bmp"
                  placeholder="Pick an image"
                  prepend-icon="mdi-camera"
                  @change="changeFile"
                  @click:clear="clearImagePreview()"
                  label="Image"
                ></v-file-input>
              </div>
            </v-card-text>
          </v-col>
          <v-divider vertical></v-divider>

          <v-col>
            <v-layout>
              <v-list class="mx-5" :items="items"></v-list>
            </v-layout>
          </v-col>
        </v-row>
      </v-container>
    </v-card>
  </v-app>
</template>

<style scoped>
.productPreview {
}

.productPreview.v-responsive {
  /* display: initial; */
}

.productPreviewContainer {
  position: relative;
  height: fit-content;
  width: auto;
}

#drawCanvas {
  position: absolute;
  z-index: 5;
  top: 0;
  left: 0;
  width: 0;
  height: 100%;
  width: 100%;
  border: 5px solid red;
}
</style>

<script>
export default {
  name: "ClientReviewer",

  data: () => ({
    /* PROJECT LIST */
    items: [
      { type: "subheader", title: "Project #1" },
      {
        title: "Item wfewef #1",
        value: 1,
      },
      {
        title: "Item wefwfwef #2",
        value: 2,
      },
      {
        title: "Item qwfdqwd #3",
        value: 3,
      },
      { type: "divider" },
      { type: "subheader", title: "Project #2" },
      {
        title: "Item #4",
        value: 4,
      },
      {
        title: "Item #5",
        value: 5,
      },
      {
        title: "Item #6",
        value: 6,
      },
    ],

    imgurl: null,
    imgWidth: 10,
    /* CANVAS VARIABLES */
    isDrawing: false,
    lastX: 0,
    lastY: 0,

    /* TEST */
    image: null
  }),

  mounted() {
    this.canvas = this.$refs.canvas;
    this.context = this.canvas.getContext("2d");

    // this.image = new URL("@/assets/logo.png", import.meta.url);
    // this.image = URL.createObjectURL(this.image.url)
    // console.log(this.image);
  },

  methods: {
    changeFile(e) {
      const file = e.target.files[0];
      this.imgurl = URL.createObjectURL(file);
    },

    async clearImagePreview() {
      this.imagePreview = "";
    },

    /* CANVAS DRAWING */

    startDrawing(event) {
      this.isDrawing = true;
      [this.lastX, this.lastY] = [event.offsetX, event.offsetY];
    },

    draw(event) {
      if (!this.isDrawing) return;

      this.context.beginPath();
      this.context.moveTo(this.lastX, this.lastY);
      this.context.lineTo(event.offsetX, event.offsetY);
      this.context.stroke();

      [this.lastX, this.lastY] = [event.offsetX, event.offsetY];
    },
    stopDrawing() {
      this.isDrawing = false;
    },
  },
};
</script>
