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
                    <a class="navigation__link" href="#">
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
    }
}
</script>

<style lang="scss" scoped>
    .navigation {
        height: 45px;
        position: fixed;
        top: 0px;
        z-index: 2;
        width: 100%;
        transition: background-color .3s;

        @media(min-width: 768px) {
            height: 60px;
        }

        &--dark {
            background-color: #384653;
        }

        &__burger {
            position: absolute;
            top: 50%;
            right: 2%;
            transform: translate(0%, -50%);
            width: 25px;
            height: 25px;
            cursor: pointer;
            z-index: 5;

            @media(min-width: 768px) {
                width: 39px;
                height: 30px;
            }

            @media(min-width: 1024px) {
                display: none;
            }

            &--active {
                position: relative;
                display: inline-block;
                width: 14px;
                height: 2px;
                background-color: #384653;

                @media(min-width: 768px) {
                    width: 30px;
                    height: 4px;
                }

                &::before,
                &::after {
                    content: '';
                    width: 18px;
                    height: 2px;
                    background-color: inherit;
                    position: absolute;
                    transition: transform .5s;

                     @media(min-width: 768px) {
                        width: 34px;
                        height: 4px;
                    }

                }

                &::before {
                    top: 6px;

                    @media(min-width: 768px) {
                        top: 10px;
                    }
                }

                &::after {
                    bottom: 6px;

                    @media(min-width: 768px) {
                        bottom: 10px;
                    }

                }
            }

            &--close {
                position: relative;
                display: inline-block;

                &::before,
                &::after {
                    content: '';
                    width: 18px;
                    height: 2px;
                    background-color: #fff;
                    position: absolute;
                    transition: transform .5s;

                    @media(min-width: 768px) {
                        width: 36px;
                        height: 4px;
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
                    width: 550px;
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
            padding: 16px 0;

            @media(min-width: 768px) {
                padding: 22px 0;
            }

            @media(min-width: 1024px) {
                padding: 0px 0px;
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
                font-size: 28px;
            }

            @media(min-width: 1024px) {
                font-size: 16px;
                color: inherit;
            }
        }

        // SLIDEDOWN ANIMATION

        .slideDown-enter-active,
        .slideDown-leave-active {
            transition: all .2s;
        }

        .slideDown-enter {
            transform: translateY(-200px);
        }

        .slideDown-leave-to {
            transform: translateY(-300px);
            opacity: 0;
        }

        .colorWhite {
            color: #fff;
        }
    }
</style>
