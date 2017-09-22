<template>
    <div style="flex-direction: column">
        <div class="hello">
            <div class="title1" v-for="(msg,index) in message" @click="selecttile(msg )">
                <text :class="[sindex===msg.index?selectclass:defclass]">{{msg.name}}</text>
            </div>
        </div>
        <div style="flex: 1">
            <slider :value="val" :style="mStyle(value,index)" interval="4500" @change="onchange">

                //web、无法渲染
                <!--<embed-->
                <!--:style="{ visibility: item.visibility }"-->
                <!--v-for="(item,index) in message"-->
                <!--:key="index"-->
                <!--:src="item.src"-->
                <!--type="weex">-->
                <!--</embed>-->


                <div
                        v-for="(item,index) in message"
                        :style="{ visibility: item.visibility }"
                >
                    <text1 v-if="val===sindexweb1"></text1>
                    <text2 v-if="val===sindexweb2"></text2>
                    <text3 v-if="val===sindexweb3"></text3>
                </div>

            </slider>
        </div>
    </div>

</template>

<script>
    import text1 from "./text1.vue"
    import text2 from "./text2.vue"
    import text3 from "./text3.vue"
    //    var modal = weex.requireModule('modal')
    export default {
        props: {
            message: {default: []},
            selectedColor: {default: '#2d9fff'},
            unselectedColor: {default: '#000000'}
        },
        name: 'hello',
        data () {
            return {
                sindexweb1: 0,
                sindexweb2: 1,
                sindexweb3: 2,

                scrollHnadlerCallCount: 0,
                selectedIndex: 0,
                value: 0,
                val: 0,
                index: 0,
                sindex: 0,

                defclass: 'defclass',
                selectclass: 'selectclass',
                itemsrc: "https://gd2.alicdn.com/bao/uploaded/i2/T14H1LFwBcXXXXXXXX_!!0-item_pic.jpg",

            }
        },
        components: {
            text1,
            text2,
            text3,
        },

        created () {
            this.select(this.selectedIndex)
        },
        methods: {
            mStyle: function () {
                return {
                    width: 750 + 'px',
                    height: 1190 + 'px',
                }
            },
            onchange (event) {
                this.sindex = event.index
                this.select(this.sindex)

                //web  可以不做终端验证
                if (event.index === 0) {
                    this.val = event.index
                } else if (event.index === 1) {
                    this.val = event.index
                } else if (event.index === 2) {
                    this.val = event.index
                }
            },

            selecttile (event) {
                this.sindex = event.index
                this.val = this.sindex


                //web 可以不做终端验证
                if (event.index === 0) {
                    this.sindexweb1 = event.index
                } else if (event.index === 1) {
                    this.sindexweb2 = event.index
                } else if (event.index === 2) {
                    this.sindexweb3 = event.index
                }

            },
            select (index) {

                for (let i = 0; i < this.message.length; i++) {
                    console.log("点击的下标" + index);
                    let msg = this.message[i]
                    if (i == index) {
                        msg.visibility = 'visible'
                        console.log("显示的下标" + i);
                    } else {
                        msg.visibility = 'hidden'
                        console.log('隐藏的下标' + i);
                    }
                }
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .hello {
        left: 0;
        right: 0;
        flex-direction: row;
    }

    .title1 {
        justify-content: center;
        align-items: center;
        background-color: #afddff;
        height: 100px;
        flex: 1;
    }

    .defclass {

    }

    .selectclass {
        color: red;
    }
</style>
