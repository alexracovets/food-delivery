<template>
    <div class="page">
        <nuxt/>
        <MainScreen/>
        <Benefit/>
    </div>
</template>

<script>

import MainScreen from "@/components/MainScreen/MainScreen.vue";
import Benefit from "@/components/Benefits/Benefits.vue";

export default {
    name: 'Main',
    components: {MainScreen, Benefit}
}
</script>
