<template>
    <div class="clock">
        <div class="day-name">
            {{ time | moment('dddd') }}
        </div>
        <span class="date">
            {{ time | moment('DD.MM.YYYY') }}
        </span>
        <span class="time">
            {{ time | moment('HH:mm') }}
        </span>
    </div>
</template>

<script>
export default {
    data: () => {
        return {
            time: new Date(),
        }
    },
    created: function() {
        let data = this;
        setInterval(() => {
            data.time = new Date()
        }, 1000);
        this.time = new Date();
    }
}
</script>

<style lang="scss" scoped>
.clock {
    font-size: 30px;

    .day-name {
        font-size: 50px;
    }

    .time {
        margin-left: 15px;
    }
}
</style>
