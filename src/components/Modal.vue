<template>
    <div class="modalContainer">
        <span @click="$emit('close-modal')" class="close"></span>
        <span @click="prev()" class="arrow arrow__prev"></span>
        <span @click="next()" class="arrow arrow__next"></span>
       <figure class="modalContainer__item">
            <img v-if="img.url" :src="img.url" alt="">
        </figure>
    </div>
</template>

<script>
export default {
    data() {
        return {
            img: '',
            currentIndex: 0,
            maxIndex: null,
        }
    },
    props: {
        modalImg: {
            type: Object,
            required: true,
        },

        sortedImg: {
            type: Array,
            required: true,
        },

        gallery: {
            type: Array,
            required: true,
        }
    },

    mounted() {
        this.img = this.modalImg;
        console.log(this.sortedImg);
    },

    methods: {
        next() {
            this.currentIndex = this.sortedImg.indexOf(this.img);
            this.maxIndex = this.sortedImg.length-1;
            this.img = this.sortedImg[ this.currentIndex < this.maxIndex ? this.currentIndex + 1 : 0];
        },

        prev() {
            this.currentIndex = this.sortedImg.indexOf(this.img);
            this.maxIndex = this.sortedImg.length-1;
            this.img = this.sortedImg[this.currentIndex === 0 ? this.maxIndex : this.currentIndex-1];
        }
    },
}
</script>

<style lang="scss" scoped>
    .modalContainer {
        position: fixed;
        top: 0;
        left: 0;
        height: 100vh;
        width: 100%;
        background-color: rgba(0,0,0,.7);

        z-index: 5;

        &__item {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 100%;
            padding: 3rem;

            & > img {
                max-width: 100%;
            }

            @media(min-width: 768px) {
                width: 60%;
            }

            @media(min-width: 1024px) {
                width: 30%;
            }
        }

        .close {
            display: block;
            position: absolute;
            top: 1rem;
            right: .5rem;
            width: 2rem;
            height: 2rem;
            cursor: pointer;
            z-index: 6;

            &::before,
            &::after {
                content: '';
                position: absolute;
                top: 50%;
                width: 1.8rem;
                height: .2rem;
                background-color: #fff;
            }

            &::before {
                transform: rotate(45deg);
            }

            &::after {
                transform: rotate(-45deg);
            }
        }
    }

    .arrow {
        display: inline-block;
        position: absolute;
        top: 50%;
        width: 1.6rem;
        height: 1.6rem;
        transform: rotate(45deg);
        border: 3px solid rgba(0,0,0, .6);
        cursor: pointer;
        transition: border .3s;
        z-index: 1;

        @media(min-width: 768px) {
            width: 5rem;
            height: 5rem;
            border: 1px solid rgba(255,255,255, .7);
        }

        &__prev {
            left: 15%;
            border-top: 0;
            border-right: 0;

            @media(min-width: 768px) {
                right: 10%;
            }

            &:hover {
                border-bottom: 3px solid rgba(0,0,0, .6);
                border-left: 3px solid rgba(0,0,0, .6);

                 @media(min-width: 768px) {
                    border-bottom: 1px solid rgba(255,255,255, 1);
                    border-left: 1px solid rgba(255,255,255, 1);
                }
            }
        }

        &__next {
            right: 15%;
            border-bottom: 0;
            border-left: 0;

            @media(min-width: 768px) {
                right: 10%;
            }

             &:hover {
                border-top: 3px solid rgba(0,0,0, .6);
                border-right: 3px solid rgba(0,0,0, .6);

                @media(min-width: 768px) {
                    border-top: 1px solid rgba(255,255,255, 1);
                    border-right: 1px solid rgba(255,255,255, 1);
                }
            }
        }
    }
</style>
