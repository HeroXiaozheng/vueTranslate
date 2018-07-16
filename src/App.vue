<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单 / 易用 / 快捷</h5>
    <translatorForm v-on:translate="translateText"></translatorForm>
    <translatorResult v-text="result"></translatorResult>
  </div>
</template>

<script>
import translatorForm from './components/translatorForm'
import translatorResult from './components/translatorResult'

export default {
  name: 'App',
  data(){
    return {
      result:""
    }
  },
  components: {
    translatorForm,translatorResult
  },
  methods:{
    translateText:function(text,lang) {
      // alert(text);
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180716T012751Z.923d77ace532723b.8cfd51873339aaa9f3b942918c27fe51cf05977d&lang='+lang+'&text='+text)
          .then((response)=>{
            // console.log(response.body.text[0]);
            this.result=response.body.text[0];
          })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
