<template>
    <div class="menu-btn" @click="opener" cursor-target>
        <span></span>
        <span></span>
        <span></span>
    </div>
</template>

<script>

export default {
    name: 'Burger',
    props: ['opener']
}
</script>

<style lang="scss" scoped>
@import "./Burger.scss";
</style>
