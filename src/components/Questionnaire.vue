<template>
  <div>
    <Question4Choices v-show="showQuestion4" @select-question4="selectQuestion4"/>
    <Question2Choices v-show="!showQuestion4&&!showAnswer" :hasTrue="hasTrue" @select-question2="selectQuestion2"/>
    <Answers v-show="showAnswer" :point="selectedQuestion2.point"/>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs, computed } from 'vue';
import Question4Choices from '@/components/Question4Choices.vue';
import Question2Choices from '@/components/Question2Choices.vue';
import Answers from '@/components/Answers.vue';

interface QuestionnaireState {
      selectedQuestion4: Array<any>,
      selectedQuestion2: any
    }

export default defineComponent({
  name: 'Questionnaire',
  components: {
    Question4Choices,
    Question2Choices,
    Answers
  },
  setup() {

    const state = reactive<QuestionnaireState>({
      selectedQuestion4: [],
      selectedQuestion2: {
        point: 0,
        isComplete: false
      }
    });

    const showQuestion4 = computed(function() { return state.selectedQuestion4.length < 5})
    const hasTrue = computed(function() { return state.selectedQuestion4.includes(true)})
    const showAnswer = computed(function() { return state.selectedQuestion2.isComplete})
    
    function selectQuestion4(q: any) {
      state.selectedQuestion4.push(q);
    }

    function selectQuestion2(q: any) {
      state.selectedQuestion2.point += q.point;
      state.selectedQuestion2.isComplete = q.isComplete;
    }

    return {
      ...toRefs(state),
      showQuestion4,
      hasTrue,
      showAnswer,
      selectQuestion4,
      selectQuestion2
    }
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
