<template>
    <div class="playground">
        <div class="top">
            <div class="cardArea">1111</div>
        </div>
        <div class="glass">
            <div class="row" v-for="row in runtime.lines">
                <div class="col" v-for=" col in row.blocks">233</div>
                <div class="student" v-for="student in row.students" :style="{left: student.x+'vw'}">114514</div>
            </div>
        </div>
    </div>
</template>
<script setup>
import { reactive } from 'vue';
import { useIntervalFn, useCssVar } from '@vueuse/core'

const runtime = reactive({
    lines: [],
    interval: null
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
const teacher = {
    x: 100
}
runtime.lines[0].students.push(teacher);
const { pause, resume, isActive } = useIntervalFn(() => {
    console.log('游戏刻')
    runtime.lines.forEach(l => {
        l.students.forEach(s => {
            s.x-=0.01
        })
    })
}, 10)
// resume();

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
        position: relative;
        .col {
            width: 20vw;
            border: 1px solid green;
        }
        .student{
            position: absolute;
            height: 100%;
            width: 10vw;
            background-color: red;
        }
    }
}
</style>