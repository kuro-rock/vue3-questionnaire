<template>
  <div>
    <h2>Q. {{numQuestion}}</h2>
    <p>{{questions[currentQuestion].message}}</p>
    <ul>
      <li v-for="(choice, index) in questions[currentQuestion].choices" :key="index">
        <button @click="selectQuestion(choice)" :class="{fillColor: choice.flag}">
          {{choice.text}}
        </button>
      </li>
    </ul>

  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs, computed } from 'vue';

export default defineComponent({
  name: 'Question4Choices',
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
              flag: false
            },
            {
              text: "④",
              flag: true
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
.fillColor {
  background: #faa;
  color: #fff;
}
</style>
