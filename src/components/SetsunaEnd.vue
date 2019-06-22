<template>
    <main id="end">
        <el-row>
            <el-col :span="24">
                <div class="center">{{Math.round(tickTime / (1000 / 60))}} ({{tickTime}} ms)</div>
            </el-col>
        </el-row>

        <el-row>
            <el-col :span="24">
                <el-button type="warning" @click="clickNext" class="center">TO Start</el-button>
            </el-col>
        </el-row>
    </main>
</template>

<script>
export default {
    props: ['tickTime'],
    methods: {
        clickNext: function () {
            this.$emit('endNextEvent');
        }
    }
}
</script>

<style lang="scss" scoped>
</style>