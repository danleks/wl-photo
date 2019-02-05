<template>
    <section id="about" class="aboutWrapper">
        <div class="aboutWrapper__img">
            <img src="../assets/img-2.jpg" alt="a flying man with a camera">
        </div>
        <div class="aboutWrapper__content">
            <h2>Beautiful things <br/>
            can make you fly
            </h2>
            <p>I believe the way you percept your surroundings influences your life. Be <span>creative</span> - notice what seems to be hidden. Follow me and catch a glimpse of the world through my eyes. </p>
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
        width: 1000px;
        margin: auto;
    }

    &__img {

         @media(min-width: 1024px) {
            flex: 1;
        }

        img {
            display: block;
            width: 100%;
            height: auto;
        }
    }

    &__content {
        color: white;
        background: rgba(#384653, 1);
        padding: 1rem 3rem;

         @media(min-width: 768px) {
            padding: 1rem 15rem;
        }

         @media(min-width: 1024px) {
            flex: 1;
            display: flex;
            flex-direction: column;
            justify-content: center;
            padding: 1rem 3rem;
        }

        h2 {
            margin: 1rem 0;
            margin-bottom: 1rem;
            color: #f55110;
            font-size: var(--headerFontsize);
            font-weight: 100;
            text-align: center;
            letter-spacing: var(--headerLetterSpacing);

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
                font-size: 2.5rem;
            }
        }

        span {
            color: #f55110;
            font-weight: bold;
            font-size: 18px;
            text-transform: uppercase;

            @media(min-width: 768px) {
                font-size: 3rem;
            }
        }
    }
}

</style>
