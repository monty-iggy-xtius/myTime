<template>
    <div class="time-div">
        <p>{{ current_time }}</p>
        <p>{{ current_date }}</p>
    </div>
</template>
<script>
export default {
    name: 'TimeDisplay',
    data() {
        return {
            current_time: "Syncing...",
            current_date: new Date().toLocaleDateString()
        }
    },
    mounted() {
        // change the time label every 1s after the component is mounted
        setInterval(() => {
            this.displayCurrentTime()
        }, 1000)
    },
    methods: {
        displayCurrentTime: function() {
            // 24 hr format options
            const time_options = {
                hour12: false,
                hour: '2-digit',
                minute: '2-digit',
                second: '2-digit'
            };
            // update current time to the current time including seconds
            this.current_time = new Date().toLocaleTimeString('en-US', time_options);

        }
    }

}
</script>
<style lang="css" scoped>
.time-div {
    padding: 13px 12px;
    color: #00B612;
    cursor: none;
}

.time-div p:nth-child(1) {
    font-size: 7rem;
    letter-spacing: 1px;
    font-weight: 600;
}

.time-div p:nth-child(2) {
    margin-top: 10px;
    font-size: 2rem;
    font-weight: 400;
}



@media only screen and (max-width: 700px) {
    .time-div p:nth-child(1) {
        font-size: 5rem;
    }
}
</style>