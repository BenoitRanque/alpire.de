<template>
  <div class="cube">
    <div class="a-side">
      <slot name="a-side"></slot>
    </div>
    <div class="b-side">
      <slot name="b-side"></slot>
    </div>
  </div>  
</template>

<script>
</script>

<style>
.cube {
  transition: transform .33s;
  transform-style: preserve-3d;
  height: 200px;
  width: 200px;
  cursor: pointer;
}
.cube .a-side, .cube .b-side {
  height: 200px;
  width: 200px;
  box-shadow: rgba(0, 0, 0, 0.07) 0px 1px 2px, rgba(0, 0, 0, 0.07) 0px 2px 4px, rgba(0, 0, 0, 0.07) 0px 4px 8px, rgba(0, 0, 0, 0.07) 0px 8px 16px, rgba(0, 0, 0, 0.07) 0px 16px 32px, rgba(0, 0, 0, 0.07) 0px 32px 64px;
  background: var(--neutral-500);
  color: var(--neutral-500-contrast);
}
.cube .a-side {
  transform: translateZ(100px);
}
.cube .b-side {
  transform: rotateX(-90deg) translateZ(-100px);
}
.cube:hover {
	transform: rotateX(90deg); /* Text bleed at 90º */
}
</style>