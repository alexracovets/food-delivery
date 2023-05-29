<template>
    <div class="container">
        <div class="benefit-wrapper">
            <Benefit v-for="benefit in benefits"
                     :key="benefit.id"
                     :benefit="benefit"
            />
        </div>
    </div>
</template>

<script>
import Benefit from "@/components/Benefits/Benefit/Benefit.vue";
import {gsap} from "gsap";
import {ScrollTrigger} from "gsap/ScrollTrigger";

export default {
    name: 'Benefits',
    components: {Benefit},
    data: () => ({
        benefits: [
            {
                title: 'Висока якість продукції',
                img: require('~/static/img/benefit1.png'),
                text: 'Наша доставка гарантує вам високу якість продуктів.  Кожна страва, яку ми готуємо, пройшла строгий контроль якості, щоб забезпечити вам найкращий смаковий досвід.',
                id: 1,
            },
            {
                title: 'Різноманітність страв',
                img: require('~/static/img/benefit2.png'),
                text: 'Наша доставка гарантує вам високу якість продуктів.  Кожна страва, яку ми готуємо, пройшла строгий контроль якості, щоб забезпечити вам найкращий смаковий досвід.',
                id: 2,
            },
            {
                title: 'Швидка доставка',
                img: require('~/static/img/benefit3.png'),
                text: 'Наша доставка гарантує вам високу якість продуктів.  Кожна страва, яку ми готуємо, пройшла строгий контроль якості, щоб забезпечити вам найкращий смаковий досвід.',
                id: 3,
            },
            {
                title: 'Працюємо цілодобово',
                img: require('~/static/img/benefit4.png'),
                text: 'Наша доставка гарантує вам високу якість продуктів.  Кожна страва, яку ми готуємо, пройшла строгий контроль якості, щоб забезпечити вам найкращий смаковий досвід.',
                id: 4,
            },
        ]
    }),
    mounted() {
        const animItems = document.querySelectorAll('.benefit-wrapper .item');
        gsap.registerPlugin(ScrollTrigger);

        animItems.forEach((animItem) => {
            ScrollTrigger.create({
                trigger: animItem,
                toggleClass: 'active',
                toggleActions: 'play none none none',
                once: true,
            })
        })
    }
};
</script>

<style lang="scss" scoped>
@import "./Benefits";
</style>
