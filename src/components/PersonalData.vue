<template>
  <transition name="slide-fade">
    <article v-show="isShowpersona">
      <h1>
        <span class="fa fa-angle-left" ></span>
        个人资料修改
      </h1>
      <form action="">
        <div>
          <label>昵称</label>
          <input type="text" placeholder="热巴">
        </div>
        <div>
          <label>E-mail</label>
          <input type="text" placeholder="请填写你的安全邮箱">
        </div>
        <div class="gender">
          <label>性别</label>
          <span :class="{'color-lgtgreen':menShow}" @click="maleSwitch">男</span>
          <span :class="{'color-lgtgreen':womenShow}" @click="femaleSwitch">女</span>
          <span :class="{'color-lgtgreen':secrecy}" @click="secrecys">保密</span>
        </div>
        <div>
          <label>生日</label>
          <input type="date" class="birthday">
        </div>
        <div>
          <label>身份证号</label>
          <input type="text" placeholder="请输入您的18位身份证号" >
        </div>
        <div class="version">
          <label >个人描述</label>
          <textarea type="text" placeholder="请谈谈你对自己的认识"></textarea>
        </div>
        <button type="button" class="modify" @click="$emit('personbtn')">确认</button>
      </form>
      <section class="popup" v-if="personshows">
        <div>
          <p>个人资料修改成功!</p>
          <p type="button" @click="$emit('personHides')">确定</p>
        </div>
      </section>
    </article>
  </transition>

</template>

<script>
export default {
  name: 'personal',
  props:['isShowpersona','personshows'],
  data () {
    return {
      msg: '首页',
	  menShow:false,
	  womenShow:false,
	  secrecy:true
    }
},
methods:{
	maleSwitch(){
		this.menShow = true;
	    this.womenShow = false;
	    this.secrecy = false
	},
	femaleSwitch(){
		this.menShow = false;
		this.womenShow = true;
		this.secrecy = false
	},
	secrecys(){
		this.menShow = false;
		this.womenShow = false;
		this.secrecy = true
	}
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
  @import "../styles/personalData.less";
</style>
