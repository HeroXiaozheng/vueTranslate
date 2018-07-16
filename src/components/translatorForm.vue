<template>
	<div id="translatorForm" class="row">
		<div class="col-md-6 col-md-offset-3">
			<form v-on:submit="translate" class="well form-inline" id="transform">
				<input class="form-control"
				type="text" placeholder="请输入文本" v-model="translateText">
				<select v-model="language" class="form-control">
					<option value="en">英语</option>
					<option value="fr">法语</option>
					<option value="ko">韩语</option>
					<option value="ja">日语</option>
				</select>
				<input type="submit" value="翻译" class="btn btn-primary">
			</form>
		</div>
	</div>
</template>
<script>
	export default{
		name:"translatorForm",
		data(){
			return {
				translateText:"",
				language:"en"
			}
		},
		methods:{
			translate:function(e) {
				// alert(this.translateText);
				this.$emit("translate",this.translateText,this.language);
				e.preventDefault();
			}
		}

	}
</script>
<style>
	#translatorForm{
		margin-left: 500px;
	}
	#transform{
		border: 1px solid #ccc;
		border-radius: 10px;
	}
</style>