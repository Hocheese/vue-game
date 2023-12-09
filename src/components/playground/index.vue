<template>
    <div class="playground">
        <div class="top">
            <div class="cardArea">
                <div v-for="teacher in runtime.teachers" class="teacher">
                    <div >111</div>
                </div>
            </div>
        </div>
        <div class="glass">
            <div class="row" v-for="row in runtime.lines">
                <div class="col" v-for=" col in row.blocks">233</div>
                <div class="student" v-for="student in row.students" :style="{left: student.x+'vw'}">114514</div>
            </div>
        </div>
        <div class="footer">
            <div @click="start">开始/暂停</div>
        </div>
    </div>
</template>
<script setup>
import { useSound } from '@vueuse/sound'
import { reactive } from 'vue';
import { useIntervalFn, useCssVar } from '@vueuse/core'
import glasswork from '../../static/sound/glasswalk.m4a'

const runtime = reactive({
    lines: [], // 草地行
    teachers:[], // 拥有的老师
});

const line = new Array(5).fill(5)
runtime.lines= line.map(() => {
    const blocks = new Array(5).fill(5);
    return {
        students: [],
        blocks: blocks.map(() => {
            return {
                type: 1,
                bullets: [],
                teachers: []
            }
        })
    }
})
const studentTest = {
    x: -10
}
const teacherTest = {
    id:'zzj'
}
runtime.teachers.push(teacherTest);
runtime.lines[0].students.push(studentTest);
const { play } = useSound(glasswork);
const { pause, resume, isActive } = useIntervalFn(() => {
    console.log('游戏刻')
    runtime.lines.forEach(l => {
        l.students.forEach(s => {
            s.x+=0.01
        })
    })
}, 10)
// resume();

function start() {
    play()
    resume()
}
pause()

</script>
<style lang="scss" scoped>
.playground{
    height: 100vh;
    width: 100vw;
    display: flex;
    flex-direction: column;
}
.top {
    .cardArea{
        height: 100px;
        background-color: chocolate;
        .teacher{
            width: 10vh;
            background-color: burlywood;
            height: 100%;
        }
    }
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