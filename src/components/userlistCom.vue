<template>
    <div>
        <ul id="useritems">
            <li v-for="(item, index) in userlist" :key="index" @click="chooseuser(item, index)" 
            :class="{current:index===currentIndex}">
                <img :src="item.headImg">
                <div class="text">
                    <div class="listname">
                        {{ item.username }}
                    </div>
                    <div class="lastestmessage">
                      这里会显示最后一条聊天记录
                    </div>
                </div>
            </li>

        </ul>
    </div>
</template>

<script>
export default {
    data() {
        return {
            currentIndex:-1,
        }
    },
    props:["userlist"],
    methods: {
        chooseuser:function(item,index){
            this.currentIndex = index
            this.$emit("chooseuser",item)
        }
    },
}
</script>

<style scoped>
    li{
        width: 250px;
        height: 48px;
        padding-top: 10px;
        padding-bottom: 10px;
    }
    li img{
        border-radius: 3px;
        margin-left: 12px;
        float: left;
        width: 48px;
    }
    .text{
        margin-left: 10px;
        display: inline-block;
        float: left;
    }
    .text .listname{
        font-size: 18px;
    }
    .text .lastestmessage{
        margin-top: 5px;
        font-size: 8px;
        color: #999;
    }
    .current{
        background-color: #c4c5c6;
    }
</style>