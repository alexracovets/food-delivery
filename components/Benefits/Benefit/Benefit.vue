<template>
    <div class="item">
        <div class="front">
            <div class="item-title">
             {{benefit.title}}
            </div>
            <div class="item-img">
                <img :src="benefit.img" />
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
    props: {
        benefit:{
            type: Object,
        }
    },
};
</script>

<style lang="scss" scoped>
@import "./Benefit";
</style>
