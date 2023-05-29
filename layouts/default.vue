<template>
    <div class="layout">
        <CustomCursor/>
        <DeliveryCircle/>
        <Header/>
        <nuxt/>
    </div>
</template>

<script>

import Header from "@/components/Header/Header.vue";
import CustomCursor from "~/components/CustomCursor/CustomCursor.vue";
import DeliveryCircle from "~/components/DeliveryCircle/DeliveryCircle.vue";

export default {
    components: {Header, CustomCursor, DeliveryCircle}
}

</script>
