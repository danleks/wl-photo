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
    </section>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>

.aboutWrapper {
    position: relative;
    padding: 0 2rem 0 2rem;
    padding-top: var(--sectionGutter);

    @media(min-width: 768px) {
        padding: 2.6rem;
    }

    @media(min-width: 1024px) {
        display: flex;
    }

    &__img {

         @media(min-width: 1024px) {
            flex: 1;
        }

        img {
            width: 100%;
            height: auto;
        }
    }

    &__content {

         @media(min-width: 768px) {
            padding: 0 6rem;
        }

         @media(min-width: 1024px) {
            flex: 1;
            align-self: center;
        }

        color: #384653;

        h2 {
            margin: 1rem 0;
            font-size: var(--headerFontsize);
            text-align: center;
            letter-spacing: var(--headerLetterSpacing);
            margin-bottom: 1rem;

            @media(min-width: 768px) {
                font-size: 3.8rem;
            }
        }

        p {
            padding-bottom: 2rem;
            font-size: var(--contentFontsize);
            text-align: justify;
            font-size: 14px;
            letter-spacing: var(--contentLetterSpacing);
            line-height: 1.4;

             @media(min-width: 768px) {
                font-size: 2.4rem;
            }
        }
    }
}

</style>
