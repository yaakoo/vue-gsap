<template>
    <transition
        appear
        name="fade"
        @before-enter="beforeEnter"
        @enter="enter"
    >
        <div class="header">
            <div class="header-title">
                <span class="header-title-text">Vue x GSAP</span>
            </div>
            <div class="links-container">
                <div class="links">
                    <a href="#">Link 1</a>
                    <a href="#">Link 2</a>
                    <a href="#">Link 3</a>
                </div>
            </div>
        </div>
    </transition>
</template>

<script>
import gsap from 'gsap'

export default {
    setup() {
        const beforeEnter = (el) => {
            console.log("Before enter")
            el.style.transform = "translateY(-60px)"
            el.style.opacity = 0
        }

        const enter = (el, done) => {
            console.log("Starting to enter")
            gsap.to(el,{
                duration:1,
                y:0,
                opacity: 1,
                ease: "bounce.out",
                onComplete: done
            })
        }
        return { beforeEnter, enter }
    }
}
</script>

<style scoped>
.header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    background-color: #2dd4bf;
    padding: 1.5rem;
}

.header-title {
    flex-shrink: 0;
    color: #ffffff;
    margin-right: 1.5rem;
}

.header-title-text {
    font-weight: 600;
    font-size: 1.5rem;
    line-height: 2rem;
    letter-spacing: -0.025em;
}

.links-container {
    width: 100%;
    display: block;
    flex-grow: 1;
}

.links a {
    display: block;
    color: #ffffff;
    margin-right: 3rem;
}

.links a:hover {
    color: #115e59;
}

@media (min-width: 1024px) {
  .links-container {
    display: flex;
    align-items: center;
    width: auto;
  }

  .links a {
    display: inline-block;
  }
}

</style>