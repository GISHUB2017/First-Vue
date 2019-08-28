<template>
  <!--第一课-->
  <div id="vue-app">
    <h5>属性:{{name}}</h5>
    <p>方法调用：{{loadData()}}</p>
    <a v-bind:href="website">百度一下</a>
    <div v-html="websiteTag"></div>
    <input type="text"  v-bind:placeholder='bindData'/>
  </div>
  <!--第二课-->
</template>
  <script>
  import { mapGetters } from 'vuex'
  import { mapActions } from 'vuex'
  import axios from 'axios'
  
  export default {
	  data()
	  {
		  return {
		  name:"Hello World!!!",
		  website:"https://www.baidu.com",
		  bindData:"请输入正确信息",
		  websiteTag:"<a href='https://www.baidu.com'>百度一下</a>",
	  }},
	  methods:{
			loadData:function(){
				  const Url ="http://221.0.170.174:8049/AjaxHandler.ashx?class=AjaxProjectManage&method=GetProjectActivity&ProjectID=ac3a0e8c-db84-4d5a-8320-7f1042045658";
				  return axios.get(Url).then((res) => {console.log(res+"返回值"); return res;}).catch((error) => {console.log(error.response+"错误信息");})
                // this.$http.get(url).then(function(data){
                //   console.info(data);
                //     // var json=data.body;
                //     // this.data=eval("(" + json +")");
                // },function(response){
                //     console.info(response);
				// })
				// $.get(url,function(data){
                //     _self.data=eval("(" + data +")");
                // })
				// return "这是方法测试";
			}
		}
	}
    </script>