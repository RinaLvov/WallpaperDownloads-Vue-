<template>
  <div>
    <h2>The best free stock photos,and royalty free wallpapers</h2>
    <SearchBar @textUpdated="triggerSearch" />
    <DisplayedImages :images="filteredImages" />
  </div>
</template>

<script>
import SearchBar from "@/components/SearchBar.vue";
import DisplayedImages from "@/components/DisplayedImages.vue";
import ImageList from "@/ImageList.js";

export default {
  components: {
    SearchBar,
    DisplayedImages,
  },
  data() {
    return {
      images: ImageList,
      searchText: "",
    };
  },
  methods: {
    triggerSearch(value) {
      // console.log("I am in triggerSearch with value = " + value);
      this.searchText = value;
    },
  },
  computed: {
    filteredImages() {
      // console.log("FILTERED");
      return this.images
        .filter((image) => {
          if (this.searchText === "") return true;
          if (image.tags.includes(this.searchText)) return true;
          if (image.colours.includes(this.searchText)) return true;
          return false;
        })
        .slice(0, 10);
    },
  },
};
</script>

<style scoped>
h2 {
  font-size: 35px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin-top: 60px;
  font-family: "Montserrat", sans-serif;
}
</style>
