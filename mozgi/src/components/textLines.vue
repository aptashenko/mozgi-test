<template>
    <div class="textBox" ref="text">
        <p class="textBox__text textBox__text--reversed">{{ text }}</p>
        <p class="textBox__text">{{ text }}</p>
    </div>
</template>

<script>
import '@/assets/style/animation.css'
export default {
    name: 'textLines',
    data() {
        return {
            text: 'FULL-CYCLE EVENT AGENCY FULL-CYCLE EVENT AGENCY'
        }
    },
}
</script>

<style lang="scss">

.textBox {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 100%;
    overflow: hidden;
    transform: translate(-50%, -50%) rotate(325deg);
    z-index: -1;
    &__text {
        font-size: 52px;
        line-height: 1.1;
        text-align: left;
        text-transform: uppercase;
        color: #bebebe;
        opacity: 0.1;
            text-shadow:
                -0 -1px 0 #373737,
                0 -1px 0 #373737,
                -0 1px 0 #373737,
                0 1px 0 #373737,
                -1px -0 0 #373737,
                1px -0 0 #373737,
                -1px 0 0 #373737,
                1px 0 0 #373737,
                -1px -1px 0 #373737,
                1px -1px 0 #373737,
                -1px 1px 0 #373737,
                1px 1px 0 #373737,
                -1px -1px 0 #373737,
                1px -1px 0 #373737,
                -1px 1px 0 #373737,
                1px 1px 0 #373737;
        width: 9999px;
        transform: translateX(10px);
        animation: textMove 30s linear infinite alternate;
        &--reversed {
            transform: rotateX(180deg) translateX(10px);
            animation: reversedTextMove 30s linear infinite alternate;
        }
    }
}

</style>