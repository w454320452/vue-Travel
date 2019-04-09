<template>
    <div>
       <div class="title">
           <img class="title-img" src="http://img1.qunarzz.com/piao/fusion/1711/16/bfbb9874e8f11402.png" alt="">
           热销推荐</div>
           <ul>
               <router-link tag="li" :to="'/detail/' + item.id"
               class="item border-bottom" 
               v-for="item of list" 
               :key='item.id'>
                   <div class="item-img-wrapper">
                       <img class="item-img" :src='item.imgUrl'
                        >
                   </div>
                   <div class="item-info">
                       <p class="item-title">{{item.title}}</p>
                       <p class="item-desc">{{item.desc}}</p>
                       <button class="item-butto">查看详细</button>
                   </div>
               </router-link>
           </ul>
    </div>
</template>
<script>
export default {
    name:'Recommend',
    props:{
        list:Array
    },
          
    }
</script>
<style lang="stylus" scoped>
@import '~styles/mixins.styl'
.title
    margin-top :.2rem
    background :#eee
    line-height :.8rem
    text-indent:.2rem
    .title-img
        display :inline-block
        overflow :hidden
        width:.3rem
        height :.3rem
        vertical-align :text-bottom
        margin-top :10px
.item
    overflow :hidden
    display :flex
    height :1.9rem
    .item-img
        width :1.7rem
        height :1.7rem
        padding :.1rem
    .item-info
        flex:1
        padding :.1rem
        min-width :0
        .item-title
            line-height :.54rem
            font-size :.32rem
            ellipsis()
        .item-desc
            line-height :.4rem
            color #ccc
            ellipsis()
        .item-butto
            width: 120px;
            line-height :.44rem
            margin-top :.16rem
            background:#ff9300
            padding :0.05rem
            border-radius:0.6rem
            color :#fff
    

</style>
