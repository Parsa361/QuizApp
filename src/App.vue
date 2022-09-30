<template>
  <div>
    <HeaderSection />
    <ContentSection v-if="questionList.length" :cQuestion="questionList[index]" :next="next" :increment="increment" :correctCount="correctCount" :totalCount="totalCount" :index="index" />

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
      correctCount: 0,
      totalCount: 0,

    }
  },
  methods: {
    next() {
      if (this.index < 10) {
        this.index++;
      }
    },
    increment(is_correct) {
      if (is_correct) {
        this.correctCount ++;
      }
      this.totalCount ++;
    }
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