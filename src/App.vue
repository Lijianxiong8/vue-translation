<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单 / 易用 / 便捷</h5>
    <translateForm v-on:formSubmit="translateText"></translateForm>

    <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm.vue'
import TranslateOutput from './components/TranslateOutput.vue'

export default {
  name: 'app',
  // data:function(){}
  data(){
    return {
      translatedText:""
    }
  },
  components: {
    // translateForm:TranslateForm
    TranslateForm,TranslateOutput
  },
  methods:{
    translateText(text,language){
      // alert(text);
      // 安装vue-resource后，可以使用http请求接口
      // TranslateForm.vue传递过来的数据textToTranslate根据形参text传递进来，所以textToTranslate对应形参text，我之前写textToTranslate是错的，因为根本没有textToTranslate
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190810T150415Z.0e925aa57229dddb.1ebdaa5860a86084d4e56b55ad576b393f81b095&text='+ text +'&lang='+language).then((response)=>{
        // console.log(response);
        // text:["a"],text[0]="a"
        // console.log(response.body.text[0]);
        this.translatedText = response.body.text[0];
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
