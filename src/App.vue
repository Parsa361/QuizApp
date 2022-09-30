<template>
  <div>
    <HeaderSection />
    <ContentSection v-if="questionList.length" :cQuestion="questionList[index]" :next="next" :index="this.index" />

  </div>
</template>

<script>
import HeaderSection from './components/Header.vue';
import ContentSection from './components/Content.vue';

export default {
  name: 'App',
  components: {
    HeaderSection,
    ContentSection, 
  },

  data() {
    return {
      questionList: [],
      index: 0,

    }
  },
  methods: {
    next() {
      if (this.index < 10) {
        this.index++;
      }
    },
  },

  mounted: function () {
    fetch('https://opentdb.com/api.php?amount=10&category=15&difficulty=easy&type=multiple', {
      method: 'get'
    }).then((response) => {
      return response.json()
    }).then((result) => {
      this.questionList = result.results
    })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
