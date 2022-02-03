<template>
    <div class="banner">
        <transition-group
            tag="div"
            class="text-container"
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
                @before-enter="circleBeforeEnter"
                @enter="circleEnter"
            >
                <img class="circle" src="../assets/circle.svg" alt="Circle"/>
            </transition>
        </div>
    </div>
</template>

<script>
import { ref } from "vue"
import gsap from "gsap"

export default {
    setup() {
        // 表示するテキストを設定
        const lines = ref([
            { phrase: "Vue" },
            { phrase: "Meets" },
            { phrase: "GSAP" },
        ])

        // テキストが上から落ちてくるアニメーション
        const textEnter = (el, done) => {
            gsap.from(el, {
                opacity: 0,
                duration: 1,
                y: "-100%",
                ease: "bounce.out",
                // テキストを0.4秒ずつずらして上から落とす
                delay: 2 + 0.4 * (lines.value.length - el.dataset.index),
                onComplete: done,
            })
        }

        // ボールが上から落ちてくるアニメーションのスタート位置設定
        const circleBeforeEnter = (el) => {
            el.style.transform = "translateY(-100vh)"
        }

        // ボールが上から落ちて跳ねるアニメーション
        const circleEnter = (el) => {
            const tl = gsap.timeline( {delay:5} ) // アニメーションのタイムライン
            const screenWidth = window.innerWidth // 画面の横幅
            const elementWidth = el?.getBoundingClientRect().right // ボールの横幅

            // ボールのアニメーションの設定
            tl
                .to(el, {y: 350} )
                .to(el, {y:0, duration: 0.5} )
                .to(el, {y:350, duration: 1.25, ease: "bounce.out"})
                .to(el, {x: screenWidth - elementWidth - 10, duration: 2.5}, "-=1.75")
                .to(el, {x:0, duration: 1}, "+=1")
                .call(circleEnter)
        }
        return { lines, textEnter, circleEnter, circleBeforeEnter }
    }
}
</script>

<style scoped>
.banner {
    display: flex;
    justify-content: center;
    gap: 1rem;
    margin-top: 7.6rem;
}

.text-container {
    font-size: 5rem;
    line-height: normal;
}

.shape-container img {
    position: absolute
}

.circle {
    width: 9rem;
    height: 9rem;
    top: -1.2rem;
}

@media (max-width: 640px) {
    .shape-container img {
        display: none;
    }
}

@media (max-width: 1024px) {
    .circle {
        width: 7.5rem;
        height: 7.5rem;
        top: 3.5rem;
    }
}
</style>
