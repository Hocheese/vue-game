<template>
    <div class="playground">
        <div class="top">
            <div class="cardArea">1111</div>
        </div>
        <div class="glass">
            <div class="row" v-for="row in runtime.lines">
                <div class="col" v-for=" col in row.blocks">233</div>
            </div>
        </div>
    </div>
</template>
<script setup>
import { reactive } from 'vue';
const runtime = reactive({
    lines: []
});

const line = new Array(5).fill(5)
runtime.lines= line.map(() => {
    const blocks = new Array(5).fill(5);
    return {
        students: [],
        blocks: blocks.map(() => {
            return {
                type: 1,
                teachers: []
            }
        })
    }
})

</script>
<style lang="scss" scoped>
.playground{
    height: 100vh;
    width: 100vw;
    display: flex;
    flex-direction: column;
}
.glass{
    background-color: greenyellow;
    .row {
        display: flex;
        width: 100vw;
        height: 10vh;
        .col {
            width: 20vw;
            border: 1px solid green;
        }
    }
}
</style>