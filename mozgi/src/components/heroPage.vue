<template>
    <main class="hero">
        <div class="hero__container">
            <div class="hero__blur">
                <div class="hero__backdrop">
                </div>
                <heroCircular />
            </div>
            <h2 class="hero__title" ref="title">FULL-CYCLE EVENT AGENCY</h2>
        </div>
    </main>
</template>

<script>
import heroCircular from './heroCircle.vue'

export default {
    name: 'heroPage',
    components: {
        heroCircular,
    },
    data() {
        return {
        }
    },
    computed: {
    },
    methods: {
        titleMove() {
            const halfX = this.$refs.title.getBoundingClientRect().width / 2;
            const halfY = this.$refs.title.getBoundingClientRect().height / 2;
            const centerX = halfX + this.$refs.title.getBoundingClientRect().left;
            const centerY = halfY + this.$refs.title.getBoundingClientRect().top;
            this.$refs.title.style.transform = `translate(${-halfX}px, ${-halfY}px)`;
            window.addEventListener('mousemove', e => {
                const x = (e.pageX - centerX) / 60;
                const y = (e.pageY - centerY) / 60;
                this.$refs.title.style.transform = `translate(${-halfX + x}px, ${-halfY + y}px)`;
            })
        }
    },
    mounted() {
        this.titleMove();
    }
}
</script>

<style lang="scss">


%container {
    padding-left: 15px;
    padding-right: 15px;
    margin-left: auto;
    margin-right: auto;
    width: 100%;
    height: 100%;
}

.hero {
    display: flex;
    align-items: center;
    flex-grow: 1;
    position: relative;
    &__container {
        @extend %container;
        width: 100%;
        height: 100%;
    }
    &__title {
        position: absolute;
        top: 50%;
        left: 50%;
        width: 100%;
        max-width: 375px;
        transform: translate(-50%, -50%);
        padding: 0 21px;
        text-align: center;
        font-style: normal;
        font-weight: 700;
        font-size: 34px;
        line-height: 1.1;
        text-transform: uppercase;
        color: #373737;
        z-index: 1;
    }
    &__backdrop {
        position: absolute;
        top: 50%;
        left: 50%;
        width: 294px;
        height: 294px;
        filter: blur(26px);
        transform: translate(-50%, -50%);
        z-index: 0;
        background: #FFCB46;
        border-radius: 50%;
    }
    &__blur {
        position: absolute;
        top: 50%;
        left: 50%;
        width: 245px;
        height: 315px;
        transform: translate(-50%, -50%);
    }
}

@media (min-width: 768px) {
    .hero {
        &__blur {
            width: 380px;
            height: 440px;
        }

        &__title {
        max-width: 1024px;
        font-size: 58px;
        padding: 0 100px;
        }

        &__backdrop {
            width: 482px;
            height: 482px;
            filter: blur(46px)
        }
    }
}

@media (min-width: 1200px) {
    .hero {
        &__blur {
            width: 475px;
            height: 475px;
        }

        &__title {
            max-width: 1200px;
            font-size: 82px;
            padding: 0;
        }

        &__backdrop {
            width: 578px;
            height: 578px;
            filter: blur(46px)
        }
    }
}

</style>