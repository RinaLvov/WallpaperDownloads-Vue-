<template>
  <div class="wallpapers" id="mainDiv">
    <div
      v-for="(image, index) in images"
      :key="index"
      class="image"
      id="image1"
    >
      <img class="image" :src="image.fileName" />
      <div class="titleBtn">
        <p>{{ image.title }}</p>
        <v-btn @click="() => downloadImage(image.title)" class="downloadButton">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="16"
            height="16"
            fill="currentColor"
            class="bi bi-box-arrow-in-down"
            viewBox="0 0 16 16"
          >
            <path
              fill-rule="evenodd"
              d="M3.5 6a.5.5 0 0 0-.5.5v8a.5.5 0 0 0 .5.5h9a.5.5 0 0 0 .5-.5v-8a.5.5 0 0 0-.5-.5h-2a.5.5 0 0 1 0-1h2A1.5 1.5 0 0 1 14 6.5v8a1.5 1.5 0 0 1-1.5 1.5h-9A1.5 1.5 0 0 1 2 14.5v-8A1.5 1.5 0 0 1 3.5 5h2a.5.5 0 0 1 0 1h-2z"
            />
            <path
              fill-rule="evenodd"
              d="M7.646 11.854a.5.5 0 0 0 .708 0l3-3a.5.5 0 0 0-.708-.708L8.5 10.293V1.5a.5.5 0 0 0-1 0v8.793L5.354 8.146a.5.5 0 1 0-.708.708l3 3z"
            />
          </svg>
        </v-btn>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    images: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    downloadImage(title) {
      console.log("title parameter: ", title);
      const link = document.createElement("a");

      const filteredResult = this.images.filter(
        (image) => image.title === title
      );
      console.log("filteredResult: ", filteredResult);

      const selectedImage = filteredResult[0];
      console.log("selectedImage: ", selectedImage);

      link.href = selectedImage.fileName;
      link.download = selectedImage.title;
      link.click();

      /*
      ASSUMING THERE IS A PARAMETER CALLED title
      1. Find the image object that is assoicated with this title.
      2. link.href = selectedImage.fileName
      3. link.download = selectedImage.title 
      */
    },
  },
};
</script>

<style scoped>
.downloadButton {
  border: none;
  background: none;
  cursor: pointer;
  margin: 0;
  padding: 0;
}
.titleBtn {
  display: flex;
  justify-content: center;
  margin-top: 10px;
  flex-wrap: wrap;
}
</style>
