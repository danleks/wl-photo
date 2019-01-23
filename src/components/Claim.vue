<template>
    <section class="claimWrapper">
        <h1 class="claimWrapper__heading">
            <span>D</span>
            <span>ay</span>
            <span>reamer</span>
        </h1>
        <div class="claimWrapper__text">
            <p>Photos I like most</p>
        </div>
    </section>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
    .claimWrapper {


        &__heading {
            position: absolute;
            top: 32%;
            left: 18%;
            transform: translate(-50%, -50%);
            color: #384653;
            font-weight: 500;

            & > span {
            position: absolute;
            font-size: 38px;
            text-transform: uppercase;
            letter-spacing: 5px;

            @media(min-width: 768px) {
                font-size: 72px;
            }

            @media(min-width: 1024px) {
                letter-spacing: 30px;
            }

            &:first-child {
                position: relative;
                font-size: 120px;
                color: #942130;

                @media(min-width: 768px) {
                    font-size: 288px;
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

        &__text {
            width: 100%;
            position: absolute;
            top: 48.7%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 12px;
            color: rgba(#942130,.3);
            text-transform: uppercase;

            @media(min-width: 768px) {
                font-size: 16px;
                color: transparent;
                text-shadow: 0 0 5px rgba(#942130,.3);
            }

            p {
                text-align: center;
                letter-spacing: 4px;

                @media(min-width: 768px) {
                    font-size: 30px;
                    letter-spacing: 10px;
                }
            }
        }

    }

</style>
