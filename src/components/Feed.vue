<template>
    <div class="feed">
        <div class="hn">
            <h1>Hackernews Top Stories</h1>

            <div v-for="item in feed" :key="item.title" class="story">
                <a v-bind:href="item.url">
                    {{ item.title }}
                </a>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data: () => {
        return {
            feed: []
        }
    },
    mounted: function() {
        let data = this;
        fetch("http://localhost:8000/feed")
            .then(resp => resp.json())
            .then(feed => {
                data.feed = feed
            })
    }
}
</script>

<style lang="scss" scoped>
.feed .story {
    font-size: 18px;
    margin-bottom: 10px;
}
</style>

