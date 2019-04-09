<template>
    <div>
      <home-header ></home-header>
      <home-swiper :list="swiperList"></home-swiper>
      <home-icon :list="iconList"></home-icon>
      <recommend :list="recommendList"></recommend>
      <Weekend :list="weekendList"></Weekend>
    </div>
</template>>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcon from './components/Icons'
import Recommend from './components/Recommend'
import Weekend from './components/Weekend'
import axios from 'axios'
import {mapState} from 'vuex'
export default {
    name:'Home',
    components:{
        HomeHeader,
        HomeSwiper,
        HomeIcon,
        Recommend,
        Weekend   
    },
    data (){
        return {
            swiperList:[],
            iconList:[],
            recommendList:[],
            weekendList:[],
            lastCity:''
        }
    },
    computed:{
        ...mapState(['city'])
    },
    methods:{
        getHomeInfo(){
            axios.get('/api/index.json?city='+this.city)
                .then(this.getHomeInfoSucc)
        },
        getHomeInfoSucc(res){
            res=res.data
            if(res.ret && res.data){
                const data = res.data
                this.swiperList=data.swiperList
                this.iconList=data.iconList
                this.recommendList=data.recommendList
                this.weekendList=data.weekendList
            }
            console.log(res)
            
        }
    },
    mounted(){
        this.lastCity =this.city
        this.getHomeInfo()
    },
    activated(){
        //点击不同的城市获取不同的数据
        if(this.lastCity !== this.city){
            this.lastCity = this.city
            this.getHomeInfo()
        }
    }
}
</script>

<style >

</style>
