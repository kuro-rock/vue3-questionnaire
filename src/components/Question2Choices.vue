<template>
  <div>
    <h2>Q.{{question[currentQuestion].number}}</h2>
    <p>{{question[currentQuestion].message}}</p>
    <ul>
      <li v-for="(choice,index) in question[currentQuestion].choices" :key="index">
        <button @click="selectQuestion(choice.point)">{{choice.text}}</button>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs } from 'vue';

export default defineComponent({
  name: 'Question2Choices',
  props: {
    hasTrue: Boolean,
  },
  setup(props, context) {
    const state = reactive({
      question: [
        {
          number: "6",
          message: "利用するか",
          choices: [
            {
              text: "Yes",
              point: 0
            },
            {
              text: "No",
              point: 1
            },
          ]
        },
        {
          number: "7",
          message: "世界か日本か",
          choices: [
            {
              text: "A",
              point: 0
            },
            {
              text: "B",
              point: 1
            },
          ]
        },
        {
          number: "7",
          message: "中小か",
          choices: [
            {
              text: "Yes",
              point: 0
            },
            {
              text: "No",
              point: 1
            },
          ]
        },
      ],
      currentQuestion: 0
    });
    const selectQuestion = (p:number) => {
      let point;
      let isComplete;
      if (!props.hasTrue && state.currentQuestion === 0){
        point = p * 2 + 2;
        state.currentQuestion += (p + 1);
        isComplete = false;
      } else {
        point = p;
        isComplete = true;
      }

      context.emit("select-question2", {
        point: point,
        isComplete: isComplete
      });
    };
    return {
      ...toRefs(state),
      selectQuestion
    }
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
button {
  padding: 0.25em 1em;
  border: solid 1px #999;
  border-radius: 0.125em;
  background: #fff;
}

</style>
