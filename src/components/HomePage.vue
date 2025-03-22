<template>

  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
  </head>

  <body>
    <h1 :class="title">标题待定<img src="" alt=""></h1>
    <SearchBox />
    <div class="shortcut">
      <a class="cut" href="https://www.bilibili.com/"><img width="17%" src="@/assets/bilibili.ico" alt=""></a>
      <a class="cut" href=""><img src="" alt=""></a>
      <a class="cut" href=""></a>
      <a class="cut" href=""></a>
    </div>
  </body>

</template>

<style>
@import'@/assets/HomePage.css';
</style>

<script>
import SearchBox from './SearchBox.vue';

export default {
  name: 'HomePage',

  components: {
    SearchBox
  },

  props: {
    msg: String
  },

  data() {
    return {
      title: "title",
    }
  },

  methods: {
  }

}
</script>
