<template>
  <div>
    <input type="number" v-model="index" min="0" v-bind:max="images.length-1" />
    <ul>
      <li v-bind:key="i" v-for="(img, i) in images" v-bind:hidden="i != index">
        <div v-if="img.complete">
          <img v-bind:src="img.src" />
        </div>
        <div v-else>
          <ImagePlaceholder />
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import Vue from "vue";
import _ from 'lodash'
import ImagePlaceholder from './ImagePlaceholder'

const api = "http://shibe.online/api/shibes?count=";
export default {
  name: "ImageView",
  components: {
    ImagePlaceholder
  },
  mounted: async function() {
    for (let index = 0; index < 2; index++) {
      this.requestImage(index);
    }

    document.addEventListener("keydown", event => {
      switch (event.code) {
        case "ArrowRight":
          this.index++;
          break;
        case "ArrowLeft":
          this.index--;
          break;
      }
      this.index = _.clamp(this.index, 0, this.images.length);
      if (this.index == this.images.length - 1)
        this.requestImage(this.index + 1);
    });
  },
  methods: {
    requestImage: function(index) {
      this.images.push("./assets/blank");
      fetch(api + 1)
        .then(response => response.json())
        .then(result => {
          let img = new Image();
          Vue.set(this.images, index, img);
          img.src = result[0];
          img.onload = () => {
            Vue.set(this.images, index, img);
          };
        });
    }
  },
  data() {
    return {
      images: [],
      index: 0
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  list-style: none;
}
img {
  width: 400px;
  height: auto;
}
</style>
