<template>
    <div class="menu-wrapper">
        <div class="menu">
            <Cross :closer="closer"/>
            <Navbar/>
            <IsDeliver/>
            <CallRequest/>
        </div>
    </div>
</template>

<script>

import CallRequest from "@/components/Header/CallRequest/CallRequest.vue";
import IsDeliver from "@/components/Header/IsDeliver/IsDeliver.vue";
import Navbar from "@/components/Header/Navbar/Navbar.vue";
import Cross from "@/components/Header/Cross/Cross.vue";

export default {
    name: 'FullMenu',
    components: {Cross, Navbar, IsDeliver, CallRequest},
    props: ['closer'],
    mounted() {
        const menuWrapper = document.querySelector('.menu-wrapper');
        const menuMenu = document.querySelector('.menu');
        const closeMenu = this.closer;

        menuWrapper.addEventListener("click", function (e) {
            if (e.x > menuMenu.getBoundingClientRect().width) {
                closeMenu()
            }
        });
        document.addEventListener('keydown', function (e) {
            if (e.key === 'Escape') {
                closeMenu()
            }
        });
    }
}
</script>

<style lang="scss" scoped>
@import "./FullMenu.scss";
</style>
