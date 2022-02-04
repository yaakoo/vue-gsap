<template>
    <div class="banner">
        <div class="text-container">
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
        </div>
        <div class="shape-container">
            <div class="circle"> 
                <img src="../assets/circle.svg" alt="Circle"/>
            </div>
        </div>
    </div>
</template>

<script>
import { ref } from "vue"

export default {
    setup() {
        // 表示するテキストを設定
        const lines = ref([
            { phrase: "Vue" },
            { phrase: "Meets" },
            { phrase: "GSAP" },
        ])

        return { lines }
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
    top: 20rem;
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
