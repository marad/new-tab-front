<template>
    <div class="nearest-events">
        <div v-for="event in events" :key="event.id" class="story">
        <div class="event">
            <div class="time start">
                {{ event.startTime | moment('HH:mm') }}
            </div>
            <div class="time end">
                {{ event.endTime | moment('HH:mm') }}
            </div>
            <div class="date">
                <!-- {{ event.startTime | date:'dd E' }} -->
                {{ event.startTime | moment('D ddd') }}
            </div>
            <div class="title">{{ event.summary }}</div>
            <div class="location">{{ event.location }}</div>
        </div>
    </div>
</div>

</template>

<script>
export default {
    data: () => {
        return {
            events: []
        }
    },
    mounted: function() {
        let data = this;
        fetch("http://localhost:8000/events")
            .then(resp => resp.json())
            .then(events => {
                console.log(events)
                data.events = events.sort((a, b) => {
                    return new Date(a.startTime) - new Date(b.startTime)
                })
            })
    }
}
</script>

<style lang="scss" scoped>
.popper {
    visibility: hidden;
    //border-radius: 5px;
    //border: 1px solid ;
    background-color: rgba(255, 255, 255, 0.5);
    padding: 8px;
}


.nearest-events {
    .event {
        cursor: pointer;
        display: grid;
        grid-template-areas:
        "a d"
        "b d"
        "c e";

        grid-template-columns: 60px auto;
        grid-template-rows: auto;

        padding-bottom: 10px;

        .title {
            font-size: 18px;
            // margin-bottom: 5px;
            grid-area: d;
            align-content: baseline;
        }

        .time {
            font-size: 13px;
        }

        .start {
            grid-area: a;
        }

        .end {
            grid-area: b;
        }

        .date {
            color: #555;
            font-size: 12px;
            // text-align: right;
            grid-area: c;
        }

        .location {
            grid-area: e;
            font-size: 12px;
        }

    }
}
</style>

