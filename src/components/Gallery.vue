<template>
    <section id="gallery" class="galleryWrapper">
        <header>
            <h2>Photo Gallery</h2>
            <p>This is a small collection of photos <br/>I find inspiring</p>
        </header>
        <div class="galleryWrapper__items">
            <nav class="galleryWrapper__nav">
                <a @click="filterBy($event)" href="#">All</a>
                <a @click="filterBy($event)" href="#">Nature</a>
                <a @click="filterBy($event)" href="#">Buildings</a>
                <a @click="filterBy($event)" href="#">Cars</a>
                <a @click="filterBy($event)" href="#">Animals</a>
            </nav>

            <figure :class="[modal ? modalContainer : '']" v-for="img in sortedImgs" :key="img.id">
                <span v-if="modal" @click="closeModal()" class="close"></span>
                <img :class="[modal ? modalItem : '']" @click="showModal($event)" :src="[modal ? imgModal : img.url]"
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
        }
    },

    computed: {
        sortedImgs() {
            let filter = new RegExp(this.filter, 'i');

            return this.gallery.filter(item => item.label.match(filter));
        }
    },

    mounted() {
        //
    }

}
</script>

<style lang="scss" scoped>
    .galleryWrapper {
        position: relative;
        padding-top: var(--sectionGutter);
        background-color: #384653;
        padding: 2rem;

        header {
            color: #fff;
            text-align: center;

            & > h2 {
                font-size: var(--headerFontsize);
                letter-spacing: var(--headerLetterSpacing);
            }

            & > p {
                font-size: var(--contentFontsize);
                letter-spacing: var(--contentLetterSpacing);
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
            figure {
                position: relative;
                width: 100%;

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
                    padding: 2rem 0;
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

        .close {
            display: block;
            position: absolute;
            top: 1rem;
            right: .5rem;
            width: 2rem;
            height: 2rem;
            cursor: pointer;

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
