<template>
        <common-nav-bar>
            <template #left>
                <img src="~assets/img/common/back.svg" alt="" @click="goBack">
            </template>
            <template #middle>
                <ul class="nav-bar-title">
                    <li
                            v-for="(item,index) in titles"
                            :key="index"
                            :class='{active:currentIndex===index}'
                            @click="handleClick(index)"
                    >{{item}}</li>
                </ul>
            </template>
        </common-nav-bar>
</template>

<script>
    export default {
        name: "DetailNavBar",
        data(){
            return{
                titles:['商品','参数','评论','推荐'],
                currentIndex:0
            }
        },
        methods:{
            goBack(){
                this.$router.go(-1)
            },
            handleClick(index){
                this.currentIndex = index
                this.$emit('itemClick',index)
            }
        }
    }
</script>

<style scoped lang="less">
    @import '~assets/css/varible.less';
    .nav-bar-title{
        display:flex;
        font-size: 14px;
        li{
            flex:1;
        }
    }
    .active{
        color:@hightTextColor;
        font-weight: bold;
        font-size:16px;
    }
    img{
        margin-top:12px;
        width: 20px;
    }

</style>
