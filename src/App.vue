<template>
  <div id="app">
    <header>
    </header>

    <main>
      <div class="content">
        <section class="card">
          <h2>Click Counter</h2>
          <div class="counter">
            <p>Count: {{ count }}</p>
            <div class="counter-buttons">
              <button @click="decrementCount">-</button>
              <button @click="incrementCount">+</button>
            </div>
          </div>
        </section>

        <section class="card">
          <h2>Box Color Changer</h2>
            <div class="current-color-box" :style="boxStyle"></div>
            <div class="color-changer">
            <button @click="changeColor">Change Color</button>
          </div>
        </section>

        <section class="card carousel-section">
          <h2>Image Carousel</h2>
          <div class="carousel">
            <img :src="currentImage" alt="Carousel Image" class="carousel-image" />
            <div class="carousel-controls">
              <button @click="prevImage">Previous</button>
              <button @click="nextImage">Next</button>
            </div>
          </div>
        </section>
        
      </div>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,

      colors: ['#FF5733', '#33FF57', '#3357FF', '#F333FF'],
      currentColorIndex: 0,

      images: [
        'https://png.pngtree.com/thumb_back/fh260/background/20230412/pngtree-colorful-rhythmic-graphic-abstract-background-image_2206467.jpg',
        'https://png.pngtree.com/background/20230528/original/pngtree-colorful-woman-s-abstract-artwork-picture-image_2772308.jpg',
        'https://png.pngtree.com/thumb_back/fh260/background/20230521/pngtree-digitally-textured-abstract-background-with-colorful-triangles-image_2661686.jpg'
      ],
      currentImageIndex: 0,
    };
  },
  computed: {
    currentImage() {
      return this.images[this.currentImageIndex];
    },
    boxStyle() {
      return {
        width: '100px',
        height: '100px',
        backgroundColor: this.colors[this.currentColorIndex],
        border: '1px solid black',
        margin: '10px 35%'
      };
    }
  },
  methods: {
    incrementCount() {
      this.count++;
    },
    decrementCount() {
      if (this.count > 0) {
        this.count--;
      }
    },
  
    changeColor() {
      this.currentColorIndex = (this.currentColorIndex + 1) % this.colors.length;
    },

    nextImage() {
      this.currentImageIndex = (this.currentImageIndex + 1) % this.images.length;
    },
    prevImage() {
      this.currentImageIndex =
        (this.currentImageIndex - 1 + this.images.length) % this.images.length;
    }
  }
};
</script>

<style>

/* General Styling */


#app {
  text-align: center;
  color: #ffffff;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px;
}

header {
  margin-bottom: 30px;
}

h1 {
  color: #000000;
  margin: 5;
}

/* Layout and Grid */
.content {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
  max-width: 1200px;
  width: 100%;
}

/* Card Styling */
.card {
  padding: 20px;
  border-radius: 15px;
  backdrop-filter: blur(10px);
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.2);
  color: #000000;
  background-color: #d0d0d0;
}

/* Counter Section */
.counter {
  font-size: 2em;
  margin: 10px 0;
}

.counter-buttons {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10px;
}


/* Carousel Styling */
.carousel-section {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.carousel {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.carousel-image {
  width: 100%;
  max-width: 350px;
  height: auto;
  border-radius: 15px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
  margin-bottom: 10px;
}


/* Color Picker Styling */
.current-color-box {
  width: 100px;
  height: 100px;
  margin: 10px auto 20px;
  border-radius: 15px;
  border: 2px solid #000000;
}
</style>