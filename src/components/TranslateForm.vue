<template>
  <div class="translateForm">
  	<div class="col-md-6 col-md-offset-3">
		<form @submit="formSubmit">
			<input type="text" v-model="textToTranslate" placeholder="输入需要翻译的内容"/>
			<select v-model="language">
				<option value="en">English</option>
				<option value="ru">Russian</option>
				<option value="ko">Korean</option>
				<option value="ja">Janpenese</option>
			</select>
			<input type="submit"  value="翻译" />
		</form>
		</div>
  </div>
</template>

<script>
	export default {
	  name: 'translateForm',
	  data:function(){
	  	return {
	  		textToTranslate:'',
	  		language:''
	  	}
	  },
	 	methods:{
	 		formSubmit:function(e){
	 			e.preventDefault();
	 			//alert(this.textToTranslate)
	 			this.$emit("formSubmit",this.textToTranslate,this.language)//formSubmit自己随便定义
	 		}
	 	}
	  
	}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
