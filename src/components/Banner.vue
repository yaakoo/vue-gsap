<template>
    <div class="banner">
        <!--ここにtransitionを追加-->
        <transition-group
            tag="div"
            appear
            @before-enter="textBeforeEnter"
            @enter="textEnter"
            class="text-container"
        >
            <div
                v-for="(line, index) in lines"
                :key="line.phrase"
                class="text"
                :data-index="index"
            >
                <div>
                    {{ line.phrase }}
                </div>
            </div>
        </transition-group>
        <div class="shape-container">
            <transition
                appear
                @before-enter="ballBeforeEnter"
                @enter="ballEnter"
            >
                <img class="circle" src="../assets/circle.svg" alt="Circle"/>
            <!--ここでtransitionをクローズ-->
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
            { phrase: "Inpact" },
            { phrase: "Meets" },
            { phrase: "GSAP" },
        ])
        // ここにアニメーションを追加
        // テキストのスタート設定
        const textBeforeEnter = (el) => {
            gsap.set(el, {
                y: "-100%",
                opacity: 0
            })
        }
        // テキストが上から下へ移動するアニメーション
        const textEnter = (el, done) =>{
            gsap.to(el, {
                opacity: 1,
                duration: 1.2,
                y: "0",
                ease: "bounce.out",
                // テキストを0.4秒ずつずらして上から下へ移動
                delay: 2 + 0.4 * (lines.value.length - el.dataset.index),
                onComplete: done,
            })
        }
        // ボールが上から下へ移動するアニメーションのスタート位置設定
        const ballBeforeEnter = (el) => {
            gsap.set(el, {
                y: "-150%"
            })
        }
        // ボールが上から下がって跳ねるアニメーション
            const ballEnter = (el, done) => {
                const tl = gsap.timeline({ delay: 5, onComplete: done }) //アニメーションのタイムライン
                const screenWidth = window.innerWidth //画面の横幅
                const elementWidth = document.querySelector(".circle").getBoundingClientRect().right //ボールの横幅
            // ボールのアニメーションの設定
            tl
                .to(el, { y: 350 })
                .to(el, { y: 0, duration: 0.5 })
                .to(el, { y: 350, duration: 1.25, ease: "bounce.out" })
                .to(el, { x: screenWidth - elementWidth - 10, duration: 2.5 }, "-=1.75")
                .to(el, { x: 0, duration: 1 }, "+=1")
        }
        return { lines, textEnter, textBeforeEnter, ballBeforeEnter, ballEnter }
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

.text {
    font-size: 5rem;
    line-height: normal;
}

.circle {
    position: absolute;
    width: 9rem;
    height: 9rem;
    top: -1.2rem; /** アニメーション適用後に-1.2remに編集 */
}

@media (max-width: 640px) {
    .circle {
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
