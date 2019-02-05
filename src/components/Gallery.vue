<template>
    <section id="gallery" class="galleryWrapper">
        <header>
            <h2>Photo Gallery</h2>
            <p>This is a small collection of photos <br/>I find inspiring</p>
        </header>
        <nav class="galleryWrapper__nav">
            <a @click="filterBy($event)" href="#">All</a>
            <a @click="filterBy($event)" href="#">Nature</a>
            <a @click="filterBy($event)" href="#">Buildings</a>
            <a @click="filterBy($event)" href="#">Cars</a>
            <a @click="filterBy($event)" href="#">Animals</a>
        </nav>
        <div class="galleryWrapper__items"
        v-masonry
        transition-duration="0.3s"
        item-selector=".galleryWrapper__item"
        column-width=".sizer"
        gutter=".gutter-sizer"
        >
            <div class="sizer"></div>
            <div class="gutter-sizer"></div>
            <figure v-masonry-tile class="galleryWrapper__item" v-for="img in sortedImgs" :key="img.id">
                <img @click="$emit('show-modal', img, sortedImgs)" :src="img.url"
                alt="img.caption">
                <figcaption>{{img.caption}}</figcaption>
            </figure>
        </div>
    </section>
</template>

<script>

export default {
    data() {
        return {
            modal: false,
            galleryItem: 'galleryWrapper__item',
            modalContainer: 'modal',
            modalItem: 'modal',
            imgModal: null,
            filter: '',
        }
    },

    props: {
        gallery: {
            type: Array,
            required: true,
        }
    },

    methods: {
        showModal(e) {
            this.modal = true;
            this.imgModal = e.target.currentSrc;
        },

        closeModal(){
            this.modal = false;
        },

        filterBy(e) {
            e.preventDefault();
            this.filter = e.target.textContent;
            if (this.filter === 'All') {
                this.filter = '';
            }
        },
    },

    computed: {
        sortedImgs() {
            let filter = new RegExp(this.filter, 'i');

            return this.gallery.filter(item => item.label.match(filter));
        }
    },

    mounted() {
        this.$redrawVueMasonry();
    }
}
</script>

<style lang="scss" scoped>
    .galleryWrapper {
        position: relative;
        margin-top: var(--sectionGutter);
        background-color: #384653;
        padding: 2rem;

        header {
            color: #fff;
            text-align: center;

            & > h2 {
                font-size: var(--headerFontsize);
                letter-spacing: var(--headerLetterSpacing);

                @media(min-width: 768px) {
                    font-size: 3.8rem;
                }
            }

            & > p {
                font-size: var(--contentFontsize);
                letter-spacing: var(--contentLetterSpacing);

                @media(min-width: 768px) {
                    font-size: 2.4rem;
                }
            }
        }

        &__nav {
            display: flex;
            justify-content: center;
            padding: 2rem 0;

            & > a {
                &,
                &:link,
                &:visited {
                    padding-right: .5rem;
                    font-size: 1.2rem;
                    color: #ccc;
                    text-decoration: none;
                }
            }
        }


        &__items {
            width: 100%;
            min-height: 100vh;

            @media (min-width: 1024px) {
                width: 90rem;
                margin: auto;
            }

            //masonary styles

            .sizer {
                width: 100%;

                @media(min-width: 768px) {
                    width: 48%;
                }

                @media(min-width: 1024px) {
                    width: 31.333%;
                }
            }

            .gutter-sizer {
                width: 2%;
            }

            // end of masonary styles

            figure {
                position: relative;
                width: 100%;
                cursor: pointer;

                @media(min-width: 768px) {
                    width: 48%;
                }

                @media(min-width: 1024px) {
                    width: 31.333%;
                }

                &.modal {
                    width: 100%;
                    height: 100%;
                    position: fixed;
                    z-index: 2;
                    top: 0;
                    left: 0;
                    background-color: rgba(0,0,0,.2);

                }

                &:nth-child(odd) {
                    //padding: 2rem 0;
                }

                & > img {
                    max-width: 100%;
                }

                & > img.modal {
                    position: absolute;
                    top: 50%;
                    transform: translate(0, -50%);
                    padding: 3rem;
                }
            }
        }

        &__item {
            margin-bottom: 2%;
        }
    }


</style>
