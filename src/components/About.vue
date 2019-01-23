<template>
    <section id="about" class="aboutWrapper">
        <div class="aboutWrapper__img">
            <img src="../assets/img-1.jpg" alt="a flying man with a camera">
        </div>
        <div class="aboutWrapper__content">
            <h2>Beautiful things <br/>
            can make you fly
            </h2>
            <p>I believe that the way you percept your surroundings influences your life. Be creative and see what seems to be hidden. Follow me and see the world through my eyes. </p>
        </div>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>


    </section>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>

.aboutWrapper {
    position: relative;
    padding: 20px;

    @media(min-width: 768px) {
        padding: 26px;
    }

    &__img {

        img {
            width: 100%;
            height: auto;
        }
    }

    &__content {


         @media(min-width: 768px) {
            padding: 0 60px;
        }

        color: #384653;

        h2 {
            margin: 10px 0;
            font-size: 24px;
            text-align: center;
            letter-spacing: 2px;
            margin-bottom: 10px;

            @media(min-width: 768px) {
                font-size: 38px;
            }
        }

        p {
            font-size: 14px;
            text-align: justify;
            font-size: 14px;
            letter-spacing: 1px;
            line-height: 1.4;

             @media(min-width: 768px) {
                font-size: 24px;
            }
        }
    }
}

</style>
