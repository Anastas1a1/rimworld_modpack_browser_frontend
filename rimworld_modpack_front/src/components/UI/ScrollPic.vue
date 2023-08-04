<template>
    <div class="scroll-pic">
      <div class="scroll-pic__container" ref="container">
        <div class="scroll-pic__slider" :style="sliderStyle">
          <div v-for="(image, index) in images" :key="index" class="scroll-pic__slide">
            <img :src="image" alt="Slide Image" />
          </div>
        </div>
      </div>
      <div class="scroll-pic__controls">
        <button @click="scrollLeft">&#8249;</button>
        <button @click="scrollRight">&#8250;</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      images: {
        type: Array,
        required: true,
      },
    },
    data() {
      return {
        scrollPosition: 0,
        slideWidth: 200, // Adjust the slide width based on your design
      };
    },
    computed: {
      sliderStyle() {
        return {
          transform: `translateX(-${this.scrollPosition}px)`,
        };
      },
    },
    methods: {
      scrollLeft() {
        this.scrollPosition = Math.max(this.scrollPosition - this.slideWidth, 0);
      },
      scrollRight() {
        const containerWidth = this.$refs.container.clientWidth;
        const maxScroll = this.images.length * this.slideWidth - containerWidth;
        this.scrollPosition = Math.min(this.scrollPosition + this.slideWidth, maxScroll);
      },
    },
  };
  </script>
  
  <style>
  /* Add your custom styles for ScrollPic component here */
  .scroll-pic {
    position: relative;
    overflow: hidden;
    width: 100%;
  }
  
  .scroll-pic__container {
    position: relative;
    overflow: hidden;
  }
  
  .scroll-pic__slider {
    display: flex;
    transition: transform 0.3s ease;
  }
  
  .scroll-pic__slide {
    flex-shrink: 0;
    width: 200px; /* Adjust the slide width based on your design */
    margin-right: 10px; /* Adjust the margin between slides based on your design */
  }
  
  .scroll-pic__slide img {
    width: 100%;
    height: auto;
  }
  
  .scroll-pic__controls {
    position: absolute;
    top: 50%;
    left: 0;
    right: 0;
    display: flex;
    justify-content: space-between;
    transform: translateY(-50%);
  }
  
  .scroll-pic__controls button {
    background-color: transparent;
    border: none;
    font-size: 24px;
    cursor: pointer;
  }
  
  /* You can add more styles as per your requirements */
  </style>
  