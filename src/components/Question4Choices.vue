<template>
  <div>
    <h2>Q. {{numQuestion}}</h2>
    <p>{{questions[currentQuestion].message}}</p>
    <ul>
      <li v-for="(choice, index) in questions[currentQuestion].choices" :key="index">
        <button @click="selectQuestion(choice)">{{choice.text}}</button>
      </li>
    </ul>

  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs, computed } from 'vue';

export default defineComponent({
  name: 'Question4Choices',
  props: {
    msg: String,
  },
  setup(props, context) {
    const state = reactive({
      questions: [
        {
          message: "次の4つから選んでください。",
          choices: [
            {
              text: "①",
              flag: false
            },
            {
              text: "②",
              flag: true
            },
            {
              text: "③",
              flag: false
            },
            {
              text: "④",
              flag: false
            },
          ]
        },
        {
          message: "次の4つから選んでください。",
          choices: [
            {
              text: "①",
              flag: true
            },
            {
              text: "②",
              flag: false
            },
            {
              text: "③",
              flag: false
            },
            {
              text: "④",
              flag: false
            },
          ]
        },
        {
          message: "次の4つから選んでください。",
          choices: [
            {
              text: "①",
              flag: false
            },
            {
              text: "②",
              flag: false
            },
            {
              text: "③",
              flag: true
            },
            {
              text: "④",
              flag: false
            },
          ]
        },
        {
          message: "次の4つから選んでください。",
          choices: [
            {
              text: "①",
              flag: false
            },
            {
              text: "②",
              flag: false
            },
            {
              text: "③",
              flag: false
            },
            {
              text: "④",
              flag: false
            },
          ]
        },
        {
          message: "次の4つから選んでください。",
          choices: [
            {
              text: "①",
              flag: true
            },
            {
              text: "②",
              flag: true
            },
            {
              text: "③",
              flag: false
            },
            {
              text: "④",
              flag: false
            },
          ]
        },
      ],
      currentQuestion:0
    });
    const numQuestion = computed(function() { return state.currentQuestion+1})
    const selectQuestion = (c:any) => {
      if(state.currentQuestion < state.questions.length - 1) {
        state.currentQuestion++;
      }
      context.emit("select-question4", c.flag);
    };
    return {
      ...toRefs(state),
      numQuestion,
      selectQuestion
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
