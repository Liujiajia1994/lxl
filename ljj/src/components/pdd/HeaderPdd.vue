<template>
    <div class="download">
        <div class="logo">
            <img src="https://mcdn.pinduoduo.com/home/static/images/logo.png" />
            <span>0.1元包邮抢16包清风面巾纸</span>
            <button>前往购买</button>
        </div>
    </div>
</template>
<script>
export default {
    name: 'HeaderPdd',
    data(){
        return {
            
        }
    },
}
</script>
<style scoped>
    .logo{
        width: 100%;
        height: 90px;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-around;
        background-color: #ed2632;
    }
    .logo img{
        width: 190px;
        height: 60px;
    }
    .logo span{
        font-size: 26px;
        color: #fff;
    }
    .logo button{
        height: 56px;
        display: inline-block;
        border-radius: 10px;
        font-size: 28px;
        background-color: white;
        color: #ed2632;
    }
</style>
