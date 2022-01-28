<template>
    <div class="banner-container">
        <div class="shapes-container">
            <img class="circle" src="../assets/circle.svg" alt="Circle"/>
            <img class="rectangle" src="../assets/rectangle.svg" alt="Rectangle"/>
        </div>
        <div class="text-container">
            <div id="line-1">
                Vue
            </div>
            <div id="line-2">
                Meets
            </div>
            <div id="line-3">
                GSAP
            </div>
        </div>

    </div>
</template>

<style scoped>
.banner-container {
    display: flex;
    justify-content: center;
    padding-top: 3rem;
}

.banner-container > div {
    margin: 1rem;
}

.text-container {
    text-align: left;
    font-size: 5rem;
    line-height: normal;
    padding-top: 7.8rem;
}

.shapes-container img {
    position: absolute
}

.circle {
    width: 8rem;
    height: 8rem;
}

.rectangle {
    width: 8rem;
    height: 20rem;
    top: 267px;
}

@media (max-width: 640px) {
    .shapes-container img {
        display: none;
    }
}
</style>
