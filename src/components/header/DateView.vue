<template>
    <div class="date">
        <h2><span class="day">{{ day }}, </span><span class="date">{{ date }}</span></h2>
        <h4 class="month"><span>{{ month }}</span></h4>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                date: '',
                day:'',
                month: ''   
            }
        },
        methods: {
            getDate() {
                let currentDate = new Date();

                // set day
                const days = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'];
                let currentDay = currentDate.getDay();
                let day = days[currentDay];
                this.day = day;

                // set date
                let date = '';

                switch(date = currentDate.getDate()) {
                    case 1:
                        date = date + "st";
                        break;
                    case 2: 
                        date = date + "nd";
                        break;
                    case 3: 
                        date = date + "rd";
                        break;
                    default: 
                        date = date + "st"
                }

                this.date = date

                // set month
                const months = ['January', 'February', 'March', 'April', 'June', 'July', 'August', 'September', 'October', 'November', 'December'];
                let currentMonth = currentDate.getMonth();
                let month = months[currentMonth];
                this.month = month;
            }
        },
        mounted(){
            this.getDate();
        }
    }
</script>

<style scoped>
    .date{
        width: fit-content;
        font-family: cairo, sans-serif;
        font-size: 1.5rem;
    }

    .day, .month{
        font-weight: 700;
        width: fit-content;
    }

    .month{
        color: #00FF75;
        font-size: 1rem;
    }

    .date{
        font-weight: 500;
    }

    h2{
        margin-bottom: 0;
        line-height: 32px;
    }
</style>