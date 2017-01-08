<template>
    <div>
        <div :class="{pageSlideAnimate:toAnimate,pageSlideBackAnimate:toBackAnimate}" style="width:100%">
            <navBar v-on:toggleMenu="toggleMenu"></navBar>
            <router-view></router-view>
            <div class="footer">COPYRIGHT © 寅虎茶文化</div>
        </div>
        <div :class="{menuSlideAnimate:toAnimate,menuSlideBackAnimate:toBackAnimate}" :style="slideMenuContainerStyle">
            <slideMenu v-on:toggleMenu="toggleMenu"></slideMenu>
        </div>
        <!--当左侧菜单显示时，要点击右侧区域隐藏菜单，需要在右边区域增加一层遮罩层，然后把右侧点击事件绑定在遮罩层上，达到调用toggleMenu方法的目的-->
        <div class="clickLayer" @click="toggleMenu" v-show="toAnimate"></div>
    </div>
</template>
<script>
    import SlideMenu from  '../components/SlideMenu'
    import NavBar from '../components/NavBar'
    export default {
        name:'slideNav',
        data:function(){
            return {
                slideMenuContainerStyle:{
                    height:'100%',
                    width:'100%',
                    marginLeft:'-70%',
                    position:'absolute',
                    top:0
                },
                toAnimate:false,
                toBackAnimate:false
            }
        },
        components:{
            NavBar,
            SlideMenu
        },
        methods:{
            toggleMenu:function(){
                this.toAnimate=!this.toAnimate;
                this.toBackAnimate=!this.toAnimate;
                this.slideMenuContainerStyle.marginLeft=this.toAnimate ? '0%':'-70%';
            }
        },
        mounted:function(){
            var height=document.documentElement.clientHeight;
            var width=document.documentElement.clientWidth;
            this.slideMenuContainerStyle.height=height+'px';
            this.slideMenuContainerStyle.width=width*0.7+'px';
        }
    }
</script>
<style scoped>
    .menuSlideAnimate{
        transition: margin-left 400ms;
        -moz-transition: margin-left 400ms; /* Firefox 4 */
        -webkit-transition: margin-left 400ms; /* Safari 和 Chrome */
        -o-transition: margin-left 400ms; /* Opera */
        animation-fill-mode:forwards;
        
    }
    .menuSlideBackAnimate{
        transition: margin-left 400ms;
        -moz-transition: margin-left 400ms; 
        -webkit-transition: margin-left 400ms; 
        -o-transition: margin-left 400ms; 
        animation-fill-mode:forwards;
    }

    .pageSlideAnimate{
        margin-left:70%;
        transition: margin-left 400ms;
        -moz-transition: margin-left 400ms; /* Firefox 4 */
        -webkit-transition: margin-left 400ms; /* Safari 和 Chrome */
        -o-transition: margin-left 400ms; /* Opera */
        animation-fill-mode:forwards;
    }
    .pageSlideBackAnimate{
        margin-left:0%;
        transition: margin-left 400ms;
        -moz-transition: margin-left 400ms; /* Firefox 4 */
        -webkit-transition: margin-left 400ms; /* Safari 和 Chrome */
        -o-transition: margin-left 400ms; /* Opera */
        animation-fill-mode:forwards;
    }
    .clickLayer{
        height: 100%;
        width:30%;
        position:absolute;
        top:0;
        left:70%;
    }
    .footer{
        height:100px;
        width:100%;
        border-top:1px solid rgb(246,246,246);
        border-bottom:1px solid rgb(246,246,246);
        background: rgb(250,250,250);
        line-height: 100px;
        text-align: center;
        font-size:30px;
        color:rgb(103,103,103);
        position:fixed;
        bottom:0;
    }
</style>