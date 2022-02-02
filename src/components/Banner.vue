<template>
    <div class="banner">
        <transition-group
            class="text-container"
            tag="div"
            appear
            @enter="textEnter"
        >
            <div
                v-for="(line, index) in lines"
                :key="line.phrase"
                class="card"
                :data-index="index"
            >
                <div>
                    {{ line.phrase }}
                </div>
            </div>
        </transition-group>
        <div class="shape-container">
            <transition
                tag="div"
                appear
                @enter="circleEnter"
            >
                <img class="circle" src="../assets/circle.svg" alt="Circle"/>
            </transition>
        </div>
    </div>
</template>

<script>
import { ref } from 'vue'
import gsap from 'gsap'

export default {
    setup() {
        const lines = ref([
            { phrase: "Vue" },
            { phrase: "Meets" },
            { phrase: "GSAP" },
        ])

        const textEnter = (el, done) => {
            gsap.from(el, {
                duration: 1,
                opacity: 0,
                y: '-100%',
                ease: "bounce.out",
                onComplete: done,
                delay: 2 + 0.4 * (lines.value.length - el.dataset.index)
            })
        }

        const circleEnter = (el) => {
            gsap.set(el, {   
                y: '-100vh'
            })
            const tl = gsap.timeline({delay:5})
            tl
                .to(el, {y: 350})
                .to(el, {y:0, duration: 0.5})
                .to(el, {y:350, duration: 1.25, ease: "bounce.out"})
                .to(el, {x:"+=450", duration: 2.5}, "-=1.75")
                .to(el, {x:0, duration: 1}, "+=1")
                .call(circleEnter);
        }
        return { lines, textEnter, circleEnter }
    }
}
</script>

<style scoped>
.banner {
    display: flex;
    justify-content: center;
}

.banner > div {
    margin: 1rem;
    padding-left: 5.5rem;
    width: 7.3rem;
}

.text-container {
    text-align: left;
    font-size: 5rem;
    line-height: normal;
    padding-top: 7.6rem;
}

.shape-container img {
    position: absolute
}

.circle {
    width: 9rem;
    height: 9rem;
    top: -0.2rem;
}

@media (max-width: 640px) {
    .shape-container img {
        display: none;
    }
}
</style>
