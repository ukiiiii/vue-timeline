<template lang="html">
<div>
  <image-slider>
    <p>
      <a @click="prev" href='#'>Previous</a> || <a @click="next" href='#'>Next</a>
    </p>

    <transition-group name='fade' tag='div'>
      <div
       v-for="number in [currentNumber]"
       :key='number'
       >
         <img
             :src="currentImage"
             v-on:mouseover="stopRotation"
             v-on:mouseout="startRotation"
             />
    </div>
  </transition-group>
</image-slider>

</div>
</template>

<script>
export default {
    data: {
        images: [
          "/static/photo1.jpg",
          "/static/photo2.jpg",
          "/static/photo3.jpg",
          "/static/photo4.jpg",
          "/static/photo5.jpg"
        ],
        currentNumber: 0,
        timer: null
    },

    mounted: function () {
        this.startRotation();
    },

    methods: {
        startRotation: function() {
            this.timer = setInterval(this.next, 3000);
        },

        stopRotation: function() {
            clearTimeout(this.timer);
            this.timer = null;
        },

        next: function() {
            this.currentNumber += 1
        },
        prev: function() {
            this.currentNumber -= 1
        }
    },

    computed: {
    	currentImage: function() {
      	return this.images[Math.abs(this.currentNumber) % this.images.length];
      }
    }
};
</script>

<style>

.fade-enter-active, .fade-leave-active {
  transition: all 0.8s ease;
  overflow: hidden;
  visibility: visible;
  opacity: 1;
  position: absolute;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
  visibility: hidden;
}
</style>
