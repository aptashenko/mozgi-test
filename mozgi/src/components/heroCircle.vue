<template>
    <div class="circular">
        <svg viewBox="0 0 100 100">
            <path d="M 0,50 a 50,50 0 1,1 0,1 z" id="circle" />
            <circle r="6" cx="50" cy="50" fill="black" />
            <text class="circular--text">
                <textPath xlink:href="#circle">
                    showreel showreel showreel
                </textPath>
            </text>
        </svg>
    </div>
</template>

<script>
import '@/assets/style/animation.css'
export default {
    name: 'heroCircular',
}
</script>

<style lang="scss">
.circular {
    position: absolute;
    bottom: 0;
    right: 0;
    width: 90px;
    height: 90px;
    z-index: 99999;

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

</style>