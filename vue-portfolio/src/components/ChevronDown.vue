<template>
    <div id="chevron" class="chevron-down"></div>
</template>

<script setup lang="ts">

document.addEventListener("DOMContentLoaded", function() {
  const navbar = document.getElementById("chevron");
  if (navbar) {
    document.addEventListener("scroll", function() {
      if (window.scrollY > 50) {
        navbar.classList.add("transparent");
      } else {
        navbar.classList.remove("transparent");
      }
    });
  }
});

</script>

<style scoped>
.chevron-down {
    position: absolute;
    display: block;
    width: 22px;
    height: 22px;
    border: 2px solid transparent;
    border-radius: 100px;
    animation: shake-vertical 5s linear both;
    animation-iteration-count: infinite;
}

.transparent{
    opacity: 0;
    transition: .3s;
}
.chevron-down::after {
    content: "";
    display: block;
    box-sizing: border-box;
    position: absolute;
    width: 12px;
    height: 12px;
    border-bottom: 4px solid;
    border-right: 4px solid;
    transform: rotate(45deg);
    left: 4px;
    top: 2px
}

@keyframes shake-vertical {

    0%,
    100% {
        transform: translateY(0)
    }

    10%,
    30%,
    50%,
    70% {
        transform: translateY(-8px)
    }

    20%,
    40%,
    60% {
        transform: translateY(8px)
    }

    80% {
        transform: translateY(6.4px)
    }

    90% {
        transform: translateY(-6.4px)
    }

}
</style>