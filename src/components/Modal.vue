<template>
    <div class="modalContainer">
        <span @click="$emit('close-modal')" class="close"></span>
        <figure class="modalContainer__item">
            <img :src="modalImg" alt="">
        </figure>
    </div>
</template>

<script>
export default {
    props: {
        modalImg: {
            type: String,
            required: true,
        }
    }
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
</style>
