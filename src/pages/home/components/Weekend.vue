<template>
    <div>
       <div class="title">
           <img class="title-img" src="http://img1.qunarzz.com/piao/fusion/1711/16/bfbb9874e8f11402.png" alt="">
           周末去哪儿</div>
           <ul>
               <li class="item border-bottom" 
               v-for="item of list" :key='item.id'>
                   <div class="item-img-wrapper">
                       <img class="item-img" :src='item.imgUrl'
                        >
                   </div>
                   <div class="item-info">
                       <p class="item-title">{{item.title}}</p>
                       <p class="item-desc">{{item.desc}}</p>
                   </div>
               </li>
           </ul>
    </div>
</template>
<script>
export default {
    name:'Weekend',
    props:{
        list:Array
    },  
}
</script>
<style lang="stylus" scoped>
@import '~styles/mixins.styl'
.title
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
.item-img-wrapper
    overflow :hidden
    height:0
    padding-bottom:37.09%
    .item-img
        width:100%
    
.item-info
    padding :.1rem
    .item-title
        line-height :.54rem
        font-size :.32rem
        ellipsis()
    .item-desc
        line-height :.4rem
        color #ccc
        width: 300px
        ellipsis()

</style>
