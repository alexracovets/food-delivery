<template>
    <div class="cursor-wrapper" cursor-target>
        <div id="cursor" ref="cursor"></div>
        <div id="aura"></div>
    </div>
</template>

<script>

import {gsap} from "gsap";

export default {
    name: 'CustomCursor',
    data: () => {
        return {
            mouseX: 0,
            mouseY: 0,
            posX: 0,
            posY: 0
        }
    },
    methods: {
        mouseCoords(e) {
            this.$data.mouseX = e.pageX;
            this.$data.mouseY = e.pageY;
        },
        animLogic(aura, cursor) {

            gsap.to(aura, .01, {
                repeat: -1,
                onRepeat: () => {
                    this.$data.posX += (this.$data.mouseX - this.$data.posX) / 5;
                    this.$data.posY += (this.$data.mouseY - this.$data.posY) / 5;
                    gsap.set(cursor, {
                        css: {
                            left: this.$data.mouseX,
                            top: this.$data.mouseY,
                        }
                    })

                    gsap.set(aura, {
                        css: {
                            left: this.$data.posX - 24,
                            top: this.$data.posY - 24,
                        }
                    })
                }
            });
        },
        removeClass(item, className) {
            item.classList.remove(className);
        },
        addClass(item, className) {
            item.classList.add(className);
        }
    },
    mounted() {

        const
            body = document.querySelector('body'),
            cursor = document.getElementById('cursor'),
            aura = document.getElementById('aura'),
            targets = document.querySelectorAll('[cursor-target]');

        this.animLogic(aura, cursor);

        body.addEventListener('mousemove', e => {
            this.mouseCoords(e)
            this.removeClass(cursor, 'hidden');
            this.removeClass(aura, 'hidden');
        });

        body.addEventListener('mouseout', () => {
            this.addClass(cursor, 'hidden');
            this.addClass(aura, 'hidden');
        });

        targets.forEach(trigger => {
            trigger.addEventListener('mouseover', () => {
                this.addClass(cursor, 'active');
                this.addClass(aura, 'active')
            })
        })

        targets.forEach(trigger => {
            trigger.addEventListener('mouseout', () => {
                this.removeClass(cursor, 'active');
                this.removeClass(aura, 'active');
            })
        })
    }
}


</script>

<style lang="scss" scoped>
@import "CustomCursor";
</style>
