<template>
    <header class="header" :style="{ borderBottom: mobileMenu ? '1px solid #3636364e' : ''}">
        <div class="header__container">
            <div class="header__localization" @mouseenter="langShow = true" @mouseleave="langShow = false">
                <img class="header__tongue" src="../assets/images/tongue.png" alt="">
                <ul class="header__language" v-if="langShow">
                    <li class="header__language--item" v-for="(lang, i) of langs" :key="lang"><a href="#"
                            class="header__language--link" ref="langLink" :style="{display: langView(i) }">{{ lang }}</a>
                    </li>
                </ul>
            </div>
            <img src="../assets/images/logo.svg" class="header__logo" alt="">
            <div class="mobileMenu">
                <img class="header__burger" src="../assets/images/burger.svg" alt="" @click="mobileMenu = !mobileMenu">
                <nav class="mobileMenu__navigation" v-if="mobileMenu">
                    <ul class="mobileMenu__list">
                        <li class="mobileMenu__item">
                            <a href="#" class="mobileMenu__link">Where?</a>
                        </li>
                        <li class="mobileMenu__item">
                            <a href="#" class="mobileMenu__link">What?</a>
                        </li>
                        <li class="mobileMenu__item">
                            <a href="#" class="mobileMenu__link">Who?</a>
                        </li>
                    </ul>
                </nav>
            </div>
            <nav class="header__navigation">
                <ul class="header__list">
                    <li class="header__item header__item--first"><a href="" class="header__link">WHERE?</a></li>
                    <li class="header__item header__item--second"><a href="" class="header__link">WHAT?</a></li>
                    <li class="header__item header__item--third"><a href="" class="header__link">WHO?</a></li>
                </ul>
            </nav>
        </div>
    </header>
</template>

<script>
import '@/assets/style/animation.css'
export default {
    name: 'headerPage',
    data() {
        return {
            langs: ['UA', 'RU'],
            mobileMenu: false,
            langShow: false,
        }
    },
    methods: {
        langView(index) {
            setTimeout(() => {
                if (index === 1) {
                    this.$refs.langLink[index].style.display = 'block';
                    this.$refs.langLink[index].classList.add('RU');
                } else {
                    setTimeout(() => {
                        this.$refs.langLink[index].style.display = 'block';
                        this.$refs.langLink[index].classList.add('UA');
                    },500)
                }
            },300)
        }
    }
}
</script>

<style lang="scss">


%container {
    padding-left: 15px;
    padding-right: 15px;
    margin-left: auto;
    margin-right: auto;
}

.mobileMenu {
    display: flex;
    align-items: center;
    @media (min-width: 768px) {
        display: none;
    }
    &__navigation {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        opacity: 1;
        animation: slideBottom 250ms linear forwards;
    }
    &__list {
        display: flex;
        width: 100%;
        justify-content: space-around;
        align-items: center;
    }
    &__link {
        &:hover, &:active {
            color: #fff;
        }
    }
}
.header {
    padding-top: 20px;

    &__logo {
        margin-left: -80px;
        height: 25px;
    }
    &__container {
        @extend %container;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    &__navigation {
        @media (max-width: 767px) {
            display: none;
        }
    }
    &__item {
        z-index: 1;
        &--first {
            transform: rotate(90deg) translateY(-50%);
            position: absolute;
            top: 50%;
            left: -40px;
        }
        &--second {
            transform: rotate(90deg) translateY(-50%);
            position: absolute;
            top: 50%;
            right: -15px;
        }
        &--third {
            position: absolute;
            transform: translateY(-50%);
            bottom: 0;
            left: 50%;
        }
    }
    &__link {
        font-size: 14px;
        line-height: 1.4;
        color: #373737;
        transition: all 250ms linear;
        &:hover, &:active {
            color: #fff;
                &::before {
                        content: '';
                        position: absolute;
                        width: 100%;
                        height: 5px;
                        top: 100%;
                        left: 0;
                        border-radius: 8px;
                        background: #fff;
                        animation: linkBorder 250ms linear forwards;
                    }
        }
    }
    &__localization {
        position: relative;
        padding-right: 80px;
    }
    &__language {
        &--item {
            position: absolute;
            top: 50%;
            &:not(:last-child) {
                margin-right: 10px;
            }
        }
        &--link {
            display: none;
            transition: all 250ms linear;
            &:hover, &:active {
                color: #fff;
                    &::before {
                        content: '';
                        position: absolute;
                        width: 100%;
                        height: 5px;
                        top: 100%;
                        left: 0;
                        border-radius: 8px;
                        background: #fff;
                        animation: linkBorder 250ms linear forwards;
                    }
            }
        }
    }
}

.RU {
    animation: appearRU 250ms linear forwards;
}

.UA {
    animation: appearUA 250ms linear forwards;
}

@media (min-width: 768px) {
    .mobileMenu {
        display: none;
    }

    .header {
        padding-top: 15px;
            &__logo {
                height: 38px;
            }
            
    }
}

@media (min-width: 1200px) {
    .header {
        padding-top: 25px;

        &__logo {
            height: 46px;
        }

        &__tongue {
            width: 38px;
        }
    }
}
</style>