<template>
  <div>
    <h2>
      Answers
    </h2>
    <p>{{Answers[point].message}}</p>
    <a :href="Answers[point].link">詳細はこちら</a>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs } from 'vue';

export default defineComponent({
  name: 'Answers',
  props: {
    point: Number,
  },
  setup() {
    const state = reactive({
      Answers: [
        {
          message: "あなたへのおすすめはAタイプです",
          link: "https://example.com/"
        },
        {
          message: "あなたへのおすすめはBタイプです",
          link: "https://example.com/"
        },
        {
          message: "あなたへのおすすめはCタイプです",
          link: "https://example.com/"
        },
        {
          message: "あなたへのおすすめはDタイプです",
          link: "https://example.com/"
        },
        {
          message: "あなたへのおすすめはEタイプです",
          link: "https://example.com/"
        },
        {
          message: "あなたへのおすすめはFタイプです",
          link: "https://example.com/"
        },
      ]
    });
    return {
      ...toRefs(state)
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
