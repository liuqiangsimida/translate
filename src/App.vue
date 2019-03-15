<template>
	  <div id="app">
	  	<h1>在线翻译</h1>
	  	<h5 class="text-muted">简单/易用/便捷</h5>
	    <translateForm @formSubmit="translateText"></translateForm>
	    <!--translateText自己随便定义formSubmit与TranslateForm定义的一至-->
	    <translateOutput v-text="translatedText"></translateOutput>
	  </div>
</template>

<script>
	import TranslateForm from './components/TranslateForm'
	import TranslateOutput from './components/TranslateOutput'
	export default {
	  name: 'App',
	  data:function(){
	  	return {
	  		translatedText:''
	  	}
	  },
	  components:{
	  	TranslateForm,
	  	TranslateOutput
	  },
	  methods:{
	  	translateText:function(text,language){//translateText与上面一至
	  		this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190315T033021Z.0f981d353dec0891.aaa9ac363fd6d88933c02456a15b66e3c7967350&&lang='+language+'&text='+text)
	  		.then((response)=>{
	  			console.log(response)
	  			this.translatedText=response.body.text[0]
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
