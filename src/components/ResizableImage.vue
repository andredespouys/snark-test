<template>

  <div class="ex-1">
  <!-- <font-awesome-icon icon="1" /> -->
  <h2 class="ex-title">1- Conditional Image</h2>
  <div class="A">
    <img :src="imageUrl"/>
  </div>
  </div>
</template>
<style>

.ex-1{
  display: flex;
  flex-direction: column;
  align-items: center;
}
.ex-title{
  font-size: 2rem;
  font-weight: 500;
}
/* Style CSS for the div "A" */
.A {
  position: relative;
  border: 1px solid #000;
  border-radius: 1rem;
  width: 80%;
  margin: 0;
  height: 400px;
  padding: 0;
}

/* Style CSS for the image inside the div "A" */
/* Here I set the space of 15 px as asked using calc function */
.A img {
  position: absolute;
  top: 15px;
  left: 15px;
  height: calc(100% - 30px);
  width: calc(100% - 30px);
  border-radius: 1rem;
}
</style>
<script>

export default {
  el: '.A',
  data() {
    return {
      imageUrl: './src/assets/portrait.png', // Default image URL (you can change it if needed)
    };
  },
  mounted() {
    try {
    this.$nextTick(() => {
      this.resized(); // Call the resized function when the component is mounted
      window.addEventListener('resize', this.resized); // Listen for resize events
    });
  } catch (error) {
    console.error('Error in mounted hook:', error);
  }
  },
  beforeUnmount() {
    try {
      window.removeEventListener('resize', this.resized); // Remove the resize event listener when the component is unmounted
      console.log('Unmounted');
    } catch(error){
      console.error('Error in before Unmounted hook:', error);

    }
  },
  methods: {
    resized() {
      const divA = this.$el;
      console.log(divA);
      const imgA = this.$el.querySelector('img');
      console.log(imgA);
      const ratio = divA.offsetWidth / divA.offsetHeight;

      if (ratio >= 1) {
        this.imageUrl = './src/assets/landscape.png'; // Set the image URL to "paysage.png" if the ratio is greater than or equal to 1
        console.log(ratio)
      } else {
        this.imageUrl = './src/assets/portrait.png'; // Set the image URL to "portrait.png" otherwise
        console.log(ratio)

      }
    },
  },
};
</script>
