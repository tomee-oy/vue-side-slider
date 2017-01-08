<template>
    <div class="slideMenuContainer">
        <div class="menuItem">
            <div>
                <img src="../../static/img/logo3.png"/>
            </div>
        </div>
        <div v-for="(item,index) in menus" class="menuItem" @click="menuClick($event,index)" :class="{beClickedStyle:menus[index].isClicked}">
            {{item.title}}
        </div>

    </div>
</template>
<script>
    import router from '../routers.js'
    export default {
        name:'slideMenu',
        data:function(){
            return {
                menus:[
                    {title:'首页',isClicked:false},
                    {title:'茶叶',isClicked:false},
                    {title:'品茶',isClicked:false},
                    {title:'关于',isClicked:false},
                    {title:'联系',isClicked:false}
                ]
            }
        },
        methods: {
            menuClick:function(event,index){
                var length=this.menus.length;
                for(var i=0;i<length;i++){
                    if(i==index){
                        this.menus[i].isClicked=true;
                    }else{
                        this.menus[i].isClicked=false;
                    }
                }
                this.$emit('toggleMenu');
                switch(index){
                    case 0:
                        router.push({path:'/'});
                        break;
                    case 1:
                        router.push({path:'/index/product'});
                        break;
                    case 2:
                        router.push({path:'/index/teaCulture'});
                        break;
                    case 3:
                        router.push({path:'/index/about-us'});
                        break;
                    default:
                        router.push({path:'/index/contact'});
                        break;
                }
            }
        }
    }
</script>
<style scoped>
    .slideMenuContainer{
        background-color: rgb(24,24,24);
        height:100%;
    }
    .menuItem{
        text-align: center;
        font-size:40px;
        height:130px;
        line-height: 130px;
        color:#fff;
        border-bottom:1px solid rgb(35,35,35);
    }
    .menuItem:nth-child(1) > div{
        width: 100%;
        height: 100%;
        display: table;
        vertical-align: middle;
    }
    .menuItem:nth-child(1) img{
        vertical-align: middle;
        margin:0 auto;
    }
    .beClickedStyle{
        background:rgb(13,13,13);
        border-left:8px solid red;
    }
</style>