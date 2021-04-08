<template>
  <section class="palette">
    <div class="configuration">
      <article v-for="(color, name) in colors" :key="name" :class="name">
        <div class="header">
          <h2>
            {{color.name}}
          </h2>
          <input type="color" v-model="color.model.hex">
        </div>
        <p class="center">Hue: {{color.model.hue}}</p>
        <input type="range" :min="0" :max="360" v-model.number="color.model.hue">
        <p>Saturation: {{color.model.saturation}}</p>
        <input type="range" :min="0" :max="100" v-model.number="color.model.saturation">
        <p>Lightness: {{color.model.lightness}}</p>
        <input type="range" :min="0" :max="100" v-model.number="color.model.lightness">
        <p>Contrast Threshold: {{color.model.contrastThreshold}}%</p>
        <input type="range" :min="0" :max="100" v-model.number="color.model.contrastThreshold">
        <ul>
          <li v-for="variant in variants" :key="`${name}_${variant}`" :style="`background: var(--${name}-${variant}); color: var(--${name}-${variant}-contrast);`">{{name}}-{{variant}} </li>
        </ul>
      </article>
    </div>
    <div class="generated-variables">
      <article>
        <h2>Generated Configuration</h2>
        <p>Copy this generated configuration to themes.css</p>
        <pre>
          <code>
  --primary-h: {{colors.primary.model.hue}};
  --primary-s: {{colors.primary.model.saturation}};
  --primary-l: {{colors.primary.model.lightness}};
  --primary-contrast-threshold: {{colors.primary.model.contrastThreshold}}%;

  --secondary-h: {{colors.secondary.model.hue}};
  --secondary-s: {{colors.secondary.model.saturation}};
  --secondary-l: {{colors.secondary.model.lightness}};
  --secondary-contrast-threshold: {{colors.secondary.model.contrastThreshold}}%;
  
  --accent-h: {{colors.accent.model.hue}};
  --accent-s: {{colors.accent.model.saturation}};
  --accent-l: {{colors.accent.model.lightness}};
  --accent-contrast-threshold: {{colors.accent.model.contrastThreshold}}%;

  --neutral-h: {{colors.neutral.model.hue}};
  --neutral-s: {{colors.neutral.model.saturation}};
  --neutral-l: {{colors.neutral.model.lightness}};
  --neutral-contrast-threshold: {{colors.neutral.model.contrastThreshold}}%;
          </code>
        </pre>
      </article>
    </div>
  </section>
</template>

<script>
import { computed, ref } from 'vue'
/**
 * Converts an HSL color value to RGB. Conversion formula
 * adapted from http://en.wikipedia.org/wiki/HSL_color_space.
 * Assumes h, s, and l are contained in the set [0, 1] and
 * returns r, g, and b in the set [0, 255].
 *
 * @param   {number}  h       The hue
 * @param   {number}  s       The saturation
 * @param   {number}  l       The lightness
 * @return  {Array}           The RGB representation
 */
function hslToRgb(h, s, l){
    var r, g, b;

    if(s == 0){
        r = g = b = l; // achromatic
    }else{
        var hue2rgb = function hue2rgb(p, q, t){
            if(t < 0) t += 1;
            if(t > 1) t -= 1;
            if(t < 1/6) return p + (q - p) * 6 * t;
            if(t < 1/2) return q;
            if(t < 2/3) return p + (q - p) * (2/3 - t) * 6;
            return p;
        }

        var q = l < 0.5 ? l * (1 + s) : l + s - l * s;
        var p = 2 * l - q;
        r = hue2rgb(p, q, h + 1/3);
        g = hue2rgb(p, q, h);
        b = hue2rgb(p, q, h - 1/3);
    }

    return [Math.round(r * 255), Math.round(g * 255), Math.round(b * 255)];
}
/**
 * Converts an RGB color value to HSL. Conversion formula
 * adapted from http://en.wikipedia.org/wiki/HSL_color_space.
 * Assumes r, g, and b are contained in the set [0, 255] and
 * returns h, s, and l in the set [0, 1].
 *
 * @param   {number}  r       The red color value
 * @param   {number}  g       The green color value
 * @param   {number}  b       The blue color value
 * @return  {Array}           The HSL representation
 */
