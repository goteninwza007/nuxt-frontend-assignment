<template>
    <div class="carousel">
        <div class="carousel-main">
            <img :src="images[activeIndex]" alt="active image" />
        </div>

        <div class="carousel-thumbs-wrapper">
            <button class="thumb-nav prev" :class="{ disabled: isFirst }" @click="prev">‹</button>

            <div class="carousel-thumbs" ref="thumbs">
                <div
                    v-for="(img, index) in images"
                    :key="index"
                    class="thumb"
                    :class="{ active: index === activeIndex }"
                    @click="setActive(index)"
                >
                    <img :src="img" />
                </div>
            </div>

            <button class="thumb-nav next" :class="{ disabled: isLast }" @click="next">›</button>
        </div>
    </div>
</template>

<script lang="ts">
export default {
    props: {
        images: {
            type: Array as () => string[],
            required: true
        }
    },

    data() {
        return {
            activeIndex: 0
        }
    },

    methods: {
        setActive(index: number) {
            this.activeIndex = index
            this.scrollToActive()
        },

        next() {
            if (this.activeIndex < this.images.length - 1) {
                this.activeIndex++
                this.scrollToActive()
            }
        },

        prev() {
            if (this.activeIndex > 0) {
                this.activeIndex--
                this.scrollToActive()
            }
        },

        scrollToActive() {
            const thumbs = this.$refs.thumbs as HTMLElement
            const activeThumb = thumbs.children[this.activeIndex] as HTMLElement

            if (activeThumb) {
                activeThumb.scrollIntoView({
                    behavior: 'smooth',
                    inline: 'center',
                    block: 'nearest'
                })
            }
        }
    },
    computed: {
        isLast() {
            return this.activeIndex === this.images.length - 1
        },

        isFirst() {
            return this.activeIndex === 0
        }
    }
}
</script>
