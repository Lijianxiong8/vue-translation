<template>
    <div class="row" id="translateForm">
        <div class="col-md-6 col-md-offset-3">
            <form id="translateform" class="jumbotron form-inline" v-on:submit="formSubmit">
                <input class="form-control" type="text" placeholder="输入需要翻译的内容" v-model="textToTranslate">
                <select class="form-control" v-model="language">
                    <option value="en">English</option>
                    <option value="ja">Japanse</option>
                    <option value="fr">French</option>
                    <option value="es">Spanish</option>
                    <option value="de">German</option>
                    <option value="el">Greek</option>
                    <option value="it">Italian</option>
                    <option value="ko">Korean</option>
                </select>
                <input class="btn btn-primary" type="submit" value="翻译">
            </form>
        </div>
    </div>
</template>

<script>
export default {
    name:"translateForm",
    // data:function () {},
    data(){
        return {
            textToTranslate:"",
            language:""
        }
    },
    methods:{
        // formSubmit:function(){ }
        formSubmit(e){
            // alert(this.textToTranslate);
            this.$emit("formSubmit",this.textToTranslate,this.language);
            e.preventDefault();
        }
    },
    created:function(){
        this.language = "en";
    }
}
</script>

<style scoped>
form#translateform {
    margin:0 25%;
    text-align: center;
    border:1px #ccc solid; 
    border-radius: 10px;
}
</style>