function rgbToHsl(r, g, b){
    r /= 255, g /= 255, b /= 255;
    var max = Math.max(r, g, b), min = Math.min(r, g, b);
    var h, s, l = (max + min) / 2;

    if(max == min){
        h = s = 0; // achromatic
    }else{
        var d = max - min;
        s = l > 0.5 ? d / (2 - max - min) : d / (max + min);
        switch(max){
            case r: h = (g - b) / d + (g < b ? 6 : 0); break;
            case g: h = (b - r) / d + 2; break;
            case b: h = (r - g) / d + 4; break;
        }
        h /= 6;
    }

    return [h, s, l];
}
function modelColor (name) {
  // dummy variables used to track update dependencies
  // vue does not detect changes to the css variables automatically.
  // whenever we update a css variable, we also update the dummy variable, so vue will update the corresponding computed value 
  let dummyHue = ref(null);
  let dummySaturation = ref(null);
  let dummyLightness = ref(null);
  let dummyContrastThreshold = ref(null);

  const hue = computed({
    get: () => {
      dummyHue.value; // dummy reference to hue, to trigger updates
      return Number(window.getComputedStyle(document.documentElement).getPropertyValue(`--${name}-h`))
    },
    set: value => {
      dummyHue.value = value; // dummy reference to hue, to trigger updates
      document.documentElement.style.setProperty(`--${name}-h`, value)
    }
  })

  const saturation = computed({
    get: () => {
      dummySaturation.value; // dummy reference to saturation, to trigger updates
      return Number(window.getComputedStyle(document.documentElement).getPropertyValue(`--${name}-s`))
    },
    set: value => {
      dummySaturation.value = value; // dummy reference to saturation, to trigger updates
      document.documentElement.style.setProperty(`--${name}-s`, value)
    }
  })
  const lightness = computed({
    get: () => {
      dummyLightness.value; // dummy reference to lightness, to trigger updates
      return Number(window.getComputedStyle(document.documentElement).getPropertyValue(`--${name}-l`))
    },
    set: value => {
      dummyLightness.value = value; // dummy reference to lightness, to trigger updates
      document.documentElement.style.setProperty(`--${name}-l`, value)
    }
  })
  const hex = computed({
    get: () => {
      let h = hue.value
      let s = saturation.value
      let l = lightness.value

      const [r, g, b] = hslToRgb(h / 360, s / 100, l / 100)

      let rStr = `00${r.toString(16)}`.slice(-2)
      let gStr = `00${g.toString(16)}`.slice(-2)
      let bStr = `00${b.toString(16)}`.slice(-2)
      return ['#', rStr, gStr, bStr].join('')
    },
    set: value => {
      let [, r, g, b] = value.match(/#([0-9A-Fa-f]{2})([0-9A-Fa-f]{2})([0-9A-Fa-f]{2})/)

      let [h, s, l] = rgbToHsl(parseInt(r, 16), parseInt(g, 16), parseInt(b, 16))

      hue.value = Math.round(h * 360)
      saturation.value = Math.round(s * 100)
      lightness.value = Math.round(l * 100)
    }
  })
  const contrastThreshold = computed({
    get: () => {
      dummyContrastThreshold.value; // dummy reference to contrast threshold, to trigger updates

      return Number(window.getComputedStyle(document.documentElement).getPropertyValue(`--${name}-contrast-threshold`).slice(0, -1))
    },
    set: value => {
      dummyContrastThreshold.value = value; // dummy reference to contrast threshold, to trigger updates

      document.documentElement.style.setProperty(`--${name}-contrast-threshold`, `${value}%`)
    }
  })
  return {
    hue, saturation, lightness, hex, contrastThreshold
  }
}
</script>


<script setup>
  import { reactive } from 'vue'

  const variants = [
    '50',
    '100',
    '200',
    '300',
    '400',
    '500',
    '600',
    '700',
    '800',
    '900',
    'A100',
    'A200',
    'A400',
    'A700',
  ]
  const colors = reactive({
    primary: {
      name: 'Primary',
      model: modelColor('primary')
    },
    secondary: {
      name: 'Secondary',
      model: modelColor('secondary')
    },
    accent: {
      name: 'Accent',
      model: modelColor('accent')
    },
    neutral: {
      name: 'Neutral',
      model: modelColor('neutral')
    }
  })
</script>

<style>
.palette {
  padding: 2rem;
}
.palette .configuration {
  display: flex;
  flex-wrap: wrap;
}
.palette .configuration .header {
  display: flex;
  align-items: center;
  border-radius: 6px;
  padding: 0.2rem 0;
}
.palette .configuration .header h2 {
  flex-grow: 1;
  margin: 0;
}
.palette .configuration .header input[type="color"] {
  height: 2rem;
  width: 3rem;
}

.palette .configuration article {
  padding: 1rem;
  box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px, rgba(60, 64, 67, 0.15) 0px 1px 3px 1px;
  background: white;
  margin: 1rem;
  border-radius: 0.4rem;
  flex-grow: 1;
}
.palette .configuration ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin-block-end: 0;
}
.palette .configuration ul li {
  padding: 0.1rem 0.5rem;
}
.palette .configuration input[type="range"] {
  width: 100%;
}

.palette .generated-variables {
  padding: 1rem;
}
.palette .generated-variables code {
  display: block;
  padding: 0.2rem 1rem;
  box-shadow: rgba(6, 24, 44, 0.4) 0px 0px 0px 2px, rgba(6, 24, 44, 0.65) 0px 4px 6px -1px, rgba(255, 255, 255, 0.08) 0px 1px 0px inset;
  background: var(--neutral-900);
  color: var(--neutral-900-contrast);
  border-radius: 20px;
}

</style>