<template>
    <div class="wrapper">
        <header class="header">
            <div class="header__localization" @mouseenter="langShowOpacity()">
                <img class="header__tongue" src="../assets/images/tongue.png" alt="">
                <ul class="header__language" v-if="langShow">
                    <li class="header__language--item" ref="langOption" v-for="lang of langs" :key="lang"><a href="#"
                            class="header__language--link" @click="langHideOpacity()">{{lang}}</a>
                    </li>
                </ul>
            </div>
            <img src="../assets/images/logo.svg" class="header__logo" alt="">
            <img class="header__burger" src="../assets/images/burger.svg" alt="" @click="mobileMenu = !mobileMenu">
            <div class="mobileMenu" v-if="mobileMenu">
                <nav class="mobileMenu__navigation">
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
        </header>
        <main class="hero">
            <div class="hero__background">
                <div class="hero__backdrop"></div>
                <div class="hero__circular">
                    <svg viewBox="0 0 100 100">
                        <path d="M 0,50 a 50,50 0 1,1 0,1 z" id="circle" />
                        <circle r="6" cx="50" cy="50" fill="black" />
                        <text class="hero__circular--text">
                            <textPath xlink:href="#circle">
                                showreel showreel showreel
                            </textPath>
                        </text>
                    </svg>
                </div>
                <h2 class="hero__title" ref="title">FULL-CYCLE EVENT AGENCY</h2>
            </div>
        </main>
    </div>
</template>

<script>
export default {
    name: 'mainPage',
    data() {
        return {
            langs: ['UA', 'RU'],
            mobileMenu: false,
            langShow: false,
        }
    },
    methods: {
        langShowOpacity() {
            this.langShow = true;
            setTimeout(() => {
                if (this.langShow) {
                    let langIdx = -1;
                    let id = setInterval(() => {
                        if (langIdx <= this.$refs.langOption.length-2) {
                            langIdx += 1;
                            this.$refs.langOption[langIdx].style.opacity = 1;
                        } else {
                            clearInterval(id)
                        }
                        }, 100)
                }
            },500)
        },
        langHideOpacity() {
            setTimeout(() => {
                if (this.langShow) {
                    let langIdx = this.$refs.langOption.length;
                    let id = setInterval(() => {
                        if (langIdx > 0) {
                            langIdx -= 1;
                            this.$refs.langOption[langIdx].style.opacity = 0;
                        } else {
                            clearInterval(id);
                        }
                    }, 100)
                }
            },500)
        },
    },
}
</script>

<style lang="scss">
.wrapper {
    display: flex;
    flex-direction: column;
    height: 100%;
    z-index: 1;
}
.header {
    display: flex;
    position: relative;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    padding: 0 15px;
    &__localization {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding-left: 15px;
    }
    &__language {
        position: absolute;
        left: 70px;
        list-style: none;
        display: flex;
        &--link {
            color: #363636;
            font-size: 12px;
        }
        &--item {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 34px;
            height: 34px;
            border: 1px solid #363636;
            border-radius: 50%;
            opacity: 0;
            transition: opacity 250ms linear;
            &:not(:last-child) {
                margin-right: 5px;
            }
        }
    }
}

.mobileMenu {
    position: absolute;
    top: 100%;
    left: 0;
    width: 100%;
    background: #bebebe;
    border-top: 1px solid rgba(0, 0, 0, 0.134);
    &__navigation {
        padding: 20px 0;
    }
    &__list {
        display: flex;
        justify-content: space-around;
        list-style: none;
    }
    &__link {
        position: relative;
        text-decoration: none;
        color: inherit;
        &:hover, &:focus {
            color: #fff;
            &::after {
                content: '';
                position: absolute;
                width: 0%;
                height: 5px;
                top: 100%;
                left: 0;
                border-radius: 12px;
                background: #fff;
                animation: linkBorder 250ms linear forwards;
            }
        }
    }
}

.hero {
    display: flex;
    flex-grow: 1;
    padding: 0 15px;
    justify-content: center;
    align-items: center;
    &__background {
        position: relative;
        width: 294px;
        height: 294px;
    }
    &__backdrop {
        width: 100%;
        height: 100%;
        filter: blur(20px);
        border-radius: 50%;
        background: #ffcb46;
    }
    &__title {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: fit-content;
        text-align: center;
    }
    &__circular {
        position: absolute;
        bottom: 0;
        right: 0;
        width: 90px;
        height: 90px;

        & path {
            fill: none;
        }

        & svg {
            display: block;
            overflow: visible;
        }

        &--text {
            fill: #fff;
            font-size: 12px;
        }

        &:hover {
            animation: rotate 10s infinite linear;
        }
    }
}

@keyframes rotate {
    0% {
        transform: rotate(0deg)
    }

    100% {
        transform: rotate(-360deg);
    }
}
@keyframes linkBorder {
    0% {
        width: 0%;
    }
    100% {
        width: 100%;
    }
}
</style>