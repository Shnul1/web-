<template>
    <div class="nav">
        <div class="left"></div>
        <div class="right">
            <li><a href="#">申请使用</a></li>
            <li><a href="#">官网</a></li>
            <li><a href="#">周边</a></li>
            <li><a href="#">帮助</a></li>
            <li><a href="#">公众号</a></li>
        </div>
    </div>
</template>


<script>
    export default {
    name: 'LoginNav'
    };
</script>


<style>
   .nav{
        display: flex;
        justify-content: space-between;
        width: 1000px;
        height: 60px;
        margin: auto;
    }

    .nav .left{
        width: 160px;
        background-image: url("https://cdn.schoolpal.cn/schoolpal/resource/ci/SchoolPal-NETCore-PC/130/common/images/icon-loginlogo-new.jpg?version=20201022223932");
        background-repeat: no-repeat;
        background-size: contain;
        background-position: center;
    }


    .nav .right{
        display: flex;
    }

    .nav .right li{
        display: flex;
        justify-content: center;
        align-items: center;
        list-style: none;
        position: relative;
    }

    .nav .right li a{
        font-size: 16px;
        text-decoration: none;
        display: block;
        width: 80px;
        text-align: center;
        font-weight: bold;
        color: black;
    }

    .nav .right li::after{
        transition: width 2s;
        display: block;
        content:'';
        width: 40px;
        height: 4px;
        border-radius: 4px;
        background-color: #007AFF;
        bottom: 0px;
        position: absolute;
        margin:0 auto;
        visibility: hidden;
    }

    .nav .right li:hover::after{
        visibility: visible;
    }
</style>