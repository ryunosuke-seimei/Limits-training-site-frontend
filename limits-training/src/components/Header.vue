<template>
    <header id="header">
        <div class="title">
            <router-link to="/">{{title}}</router-link>
        </div>
        <div class="sub-links" v-show="pc_or_mobile_show">
            <router-link to="/item">item</router-link>
            <router-link to="/roulette">roulette</router-link>
        </div>
        <div class="sub-box" v-show="!pc_or_mobile_show" v-on:click="clickSubBox" v-bind:class="{ box_active: box_open_flag}">
        <li></li>
        <li></li>
        <li></li>
        </div>
        <div class="sub-bords" v-show="!pc_or_mobile_show" v-bind:class="{ bords_active: box_open_flag}">
            <router-link to="/item">item</router-link>
            <router-link to="/roulette">roulette</router-link>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',
    components: {
    },
    data(){
        return{
            pc_or_mobile_show: true,
            box_open_flag: false,
        }
    },
    computed:{
        title(){
            return this.$store.state.title
        }
    },
    mounted:function(){
        window.addEventListener('resize', this.resizeEventCalculate);
        this.resizeEventCalculate();
    },
    destroyed: function () {
        window.removeEventListener('resize', this.resizeEventCalculate);
    },
    methods:{
        resizeEventCalculate: function(){
            let flag = window.innerWidth > 500 ? true : false;
            this.pc_or_mobile_show = flag;
        },
        clickSubBox: function(){
            this.box_open_flag = !this.box_open_flag;
            console.log(this.box_open_flag);
        }
    }

}
</script>

<style>
header{
  position: relative;
  display: inline-flex;
  width: 100%;
  height: 60px;
  background-color: rgba(240, 230, 140, 0.5);
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
}
header .title{
  display: inline-flex;
  width: 120px;
  height: 100%;
  justify-content: center;
  align-items: center;
}

header .sub-links{
  display: inline-flex;
  width: 300px;
  height: 100%;
  justify-content: space-around;
  align-items: center;
  list-style: none;
}
header .sub-links li{
  display: inline-flex;
  width: 120px;
  height: 90%;;
  justify-content: center;
  align-items: center;
}

header .sub-box{
  position: relative;
  display: inline-block;
  box-sizing: content-box;
  width: 40px;
  margin: 10px;
  height: calc(100% - 20px);
}
header .sub-box li{
  list-style: none;
  position: absolute;
  width: 100%;
  height: 4px;
  background-color: black;
  transition: 1s;
}
.sub-box li:nth-child(1){
  top: calc(50% - 10px);
}
.sub-box li:nth-child(2){
  top: calc(50% - 2px);
}
.sub-box li:nth-child(3){
  top: calc(50% + 6px);
}

.box_active li:nth-child(1){
  top: calc(50% - 2px);
  transform: rotateZ(45deg);
}
.box_active li:nth-child(2){
  opacity: 0;
}
.box_active li:nth-child(3){
  top: calc(50% - 2px);
  transform: rotateZ(135deg);
}
.sub-bords{
  display: inline-flex;
  flex-direction: column;

  justify-content: space-around;
  align-items: center;

  left: -100%;
  top: 60px;
  position: absolute;
  width: 100%;
  height: calc(100vh - 60px);
  background-color: rgba(240, 230, 140, 0.9);
  transition: 1s;
}
.sub-bords li{
  list-style: none;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  width: 300px;
  height: 100px;

  border-radius: 15%;
  box-shadow: 1px 1px 1px black;
  background-color: rgba(240, 230, 140, 0.9);

}
.bords_active{
  left: 0;
}
</style>