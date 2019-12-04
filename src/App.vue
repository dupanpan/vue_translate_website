<template>
<div class="app">
  <h1>在线翻译</h1>

  <h5>简单 / 易用 / 便捷</h5>
  <translateForm v-on:fmSubmit="translateText"></translateForm>
  <!-- 要和translateOutput组件的id一致 -->
   <translateOutput v-bind:translatedText='translatedText'></translateOutput>
    <!-- <translateOutput></translateOutput> -->
</div>
  
</template>
d
<script>
import translateForm from './components/TranslateForm'
import translateOutput from './components/TranslateOutput'
export default {
  name: 'App',
  data:function(){
    return{
      translatedText:""
    }
  },
  components:{
    translateForm,
    translateOutput

  },
  methods:{
    translateText:function(text,language){
      // alert(text);
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20191204T014312Z.7b48f083d486db92.059d80bf532282fb755110a047691a7ee971f12f&lang='+language+'&text='+text)
      .then((response)=>{
       this.translatedText=response.body.text[0];
      //  console.log(this.translatedText);
      })
   }
  }
}
</script>

<style >
  div{
        width:500px;
        height:100px;
        margin:30px auto;
        text-align:center;

    }
    h5{
      color:#aaa;
      font-size:16px;
    }
</style>
