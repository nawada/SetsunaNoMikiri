<template>
    <main id="wait">
        <el-row>
            <el-col :span="24">
                <div class="center">「！！」が表示されたら、Enterキーか、Spaceキーを押す！</div>
            </el-col>
        </el-row>
    </main>
</template>

<script>
export default {
    methods: {
        clickNext: function () {
            this.$emit('waitNextEvent');
        }
    }
}
</script>

<style lang="scss" scoped>
</style>
