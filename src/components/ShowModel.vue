<template>
  <body>
    <div id="pixi"></div>
  </body>
</template>

<script>
import * as PIXI from "pixi.js";

export default {
  name: "Visualisation",
  data() {
    return {
      app: new PIXI.Application(),
    };
  },

  methods: {
    init: function () {
      const app = new PIXI.Application({
        width: 800,
        height: 600,
        backgroundColor: 0x1099bb,
        resolution: window.devicePixelRatio || 1,
      });
      document.body.appendChild(app.view);

      const container = new PIXI.Container();

      app.stage.addChild(container);

      // Create a new texture
      // const texture = PIXI.Texture.from(
      //   "https://syn-yf-design-tool.oss-cn-beijing.aliyuncs.com/panorama/editor/bedRoom/mobile_b.jpg"
      // );

      // Initialize the pixi Graphics class
      var graphics = new PIXI.Graphics();

      // Set the fill color
      graphics.beginFill(0xe74c3c); // Red

      // Draw a circle
      const temp = graphics.drawCircle(60, 185, 40); // drawCircle(x, y, radius)
      console.log(temp); // temp === graphics

      // Applies fill to lines and shapes since the last call to beginFill.
      graphics.endFill();

      // Set a new fill color
      graphics.beginFill(0x3498db); // Blue

      // Draw an ellipse
      graphics.drawEllipse(170, 185, 45, 25); // drawEllipse(x, y, width, height)
      graphics.endFill();

      graphics.beginFill(0x9b59b6); // Purple

      // Draw a rectangle
      graphics.drawRect(240, 150, 75, 75); // drawRect(x, y, width, height)
      graphics.endFill();

      graphics.beginFill(0x2c3e50); // Dark blue gray 'ish

      // Draw a rectangle with rounded corners
      graphics.drawRoundedRect(350, 160, 75, 50, 10); // drawRoundedRect(x, y, width, height, radius)
      graphics.endFill();

      graphics.beginFill(0xf1c40f); // Yellow

      // Draw a polygon to look like a star
      graphics.drawPolygon([
        550,
        100, // Starting x, y coordinates for the star
        570,
        150, // Star is drawn in a clockwork motion
        630,
        155,
        585,
        195,
        600,
        250,
        550,
        220,
        500,
        250,
        515,
        195,
        470,
        155,
        530,
        150,
      ]);

      graphics.endFill();

      // Add the graphics to the stage
      app.stage.addChild(graphics);

      setTimeout(()=>{
        graphics.clear();
        // 或者通过geometryData移除单个shape
      },4000);

      // Listen for animate update
      app.ticker.add((delta) => {
        // rotate the container!
        // use delta to create frame-independent transform
        container.rotation -= 0.01 * delta;
      });
    },
  },
  mounted() {
    this.init();
  },
};
</script>

<style>
.changepage {
  position: absolute;
  color: rgb(0, 0, 0);
  font-size: 30px;
}
.changepage:hover {
  position: absolute;
  color: rgb(53, 20, 199);
  font-size: 30px;
}
</style>
