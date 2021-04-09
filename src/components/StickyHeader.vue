<template>
  <header :class="{ sticky: navbarSticky }"> 
    <a href="/" class="logo">
      <svg version="1.0" xmlns="http://www.w3.org/2000/svg"
      width="120pt" height="40pt" viewBox="0 0 1035 541"
      preserveAspectRatio="xMidYMid meet">
        <g transform="translate(0,541) scale(0.1,-0.1)" stroke="none">
          <path d="M2683 5378 c-26 -28 -943 -1776 -2085 -3973 -599 -1152 -601 -1156
          -591 -1166 5 -5 88 -59 183 -119 l174 -110 4978 0 4978 0 0 245 0 244 -4829 3
          c-2656 2 -4833 6 -4836 10 -4 4 138 292 315 640 298 584 482 944 1398 2730
          180 350 330 634 333 630 3 -4 339 -644 747 -1422 1131 -2161 1107 -2115 1125
          -2114 18 2 275 162 327 204 l34 28 -117 233 c-316 634 -1493 2879 -1914 3653
          -182 335 -178 329 -220 284z"/>
          <path d="M6141 3504 c-69 -35 -127 -112 -220 -294 -165 -321 -308 -756 -346
          -1054 -19 -142 -27 -163 -91 -241 -64 -79 -84 -120 -84 -173 0 -32 6 -49 25
          -67 13 -14 31 -25 40 -25 21 0 68 25 84 44 25 29 38 17 55 -50 29 -113 68
          -169 150 -212 45 -24 62 -27 151 -26 85 0 109 3 163 26 111 46 174 91 277 196
          56 56 104 102 108 102 14 0 6 -65 -28 -238 -86 -437 -103 -747 -49 -881 19
          -48 38 -61 88 -61 76 0 103 58 281 595 79 237 157 460 175 497 33 68 70 118
          89 118 6 0 36 -23 67 -51 75 -68 132 -92 214 -93 84 -1 127 15 205 75 36 27
          71 49 79 49 18 0 39 -27 119 -150 81 -124 127 -155 231 -155 140 0 295 101
          588 382 189 182 270 253 287 253 23 0 42 -70 42 -157 -1 -133 -22 -226 -85
          -366 -27 -60 -34 -133 -16 -167 14 -27 73 -43 128 -35 132 20 331 134 494 284
          l53 49 40 -77 c44 -82 99 -130 173 -151 63 -17 186 -12 254 11 117 39 226 131
          250 211 27 89 -65 122 -214 77 -186 -55 -255 -11 -188 121 10 19 56 83 101
          142 146 187 200 295 206 413 7 126 -45 180 -172 180 -86 0 -136 -23 -213 -98
          -104 -100 -178 -234 -227 -407 -15 -52 -39 -116 -52 -142 -38 -70 -274 -298
          -309 -298 -20 0 -18 9 25 135 47 137 56 200 41 285 -24 133 -116 267 -215 315
          -56 27 -155 32 -210 11 -65 -25 -120 -91 -135 -160 -17 -83 -75 -161 -250
          -338 -154 -155 -234 -218 -276 -218 -46 0 -78 69 -114 245 -28 136 -46 189
          -80 225 -23 25 -36 30 -73 30 -66 0 -143 -56 -300 -221 -101 -106 -136 -137
          -144 -127 -5 7 -31 54 -57 103 -89 170 -143 225 -222 225 -42 0 -75 -19 -122
          -70 -41 -45 -136 -252 -197 -428 -142 -414 -26 50 154 613 109 343 128 446 90
          492 -18 21 -95 17 -119 -7 -11 -11 -66 -113 -123 -227 -110 -221 -184 -349
          -275 -476 -256 -356 -490 -472 -605 -299 -72 110 -59 165 106 442 189 318 337
          658 400 921 48 198 47 306 -3 362 -25 28 -34 32 -96 35 -59 3 -77 0 -123 -24z
          m-50 -637 c-37 -136 -176 -435 -232 -499 l-20 -23 7 25 c3 14 29 79 57 145 27
          66 62 156 77 200 15 44 37 100 50 125 26 53 70 113 77 106 2 -2 -5 -38 -16
          -79z"/>
          <path d="M7935 3024 c-55 -19 -151 -98 -205 -169 -43 -56 -45 -61 -45 -126 0
          -64 2 -71 33 -101 30 -30 37 -33 95 -32 104 0 182 56 231 165 58 125 56 233
          -4 264 -35 18 -52 18 -105 -1z"/>
        </g>
      </svg>
    </a>
    <nav class="primary" :class="{'show': showNavbar }">
      <button class="toggle" @click="showNavbar = true">
        <svg viewBox="0 0 100 80" width="30" height="30" color="white">
          <rect width="100" height="20"></rect>
          <rect y="30" width="100" height="20"></rect>
          <rect y="60" width="100" height="20"></rect>
        </svg>
      </button>
      <div class="drawer">
        <div class="drawer-header">
          <button class="toggle" @click="showNavbar = false">
            <svg viewBox="0 0 100 80" width="30" height="30" color="white">
              <rect width="100" height="20"></rect>
              <rect y="30" width="100" height="20"></rect>
              <rect y="60" width="100" height="20"></rect>
            </svg>
          </button>
        </div>        
        <ul>
          <li><a href="#something">Something</a></li>
          <li><a href="#somethingelse">Something Else</a></li>
          <li><a href="#contactus">Contact Us</a></li>
        </ul>
      </div>
    </nav>
  </header>
