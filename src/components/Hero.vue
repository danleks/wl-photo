<template>
    <section class="heroWrapper">
        <app-claim />
        <div class="heroWrapper__bg" />
        <div @click="scrollDown" class="arrowDown" slot="arrowDown">
            <div class="arrowDown__circle">
                <div class="arrowDown__triangle" />
            </div>
        </div>
    </section>
</template>

<script>
import Claim from './Claim.vue';
export default {
    components: {
        'app-claim': Claim,
    },

    data() {
        return {
            inViewPort: true,
        }
    },

    methods: {
        isInViewPort(elem) {
            let bounding = elem.getBoundingClientRect();
            return (
                bounding.top === 0
            )
        },

        scrollDown() {
            document.getElementById('about').scrollIntoView({
                behavior: 'smooth'
            });
        }
    },

    mounted() {
        let heroWrapper = document.querySelector('.heroWrapper');
        window.addEventListener('scroll', ()=>{
            if (this.isInViewPort(heroWrapper)) {
                this.inViewPort = true;
                this.$root.$emit('in-View-Port', this.inViewPort);
            } else {
                this.inViewPort = false;
                this.$root.$emit('in-View-Port', this.inViewPort);
            }
        })


    }

}
</script>

<style lang="scss" scoped>
    .heroWrapper {
        position: relative;
        background-origin: border-box;

        &__bg {
            width: 100%;
            height: 100vh;
            background-image: url('../assets/hero.jpg');
            background-size: cover;
            background-position: 50%;
            background-repeat: no-repeat;
        }

        .arrowDown {
            position: absolute;
            left: 50%;
            bottom: -2%;
            transform: translate(-50%, -50%);
            cursor: pointer;

            @media(min-width: 768px) {
                bottom: -1px;
            }

            &__circle {
                position: relative;
                width: 45px;
                height: 45px;
                border-radius: 50%;
                background-color: rgba(#000, .4);

                @media(min-width: 768px) {
                    width: 55px;
                    height: 55px;
                }
            }

            &__triangle {
                position: absolute;
                top: 50%;
                left: 50%;
                transform: translate(-50%, -50%);
                width: 0;
                height: 0;
                border-style: solid;
                border-width: 9px 9px 0 9px;
                border-color: rgba(#fff, .1) transparent transparent transparent;
                animation: blink 2s infinite;

                @media(min-width: 768px) {
                    border-width: 11px 11px 0 11px;
                }
                }

                @keyframes blink {
                    0% {border-color: rgba(#fff, .1) transparent transparent transparent;}

                    50% {border-color: rgba(#fff, 1) transparent transparent transparent;}

                    100% {border-color: rgba(#fff, .1) transparent transparent transparent;}
                }
        }
    }
</style>
