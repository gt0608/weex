<template>
    <div class="app">
        <scoorl :message="parentMsg"></scoorl>
    </div>

</template>

<script>
    import text1 from './components/text1.vue'
    import Hello from './components/Hello.vue'
    import scoorl from './components/scoorl.vue'
    import zidingyishijian from './components/zidingyishijian.vue'

    export default {
        name: 'app',
        data () {
            return {
                total: 1,
                parentMsg: [
                    {
                        name: 'Runoob',
                        index:0,
                        src:"http://101.200.147.220:8080/a/home.js",
                        visibility: 'visible'

                    },
                    {
                        name: 'Google',
                        index:1,
                        src:"http://101.200.147.220:8080/a/home.js",
                        visibility: 'hidden'
                    },
                    {
                        name: 'Taobao',
                        index:2,
                        src: 'http://101.200.147.220:8080/a/message.js',
                        visibility: 'hidden'
                    }
                ],
                src: "https://img.alicdn.com/tfs/TB1OOl1SVXXXXc_XVXXXXXXXXXX-340-340.png"
            }
        },
        components: {
            scoorl,
            zidingyishijian
        },
        methods: {
            incrementTotal: function () {
                this.total += 1
            }
        }

    }
</script>

<style scoped>
    .app {
        left: 0px;
        right: 0px;
        top: 0px;

    }
</style>
