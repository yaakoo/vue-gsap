<template>
    <div class="panels">
        <div class="panels-grid">
            <div
                v-for="(panel, index) in panels"
                :key="panel.name"
                class="panel"
                :data-index="index"
            >
                <div>{{ panel.name }}</div>
            </div>
        </div>
    </div>
</template>

<script>
import { ref } from "vue"

export default {
    setup() {
        // 表示するパネルの設定
        const panels = ref([
            { name: "Panel 1" },
            { name: "Panel 2" },
            { name: "Panel 3" },
            { name: "Panel 4" }
        ])

        // アニメーションコードをここに追加 
        return { panels }
    }
}
</script>

<style scoped>
.panels {
    padding-top: 1rem;
    display: flex;
    align-items: center;
    justify-items: center;
}

.panels-grid {
    display: grid;
    margin: 0 auto;
    grid-gap: 1rem;
    max-width: 1200px;
}

.panel {
    height: 14rem;
    width: 12rem;
    text-align: center;
    border: 4px solid #2dd4bf;
    border-radius: 0.375rem;
}

@media (min-width: 640px) {
  .panels-grid { grid-template-columns: repeat(2, 1fr); }
}

@media (min-width: 1024px) {
  .panels-grid { grid-template-columns: repeat(4, 1fr); }
}
</style>