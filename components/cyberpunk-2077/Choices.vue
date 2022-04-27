<template>
  <div :class="['choices', clicked ? 'clicked' : '']">
    <div :class="choice.active ? 'active' : ''" v-for="choice in choices" :key="choice.id" @click="handleClick(choice)">
      <Button :text="choice.button.text" :icon="choice.button.icon" />
    </div>
  </div>
</template>
https://youtu.be/QH9gRxVa2lI?t=964
<script>
import Button from './Button.vue'
export default {
  components: { Button },
  data() {
    return {
      choices: this.initChoices,
      clicked : false
    }
  },
  props: {
    initChoices: {
      type: Array,
      required: true
    }
  },
  methods: {
    handleClick(e) {
      //emit event
      e.active = true;
      this.clicked = true;
      if(e.actions) {
        setTimeout(()=> {
          this.clicked = false;
          this.choices = e.actions;
        }, 850);
      }
    }
  }
}
</script>

<style lang="scss" scoped>

.choices {
  display: flex;
  flex-flow: column nowrap;
  align-items: flex-start;
  transition: 150ms opacity;
  opacity: 1;
  >div {
    transition: 300ms transform 0ms, 100ms opacity 200ms;
    margin: 0.3rem 0;
  }
  &.clicked {
    transition: 150ms opacity 600ms;
    opacity: 0;
    >div:not(.active) {
      transform: translateX(-25px);
      opacity: 0;
    }
  }
}

</style>