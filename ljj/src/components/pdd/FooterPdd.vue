<template>
    <div class="footer">
        <div class="divider"></div>
        <span>版权所有：上海寻梦信息技术有限公司</span>
        <span>(增值电信业务经营许可证：沪B2-20170215)</span>
    </div>
</template>
<script>
export default {
    name: 'FooterPdd',
    data() {
        return {

        }
    },
}
</script>
<style scoped>
    .footer{
        margin-top: 40px;
        padding: 40px 40px 0;
        background-color: white;
    }
    .footer span{
        display: block;
        height: 60px;
        line-height: 60px;
        text-align: center;
        font-size: 24px;
        color: #7a7a7a
    }
    .divider{
        height: .13px;
        border-top: 1px solid #d6d6d6;
        transform: scaleY(.5);
    }
</style>