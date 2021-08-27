<template>
  <div :class="['button', isActive ? 'active' : '']" :style="clipPath" @click="isActive = true">
    <span v-if="icon" class="material-icons-outlined">{{icon}}</span>
    <p>{{text}}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isActive: false,
    }
  },
  props: {
    text: {
      type: String,
      required: true
    },
    icon: {
      type: String,
      required: false
    }
  },
  computed: {
    clipPath() {
      const rand = () => {return Math.floor(Math.random() * 12)};
      return {
        '--a': rand() + 'px',
        '--b': 'calc(100% - ' + rand() + 'px)',
        '--c': 'calc(100% - ' + rand() + 'px)',
        '--d': rand() + 'px'
      }
    }
  }
}
</script>

<style lang="scss" scoped>

$primary: #f4b900;
$secondary: #0a090a;
$text: #2a0300;
$white: #fff;

@mixin baseInteraction {
  font-weight: 500;
  span, p {
    color: $text;
  }
}
@keyframes scaleButton {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.2);
  }
  100% {
    transform: scale(1);
  }
}

.button {
  display: flex;
  align-items: center;
  font-family: 'Roboto', sans-serif;
  position: relative;
  background-color: $secondary;
  cursor: pointer;
  padding: 5px 17px;
  user-select: none;

  clip-path: polygon(var(--a) 0, var(--b) 0, var(--c) 100%, var(--d) 100%);

  transition: 150ms padding ease-out;

  span {
    margin-right: 7px;
    font-size: 1rem;
  }
  p {
    
    margin: 0;
  }
  span, p {
    position: relative;
    z-index: 3;
    color: $white;
  }
  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: $primary;
    z-index: 2;
    transition: 75ms;
    clip-path: polygon(100% 100%, 100% 53%, 100% 100%, 100% 100%, 100% 85%, 100% 71%, 100% 32%);
  }

  &:not(.active):hover {
    @include baseInteraction();
    padding-right: 27px;
    &::before {
      clip-path: polygon(50% 0%, 100% 0, 100% 60%, 100% 100%, 0 100%, 0% 60%, 0 0);
    }
  }
  &.active {
    @include baseInteraction();
    background-color: $primary;
    animation: 300ms ease-out alternate scaleButton;
  }  
}

</style>