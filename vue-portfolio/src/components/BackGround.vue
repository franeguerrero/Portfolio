<template>
  <div class="noisy-mesh-gradient">
    <div class="circle"></div>
    <div class="circle"></div>
    <div class="circle"></div>
    <div class="circle"></div>
  </div>
</template>

<style scoped>
.noisy-mesh-gradient {
  width: 100vw;
  height: 100vh;
  position: fixed;
  top: 0;
  left: 0;
  z-index: -1;
  background-color: #141414;
  overflow: hidden;
}

.circle {
  position: absolute;
  border-radius: 50%;
  animation: animateCircles 10s infinite linear;
  filter: blur(100px);
  z-index: -1;
}

.circle:nth-child(1) {
  background: conic-gradient(
    from 45deg,
    #6d3d8f 0deg 60deg,
    #4b25a1 60deg 150deg,
    #4c2a85 150deg 210deg,
    #6d3d8f 210deg 270deg,
    #4b25a1 270deg 330deg,
    #4c2a85 330deg 360deg
  );
  width: 80rem;
  height: 80rem;
  left: -10vw;
  top: -50vh;
}

.circle:nth-child(2) {
  background: conic-gradient(
    from 30deg,
    #ff006225 0deg 45deg,
    #00b3ff54 45deg 120deg,
    #0a027362 120deg 180deg,
    #961a5428 180deg 240deg,
    #0a84ff4a 240deg 300deg,
    #2607824e 300deg 360deg
  );
  width: 80rem;
  height: 80rem;
  left: -35vw;
  top: -55vh;
}

.circle:nth-child(3) {
  background: conic-gradient(
    from 60deg,
    #4b25a1 0deg 75deg,
    #4c2a85 75deg 135deg,
    #6d3d8f 135deg 205deg,
    #4b25a1 205deg 265deg,
    #4c2a85 265deg 325deg,
    #6d3d8f 325deg 360deg
  );
  width: 40rem;
  height: 40rem;
  left: 70vw;
  top: 50vh;
}

.circle:nth-child(4) {
  background: conic-gradient(
    from 30deg,
    #ff006225 0deg 45deg,
    #00b3ff54 45deg 120deg,
    #0a027362 120deg 180deg,
    #961a5428 180deg 240deg,
    #0a84ff4a 240deg 300deg,
    #2607824e 300deg 360deg
  );
  width: 40rem;
  height: 40rem;
  left: 75vw;
  top: 45vh;
}

.noisy-mesh-gradient::before {
  content: "";
  position: absolute;
  width: 100%;
  height: 100%;
  background-image: url(@/assets/noise.png);
  opacity: 0.3;
  pointer-events: none;
  filter: brightness(1);
  mix-blend-mode: multiply;
}

@keyframes animateCircles {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
