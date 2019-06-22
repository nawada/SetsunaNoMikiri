<template>
    <main id="start">
        <el-row>
            <el-col :span="24">
                <div class="center">
                    <el-button type="primary" @click="clickStart">開始</el-button>
                </div>
            </el-col>
        </el-row>

        <el-row>
            <el-col :span="24">
                <div class="center">
                    <p>開始するには「開始」ボタンか、Enterキーか、Spaceキーを押してください。</p>
                    <p>「<span class="red bigger-font">！！</span>」が表示されたら、Enterキーか、Spaceキーを押してください。</p>
                </div>
            </el-col>
        </el-row>

        <el-row>
            <el-col :span="24">
                <div class="center">
                    <h5>いままでのきろく</h5>
                    <ul>
                        <li v-for="(record, index) in records" :key="'item-' + index">
                            {{Math.round(record / (1000 / 60))}} ({{record}} ms)
                        </li>
                    </ul>
                </div>
            </el-col>
        </el-row>
    </main>
</template>

<script>
export default {
    props: ['records'],
    methods: {
        clickStart: function () {
            this.$emit('clickStart');
        }
    }
};
</script>

<style lang="scss" scoped>
</style>