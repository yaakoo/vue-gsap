<template>
    <div class="panels-container">
        <div class="panels-grid">
            <div class="card">Panel 1</div>
            <div class="card">Panel 2</div>
            <div class="card">Panel 3</div>
            <div class="card">Panel 3</div>
        </div>
    </div>
</template>

<style scoped>
.panels-container {
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

.card {
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