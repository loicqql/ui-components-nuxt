<template>
  <div class="container">
    <Choices :initChoices="choices" />
  </div>  
</template>

<script>
import Choices from '../../components/road-96/Choices.vue'
export default {
  components: { Choices },
  data() {
    return {
      choices: [
        {
          id: 1,
          button: {text: 'Parler à Zoé', icon: 'question_answer'},
          actions: [
            {
              id: 11,
              button: {text: 'Insister'},
              actions: [
                {
                  id: 111,
                  button: {text: 'Laisser tomber'},
                  actions: false
                }
              ]
            },
            {
              id: 12,
              button: {text: 'Laisser tomber'},
              actions: false
            }
          ]
        },
        {
          id: 2,
          button: {text: 'Dire bonjour à Nico'},
          actions: [
            {
              id: 21,
              button: {text: 'Wordpress'},
              actions: false
            },
            {
              id: 22,
              button: {text: 'Symfony', icon: 'question_answer'},
              actions: [
                {
                  id: 221,
                  button: {text: 'Tu es sûr ?'},
                  actions: false
                },
                {
                  id: 222,
                  button: {text: 'Go pour ça', icon: 'question_answer'},
                  actions: false
                }
              ]
            }
          ]
        },
        {
          id: 3,
          button: {text: 'Non'},
          actions: false
        },
      ]
    }
  }
}
</script>

<style lang="scss" scoped>

.container {
  padding: 100px;
}

</style>