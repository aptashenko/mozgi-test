<template>
    <div class="wrapper">
        <header class="header">
            <div class="header__localization">
                <img class="header__tongue" src="../assets/images/tongue.png" alt="">
            </div>
            <img class="header__logo" src="../assets/images/logo.svg" alt="">
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
            <div class="hero__circle"></div>
            <h1 class="hero__title">FULL-CYCLE EVENT AGENCY</h1>
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
        </main>
    </div>
</template>

<script>
export default {
    name: 'mainPage',
    data() {
        return {
            mobileMenu: false,
        }
    },
}
</script>

<style lang="scss">
.wrapper {
}
.header {
    display: flex;
    position: relative;
    justify-content: space-between;
    width: 100%;
    padding: 0 15px;
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
        text-decoration: none;
        color: inherit;
    }
}

.hero {
    padding: 0 15px;
    &__background {
        position: relative;
    }
    &__circle {
        position: absolute;
        top: 50%;
        left: 50%;
        background: #FFCB46;
        filter: blur(26px);
        height: 294px;
        width: 294px;
        border-radius: 50%;
        transform: translate(-50%, -50%);
    }
    &__title {
        position: absolute;
        top: 50%;
        left: 50%;
        font-style: normal;
        font-weight: 700;
        font-size: 34px;
        line-height: 1.1;
        text-align: center;
        text-transform: uppercase;
        transform: translate(-50%, -50%);
        width: 333px;
    }
        &__circular {
            position: absolute;
            bottom: 25%;
            right: 22%;
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

    50% {
        transform: rotate(-180deg);
    }

    100% {
        transform: rotate(-360deg);
    }
}
</style>