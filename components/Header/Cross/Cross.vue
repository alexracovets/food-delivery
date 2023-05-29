<template>
    <div class="cross" @click="closer" cursor-target>
        <div class="cross-mark"></div>
    </div>
</template>

<script>

export default {
    name: 'Cross',
    props: ['closer'],
}
</script>

<style lang="scss" scoped>
@import "./Cross.scss";
</style>
