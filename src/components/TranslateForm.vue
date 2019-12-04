<template>
  <div id="translateForm" >
      <form action="" v-on:submit="formSubmit" class="form-group transform" >
        <input type="text" placeholder="输入需要翻译的内容"  class="form-control transInput" id="transInput" v-model="textToTranslate">
        <select name="" id="" v-model="language" class="form-control transSelect" >
            <option value="en">English</option>
            <option value="ko">Korean</option>
            <option value="zh">Chinese</option>
            <option value="es">Spanish</option>
            <option value="it">Italian</option>
            <option value="la">Latin</option>
        </select>
        <input type="submit"  class="btn btn-primary transbtn" value="翻译">
      </form>

  </div>
</template>

<script>
export default {
    name:'translateForm',
    data:function(){
        return {
            textToTranslate:"",
            language:"",
        }
    },
    methods:{
        // emit 解决子组件向父组件传值的问题
        // 流程：点击提交按钮，触发子组件的formSubmit 
        // 发射fmsubmit事件，这也就是父组件中监听的事件
        // 第二个参数就是传的值


        formSubmit:function(e){
            // alert(this.textToTranslate);
            // 发射的事件就是父组件所监听事件
            this.$emit("fmSubmit",this.textToTranslate,this.language);
            // 取消默认事件,点击提交按钮不会刷新当前页面了
            e.preventDefault();
            
        }
    },
    // 设置默认语言
    created:function(){
        this.language="en"
    }
}
</script>

<style scoped>
  #translateForm{
      margin:0px;
  }
  .transform{
      margin-top:30px;
      width:500px;
      height:100px;
      display:flex;
  }
  .transbtn{
      height:40px;
      width:150px;
      }
  .transSelect{
      width:100px;
      margin:0px 10px;
      border:none;
      border-bottom: 1px solid rgb(206,212,218);
      border-radius: 0;
      }
  .transInput{
      border:none;
      border-bottom: 1px solid rgb(206,212,218);
      border-radius: 0;}
  .form-control{
      outline: none;
  }

</style>
