<template>
    <main id="action">
        <el-row>
            <el-col :span="24">
                <div class="center">
                    <el-button type="danger" @click="clickNext" class="center">！！！</el-button>
                </div>
            </el-col>
        </el-row>

        <el-row>
            <el-col :span="24">
                <div class="center">
                    <p class="biggest-font red">！！</p>
                </div>
            </el-col>
        </el-row>
    </main>
</template>

<script>
export default {
    methods: {
        clickNext: function () {
            this.$emit('actionNextEvent');
        }
    }
}
</script>

<style lang="scss" scoped>
</style>