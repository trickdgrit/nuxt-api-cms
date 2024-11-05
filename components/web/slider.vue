<template>
  <div>
    <b-container class="mt-3">
      <b-carousel
        id="carousel-fade"
        style="
          background-color: #f5f5f5;
          box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
        "
        fade
        indicators
        img-width="1024"
        img-height="300"
      >
        <b-carousel-slide
          v-for="slider in sliders"
          :key="slider.id"
          :img-src="slider.image"
        ></b-carousel-slide>
      </b-carousel>
    </b-container>
  </div>
</template>

<script>
export default {
  //data function
  data() {
    return {
      //state sliders
      sliders: [],
    };
  },

  async fetch() {
    //fething sliders on Rest API
    await this.$axios.get("/api/web/sliders").then((response) => {
      //assign response to state "sliders"
      this.sliders = response.data.data;
    });
  },
};
</script>

<style></style>
