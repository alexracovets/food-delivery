<template>
    <div class="delivery-circle" id="DelCircle">
        <div class="circle-content">
           <a href="###">Замовити доставку</a>
        </div>
    </div>
</template>

<script>

import {gsap} from "gsap";
import {ScrollTrigger} from "gsap/ScrollTrigger";

export default {
    name: 'DeliveryCircle',
    methods: {
        decreaseCircle(item) {
            gsap.to(item, {
                scrollTrigger: {
                    trigger: item,
                    start: "left center",
                    toggleActions: 'play none none none',
                    toggleClass: 'start',
                    once: true,
                },
            });

            item.addEventListener('mouseover', () => {
                item.classList.add('increase');
            })

            item.addEventListener('mouseout', () => {
                item.classList.remove('increase');
            })
        }
    },
    mounted() {
        const animCircle = document.getElementById('DelCircle');
        gsap.registerPlugin(ScrollTrigger);
        this.decreaseCircle(animCircle);
    }
}
</script>

<style lang="scss" scoped>
@import "./DeliveryCircle.scss";
</style>
