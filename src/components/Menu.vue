<template>
    <nav :class="[nav, darkenMenu ? navDark : '']">
        <div @click="$emit('close-menu')" class="navigation__burger">
            <span
            :class="[menuActive ? close : burger, darkenMenu ? burgerWhite : '']"
            ></span>
        </div>
        <transition name="slideDown">
        <div v-show="menuActive" class="navigation__list">
            <ul :class="[darkenMenu ? colorWhite : '']">
                <li class="navigation__item">
                    <a class="navigation__link" href="#">
                        <i class="fas fa-home"></i>
                        home
                    </a>
                </li>
                <li class="navigation__item">
                    <a class="navigation__link" href="#about">
                        <i class="fas fa-user-astronaut"></i>
                        about me
                    </a>
                </li>
                <li class="navigation__item">
                    <a @click="scrollDown" class="navigation__link" href="#gallery">
                        <i class="fas fa-images"></i>
                        gallery
                    </a>
                </li>
                <li class="navigation__item">
                    <a class="navigation__link" href="#">
                        <i class="fas fa-envelope"></i>
                        contact
                    </a>
                </li>
            </ul>
        </div>
        </transition>
    </nav>
</template>

<script>
export default {
    data() {
        return {
            burger: 'navigation__burger--active',
            close: 'navigation__burger--close',
            burgerWhite:  'navigation__burger--white',
            nav: 'navigation',
            navDark: 'navigation--dark',
            colorWhite: 'colorWhite',
            darkenMenu: false,
        }
    },

    props: {
        menuActive: {
            type: Boolean,
            required: true,
        }
    },

    mounted() {
        this.$root.$on('in-View-Port', (e) => {
            this.darkenMenu = !e;
        })
    },

    methods: {
        scrollDown() {
            document.getElementById('gallery').scrollIntoView({
                behavior: 'smooth',
                block: 'end',
            });

            console.log(document.getElementById('gallery'));
        }
    }
}
</script>

<style lang="scss" scoped>
    .navigation {
        height: 4.5rem;
        position: fixed;
        top: 0px;
        z-index: 2;
        width: 100%;
        transition: background-color .3s;

        @media(min-width: 768px) {
            height: 6rem;
        }

        &--dark {
            background-color: #384653;
        }

        &__burger {
            position: absolute;
            top: 50%;
            right: 2%;
            transform: translate(0%, -50%);
            width: 2.5rem;
            height: 2.5rem;
            cursor: pointer;
            z-index: 5;

            @media(min-width: 768px) {
                width: 3.9rem;
                height: 3rem;
            }

            @media(min-width: 1024px) {
                display: none;
            }

            &--active {
                position: relative;
                display: inline-block;
                width: 1.4rem;
                height: .2rem;
                background-color: #384653;

                @media(min-width: 768px) {
                    width: 3rem;
                    height: .4rem;
                }

                &::before,
                &::after {
                    content: '';
                    width: 1.8rem;
                    height: .2rem;
                    background-color: inherit;
                    position: absolute;
                    transition: transform .5s;

                     @media(min-width: 768px) {
                        width: 3.4rem;
                        height: .4rem;
                    }

                }

                &::before {
                    top: .6rem;

                    @media(min-width: 768px) {
                        top: 1rem;
                    }
                }

                &::after {
                    bottom: .6rem;

                    @media(min-width: 768px) {
                        bottom: 1rem;
                    }

                }
            }

            &--close {
                position: relative;
                display: inline-block;

                &::before,
                &::after {
                    content: '';
                    width: 1.8rem;
                    height: .2rem;
                    background-color: #fff;
                    position: absolute;
                    transition: transform .5s;

                    @media(min-width: 768px) {
                        width: 3.6rem;
                        height: .4rem;
                    }

                }

                &::before {
                    top: 0px;
                    transform: rotate(225deg);
                }

                &::after {
                    top: 0px;
                    transform: rotate(-225deg);
                }
            }

            &--white {
                background-color: #fff;
            }
        }

        &__list {
            display: flex;
            justify-content: center;
            height: 45vh;
            background-color: #384653;

            & > ul {
                display: flex;
                flex-direction: column;
                align-items: flex-start;
                justify-content: center;
                list-style: none;


                 @media(min-width: 1024px) {
                    width: 55rem;
                    height: 100%;
                    flex-direction: row;
                    align-items: center;
                    justify-content: space-evenly;
                    color: #384653;
            }
            }

            @media(min-width: 1024px) {
                display: flex !important;
                justify-content: flex-end;
                background-color: transparent;
                height: 100%;
            }
        }

        &__item {
            padding: 1.6rem 0;

            @media(min-width: 768px) {
                padding: 2.2rem 0;
            }

            @media(min-width: 1024px) {
                padding: 0 0;
            }
        }

        &__link {
            font-size: 20px;
            color: #fff;

            &,
            &:link,
            &:visited {
                text-decoration: none;

            }

            & > i {
                padding-right: 4px;
                transition: all .3s;
            }

            &:hover {

                i {
                    color: #942130;
                }
            }

            @media(min-width: 768px) {
                font-size: 2.8rem;
            }

            @media(min-width: 1024px) {
                font-size: 1.6rem;
                color: inherit;
            }
        }

        // SLIDEDOWN ANIMATION

        .slideDown-enter-active,
        .slideDown-leave-active {
            transition: all .2s;
        }

        .slideDown-enter {
            transform: translateY(-20rem);
        }

        .slideDown-leave-to {
            transform: translateY(-30rem);
            opacity: 0;
        }

        .colorWhite {
            color: #fff;
        }
    }
</style>
