<template>
    <div class="item" cursor-target>
        <div class="front">
            <div class="item-title">
             {{benefit.title}}
            </div>
            <div class="item-img">
                <img :src="benefit.img" :alt="benefit.title" />
            </div>
        </div>
        <div class="back">
            {{benefit.text}}
        </div>
    </div>
</template>

<script>
export default {
    name: 'Benefit',
    props: ['benefit']
};
</script>

<style lang="scss" scoped>
@import "./Benefit";
</style>
