<template>
    <div class="container">
        <pdd-download></pdd-download>
        <div class="index">
            <div class="header">
                <span 
                    v-for="(title,index) in tabTitles" 
                    :key="index" 
                    @click="changeTab(index)"
                    :class="activeTab === index ? 'active' : 'default' "
                >
                    {{title}}
                </span>
            </div>
            <div class="main" v-if="activeTab == 0">
                <div class="banner">
                    <img src="https://mcdn.pinduoduo.com/home/static/images/banner_index.jpg" />
                </div>
                <div class="subject">
                    <div class="title">
                        <span class="title-text">精彩活动</span>
                        <span class="title-more">查看更多></span>
                    </div>
                    <div class="banner">
                        <img src="https://mcdn.pinduoduo.com/home/static/images/seckill.png" /> 
                    </div>           
                    <div class="banner-img">
                        <img src="https://mcdn.pinduoduo.com/home/static/images/sale.png" />
                    </div>
                    <div class="banner-img">
                        <img src="https://mcdn.pinduoduo.com/home/static/images/supermarket.png" />
                    </div>
                </div>
                <div class="subject">
                    <div class="title">
                        <span class="title-text">精彩专题</span>
                        <span class="title-more">查看更多></span>
                    </div>
                    <div class="item" v-for="(item,itemIndex) in items" :key="itemIndex">
                        <div class="banner">
                            <img :src="item.banner" /> 
                        </div>
                        <div class="banner-img-group">
                            <div class="goods" v-for="(good,goodIndex) in item.goodsData" :key="goodIndex">
                                <div v-if="goodIndex <3">
                                    <div class="goods-img">
                                        <img :src="good.thumb_url" />
                                    </div>
                                    <div class="goods-name">
                                        {{good.goods_name}}
                                    </div>
                                    <div class="goods-price">
                                        ￥<span class="new-price">{{good.group_price/100}}</span>
                                        <span class="old-price">￥{{good.market_price/100}}</span>
                                    </div>
                                </div>
                                
                            </div>
                        </div>
                    </div>
                </div>        
            </div>
        </div>
        <pdd-footer></pdd-footer>
    </div>
</template>
<script>
import HeaderPdd from "../pdd/HeaderPdd";
import FooterPdd from "../pdd/FooterPdd";
import {
    pddGoods
} from "@/api/api.js";
export default {
    name: 'HomePDD',
    data(){
        return {
            tabTitles:[
                "首页","商家入驻","帮助中心"
            ],
            activeTab: 0,
            items: [
                {
                    banner: 'https://mcdn.pinduoduo.com/home/static/images/girlclothes.jpg',
                    goodsData: []
                },{
                    banner: 'https://mcdn.pinduoduo.com/home/static/images/boyshirt.jpg',
                    goodsData: []                    
                },{
                    banner: 'https://mcdn.pinduoduo.com/home/static/images/medical.jpg',
                    goodsData: []                    
                },{
                    banner: 'https://mcdn.pinduoduo.com/home/static/images/food.jpg',
                    goodsData: [] 
                },{
                    banner: 'https://mcdn.pinduoduo.com/home/static/images/shoes.jpg',
                    goodsData: []
                },{
                    banner: 'https://mcdn.pinduoduo.com/home/static/images/home.jpg',
                    goodsData: []
                },{
                    banner: 'https://mcdn.pinduoduo.com/home/static/images/beauty_2020.jpg',
                    goodsData: []
                },{
                    banner: 'https://mcdn.pinduoduo.com/home/static/images/electric.jpg',
                    goodsData: []
                },{
                    banner: 'https://mcdn.pinduoduo.com/home/static/images/baby.jpg',
                    goodsData: []
                },{
                    banner: 'https://mcdn.pinduoduo.com/home/static/images/furniture.jpg',
                    goodsData: []
                },{
                    banner: 'https://mcdn.pinduoduo.com/home/static/images/sports.jpg',
                    goodsData: []
                }
            ]
        }
    },
    components:{
        'pdd-download':HeaderPdd,
        'pdd-footer': FooterPdd,
    },
    created(){
        this.getList();
    },
    methods:{
        changeTab(index){
            this.activeTab = index;
        },
        getList(){
            var subject_id = [5571, 5574, 22498, 5576, 5572, 5578, 5575, 5577, 5579, 5581, 5580]
            for(let i = 0; i < subject_id.length; i++){
                pddGoods({data:{
                    subject_id: subject_id[i],
                    page: 1,
                    size:10
                }}).then(res=>{
                    this.items[i].goodsData = res.data;
                    console.log(i,this.items[i].goodsData);
                })
            }
        }
    }
}
</script>
<style scoped>
    @import "../../assets/css/home.css";
    .container{
        margin-top: -60px;
        background-color: #f3f3f3;
        font-weight: 500;
    }
</style>