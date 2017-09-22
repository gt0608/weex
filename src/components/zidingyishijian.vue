<template>
    <div class="hello">
        <button style="width: 300px;background-color: #afddff; height: 100px" @click="increment">{{ counter }}</button>
    </div>
</template>

<script>
    export default {
        data () {
            return {
                counter: 0
            }
        },
        methods: {
            increment: function () {
                this.counter += 1
                this.$emit('increment')//触发事件
            }
        }
    }
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .hello{

    }
</style>
