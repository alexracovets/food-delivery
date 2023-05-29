<template>
    <div class="menu-wrapper">
        <div class="menu">
            <div class="cross" @click="closer">
                <a>
                    <div class="cross-mark"></div>
                </a>
            </div>

            <ul class="menu-links">
                <li>
                    <a href="###">Заклади</a>
                </li>
                <li>
                    <a href="###">Доставка і оплата</a>
                </li>
                <li>
                    <a href="###">Акції</a>
                </li>
                <li>
                    <a href="###">Про нас</a>
                </li>
            </ul>
            <IsDeliver class="mobile"/>
            <CallRequest class="mobile"/>
        </div>
    </div>
</template>

<script>

import CallRequest from "@/components/Header/CallRequest/CallRequest.vue";
import IsDeliver from "@/components/Header/IsDeliver/IsDeliver.vue";

export default {
    name: 'FullMenu',
    components: {IsDeliver, CallRequest},
    props: ['closer'],
    mounted() {
        const menuWrapper = document.querySelector('.menu-wrapper');
        const menuMenu = document.querySelector('.menu');
        const closeMenu = this.closer;

        menuWrapper.addEventListener("click", function (event) {
            if (event.x > menuMenu.getBoundingClientRect().width) {
                closeMenu()
            }
        });
        document.addEventListener('keydown', function (event) {
            if (event.keyCode == 27) {
                closeMenu()
            }
        });
    }
}
</script>

<style lang="scss" scoped>
@import "./FullMenu.scss";
</style>
