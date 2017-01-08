<template>
    <div class="titleBar">
        <div class="barContainer">
            <div>
                <img id="menuBtn" src="../../static/img/menu.png" @click="toggleMenu"/>
                <img class="productLogo" src="../../static/img/logo2.png"/>
            </div>
        </div>
    </div>
</template>
<script>
    var NavBar={
        name:'navBar',
        methods:{
            toggleMenu:function(){
                this.$emit('toggleMenu');
            }
        }
    }
    export default NavBar
</script>

<style scoped>
    .titleBar{
        height:150px;
        width:100%;
        position: relative;
        left:0;
        top:0;
        background: #fff;
    }
    .barContainer{
        display: table;
        vertical-align: middle;
        width:100%;
        height:100%;

    }
    .barContainer > div{
        display: table-cell;
        vertical-align: middle;
        width:100%;
    }
    #menuBtn{        
        position:absolute;
        width:6.7%;
        left:20px;
        top:35%;
    }
    .productLogo{
        width:28%;
    }
</style>