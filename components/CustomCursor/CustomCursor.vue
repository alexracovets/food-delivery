<template>
    <div class="cursor-wrapper">
        <div id="cursor" ref="cursor"></div>
        <div id="aura"></div>
    </div>
</template>

<script>
import {gsap} from "gsap";

export default {
    name: 'CustomCursor',
    mounted() {
        const
            body = document.querySelector('body'),
            cursor = document.getElementById('cursor'),
            aura = document.getElementById('aura'),
            links = document.getElementsByTagName('a'),
            inputs = document.getElementsByTagName('input'),
            labels = document.getElementsByTagName('label'),
            circle = document.querySelector('.delivery-circle'),
            allTriggers = [...links, ...inputs, ...labels];

        let mouseX = 0,
            mouseY = 0,
            posX = 0,
            posY = 0;

        function mouseCoords(e) {
            mouseX = e.pageX;
            mouseY = e.pageY;
        }


        gsap.to({}, .01, {
            repeat: -1,
            onRepeat: () => {

                posX += (mouseX - posX) / 5;
                posY += (mouseY - posY) / 5;

                gsap.set(cursor, {
                    css: {
                        left: mouseX,
                        top: mouseY,
                    }
                })

                gsap.set(aura, {
                    css: {
                        left: posX - 24,
                        top: posY - 24,
                    }
                })
            }
        });

        body.addEventListener('mousemove', e => {
            mouseCoords(e);
            cursor.classList.remove('hidden');
            aura.classList.remove('hidden');
        });

        body.addEventListener('mouseout', e => {
            cursor.classList.add('hidden');
            aura.classList.add('hidden');
        });

        allTriggers.forEach((trigger) => {
            trigger.addEventListener('mouseover', () => {
                cursor.classList.add('active');
                aura.classList.add('active');
            })
        })

        allTriggers.forEach((trigger) => {
            trigger.addEventListener('mouseout', () => {
                cursor.classList.remove('active');
                aura.classList.remove('active');
            })
        })

        circle.addEventListener('mouseover', () => {
            cursor.classList.add('active');
            aura.classList.add('active');
        })

        circle.addEventListener('mouseout', () => {
            cursor.classList.add('active');
            aura.classList.add('active');
        })
    }
}


</script>

<style lang="scss" scoped>
@import "CustomCursor";
</style>
