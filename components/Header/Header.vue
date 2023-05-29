<template>
    <header>
        <div class="header-wrapper">
            <Logo/>
            <IsDeliver v-if="!mobileView"/>
            <Navbar v-if="!mobileView"/>
            <CallRequest v-if="!mobileView"/>
            <Burger
                v-if="mobileView"
                :opener="switchBurger"
            />
            <FullMenu
                :class="{'open': showNav}"
                :closer="switchBurger"/>
        </div>
    </header>
</template>

<script>
import Navbar from "@/components/Header/Navbar/Navbar.vue";
import IsDeliver from "@/components/Header/IsDeliver/IsDeliver.vue";
import Logo from "@/components/Header/Logo/Logo.vue";
import CallRequest from "@/components/Header/CallRequest/CallRequest.vue";
import FullMenu from "@/components/Header/FullMenu/FullMenu.vue";
import Burger from "@/components/Header/Burger/Burger.vue";

export default {
    name: 'Header',
    components: {Burger, CallRequest, Logo, IsDeliver, Navbar, FullMenu},
    data: () => {
        return {
            mobileView: true,
            showNav: false
        }
    },
    methods: {
        handleView() {
            this.mobileView = window.innerWidth <= 991;
        },
        switchBurger() {
            this.showNav = !this.showNav
        }
    },
    mounted() {
        this.handleView();
        window.addEventListener("resize", (event) => {
            this.handleView()
        });
    }
}
</script>

<style lang="scss" scoped>
@import "./Header.scss";
</style>
