<template>
  <div>
    <h2>
      Answers
    </h2>
    <a :href="Answers[point].link" class="link" :class="'course'+point">
      <div class="title">{{Answers[point].message}}</div>
      <span class="detail">詳細はこちら</span>
    </a>
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
  text-decoration: none;
}
.link {
  display: inline-block;
  padding: 0.5em 1em;
  border: 3px solid;
  border-radius: 0.5em;
  color: #d11;
}
.detail {
  font-weight: bold;
}
.detail::after {
  content: '▶';
  display: inline-block;
}
.course0 {
  color: #4a85a2;
  border-color: #4a85a2;
}
.course1 {
  color: #6e8341;
  border-color: #6e8341;
}
.course2 {
  color: #006a8a;
  border-color: #006a8a;
}
.course3 {
  color: #9d7a3c;
  border-color: #9d7a3c;
}
.course4 {
  color: #985865;
  border-color: #985865;
}
.course5 {
  color: #9ebb4d;
  border-color: #9ebb4d;
}
</style>
