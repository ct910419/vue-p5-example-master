<template>
  <div>
    <vue-p5
        @preload="preload"
        @setup="setup"
        @draw="draw"
        @keypressed="keyPressed"
        @mousemoved="mouseMoved"
        @mousedragged="mouseDragged">
    </vue-p5>
  </div>
</template>

<script>
import VueP5 from "vue-p5";
export default {
  name: "p5-example",
  components: {
    "vue-p5": VueP5
  },
  data: () => ({
    xoff:0.0,
    xincrement:0.01,
  }),
  methods: {
    setup(sketch) {
      sketch.createCanvas(710, 400);
      sketch.background(0);
      sketch.noStroke();
    },
    draw(sketch) {
      sketch.fill(0, 10);
      sketch.rect(0, 0, sketch.width, sketch.height);
      let n = sketch.noise(this.xoff) * sketch.width;
      this.xoff += this.xincrement;
      sketch.fill(200);
      sketch.ellipse(n, sketch.height / 2, 64, 64);
    },
  }
};
</script>