</template>

<script setup>
import { ref } from 'vue'
const showNavbar = ref(false);
const navbarSticky = ref(false);

window.addEventListener('scroll', function (ev) {
  navbarSticky.value = window.scrollY > 0
})
</script>

<style>
header {
  --mobile-navigation-width: 300px;
  position: fixed;
  z-index: 10;
  width: 100%;
  display: flex;
  height: var(--header-height);
  background-color: var(--primary);
  justify-content: space-between;
  z-index: 20;
}
header a.logo {
  align-self: top;
  display: inline-block;
  border-radius: 8px;
  transition: 0.2s;
  height: var(--header-height);
  padding: 6px 12px;
}
header a.logo svg {
  fill: var(--primary-A200-contrast);
  height: 100%;
}
header.sticky {
  box-shadow: rgba(0, 0, 0, 0.16) 0px 10px 36px 0px, rgba(0, 0, 0, 0.06) 0px 0px 0px 1px;  
}
nav.primary {
  position: relative;
  height: var(--header-height);
  top: 0;
}
nav.primary .toggle {
  border: none;
  padding: 5px;
  height: var(--header-height);
  width: var(--header-height);
  line-height: 1;
  border-radius: 0;
  background: transparent;
  -webkit-appearance: none;
}
nav.primary .toggle svg {
  fill: var(--primary-A200-contrast)
}
nav.primary .drawer {
  z-index: 10;
  position: fixed;
  right: calc(var(--mobile-navigation-width) * -1);
  width: var(--mobile-navigation-width);
  max-width: 100vw;
  transition: 0.3s;
  top: 0;
  height: 100vh;
  visibility: hidden;
}
nav.primary.show .drawer {
  right: 0;
  visibility: visible;
  box-shadow: rgba(0, 0, 0, 0.16) 0px 10px 36px 0px, rgba(0, 0, 0, 0.06) 0px 0px 0px 1px;  
}
nav.primary .drawer .drawer-header {
  height: var(--header-height);
  text-align: right;
  background: var(--neutral-500);
  fill: var(--neutral-500-contrast)
}
nav.primary .drawer ul {
  padding-left: 0;
  margin-top: 0;
  background: var(--neutral-300);
  color: var(--neutral-300-contrast);
  list-style-type: none;
  height: calc(100vh - var(--header-height));
  box-shadow: rgba(50, 50, 93, 0.25) 0px 30px 60px -12px inset, rgba(0, 0, 0, 0.3) 0px 18px 36px -18px inset;
  margin-block-end: 0;
}
nav.primary ul li a {
  text-decoration: none;
  color: var(--neutral-200-contrast);
  display: block;
  padding: 0 12px;
  margin: 0 12px;
  font-size: 1.4rem;
  border-bottom: 3px solid transparent;
}
@media only screen and (min-width: 60rem) {
  header {
    background: transparent;
  }
  header.sticky {
    background: var(--primary-A200);
  }
  header a.logo {
    height: calc(var(--header-height) * 2);
    padding: 24px 48px 12px;
  }
  header.sticky a.logo {
    height: var(--header-height);
    padding: 6px 12px;
  }
  nav.primary .toggle {
    display: none;
  }
  nav.primary .drawer {
    visibility: visible;
    width: auto;
    right: auto;
    position: initial;
    height: var(--header-height);
    background-color: transparent;
    box-shadow: none;
  }
  nav.primary .drawer .drawer-header {
    display: none;
  }
  nav.primary .drawer ul {
    height: auto;
    background-color: transparent;
    display: flex;
    align-items: stretch;
    box-shadow: none;
  }
  nav.primary ul li a {
    line-height: var(--header-height);
    color: var(--primary-A200-contrast);
  }
}
</style>