<template>
    <section class="claimWrapper">
        <h1 class="claimWrapper__heading">
            <span>D</span>
            <span>ay</span>
            <span>reamer</span>
        </h1>
        <!-- <div class="claimWrapper__text">
            <p>Photos I like most</p>
        </div> -->
    </section>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
    .claimWrapper {
        position: absolute;
        top: 35%;
        left: 25%;
        transform: translate(-50%, -50%);

        &__heading {
            color: #384653;
            font-weight: 500;

            & > span {
            position: absolute;
            font-size: 3.8rem;
            text-transform: uppercase;
            letter-spacing: .5rem;

            @media(min-width: 768px) {
                font-size: var(--mainLetterFontSize);
            }

            @media(min-width: 1024px) {
                letter-spacing: 30px;
            }

            &:first-child {
                position: relative;
                font-size: 12rem;
                color: #942130;

                @media(min-width: 768px) {
                    font-size: 28.8rem;
                }
            }

            &:nth-child(2) {
                top: 19%;

                @media(min-width: 768px) {
                    top: 28%;
                }

            }

            &:nth-child(3) {
                top: 50%;
            }
        }
        }

        // &__text {
        //     width: 100%;
        //     position: absolute;
        //     top: 48.7%;
        //     left: 50%;
        //     transform: translate(-50%, -50%);
        //     font-size: 1.2rem;
        //     color: rgba(#942130,.3);
        //     text-transform: uppercase;

        //     @media(min-width: 768px) {
        //         font-size: 16px;
        //         color: transparent;
        //         text-shadow: 0 0 5px rgba(#942130,.3);
        //     }

        //     p {
        //         text-align: center;
        //         letter-spacing: 4px;

        //         @media(min-width: 768px) {
        //             font-size: 30px;
        //             letter-spacing: 10px;
        //         }
        //     }
        // }

    }

</style>
