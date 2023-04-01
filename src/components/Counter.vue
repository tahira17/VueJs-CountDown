<template>
    <div v-if="loaded">
        <section class="text-3xl flex justify-center content-center flex-col mx-auto text-center">
            <h5 v-if="!expired">TIME REMAINING</h5>
            <h5 v-else>TIME OVER</h5>

        </section>
        <section class="text-6xl flex justify-center content-center">
            <div class="days mr-2 relative">
                {{ displayDays }}
                <div class="label text-sm relative bottom-0">days</div>
            </div>
            <span class= "line-height: 1.60" >:</span>
            <div class="hours mx-2 relative">
                {{ displayHours }}
                <div class="label text-sm absolute bottom-0">Hours</div>
            </div>
            <span class= "line-height: 1.60" >:</span>
            <div class="minutes mx-2 relative">
                {{ displayMinutes }}
                <div class="label text-sm absolute bottom-0">Minutes</div>
            </div>
            <span class= "line-height: 1.60" >:</span>
            <div class="seconds ml-2 relative">
                {{ displaySeconds }}
                <div class="label text-sm absolute bottom-0">Seconds</div>
            </div>
        </section>
    </div>
</template>

<script>
export default {
    props: [
        'year', 'month', 'date', 'hour', 'minute', 'second', 'milisecond'
    ],

    data: () => ({
        displayDays: 0,
        displayHours: 0,
        displayMinutes: 0,
        displaySeconds: 0,
        loaded:false,
        expired:false

    }),
    computed: {
        _seconds: () => 1000,
        _minutes() {
            return this._seconds * 60;
        },
        _hours() {
            return this._minutes * 60;
        },
        _days() {
            return this._hours * 24;
        },
        end() {
        return new Date
            (
               
            this.year,
                this.month,
              
                this.date,
                this.hour,
                this.minute,
                this.second,
                this.milisecond
            );
            
    },
  
    },
    mounted() {
        this.showRemaining()
    },
    methods: {
        formatNumber: num => (num < 10 ? "0" + num : num),
        showRemaining() {
            const timer = setInterval(() => {
                const now = new Date();
                console.log(now)
                // const end = new Date(2023, 3, 25, 2, 10, 10)
                const distance = this.end.getTime() - now.getTime()

                if (distance < 0) {
                    clearInterval(timer)
                    this.expired=true
                    this.loaded=true
                    return
                }

                const days = Math.floor(distance / this._days);
                const hours = Math.floor((distance % this._days) / this._hours);

                const minutes = Math.floor((distance % this._hours) / this._minutes);
                const seconds = Math.floor((distance % this._minutes) / this._seconds);
                this.displayMinutes = this.formatNumber(minutes);
                this.displaySeconds = this.formatNumber(seconds);

                this.displayHours = this.formatNumber(hours)
                this.displayDays = this.formatNumber(days);
                this.loaded=true
            }, 1000);
        }
    }
};
</script>

<style scoped>
.seconds {
    max-width: 60px;
}

</style>