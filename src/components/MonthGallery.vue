<template>
    <div class="month-gallery__wrapper">
        <month-item 
            v-for="month of currentMonthsRange"
            :key="month.id"
            :month="month"
        />
    </div>
    <div class="month-gallery__navigation">
        <div class="left" @click="left">left</div>
        <div class="right" @click="right">right</div>
    </div>
</template>

<script>
import MonthItem from '@/components/MonthItem'

export default {
    components: { MonthItem },
    data() {
        return {
            months: [
                { id: '1', name: 'October', year: 2022, monthNumber: 10},
                { id: '2', name: 'November', year: 2022, monthNumber: 11},
                { id: '3', name: 'December', year: 2022, monthNumber: 12},
                { id: '4', name: 'January', year: 2023, monthNumber: 1},
                { id: '5', name: 'February', year: 2023, monthNumber: 2},
                { id: '6', name: 'March', year: 2023, monthNumber: 3},
                { id: '7', name: 'April', year: 2023, monthNumber: 4},
                { id: '8', name: 'May', year: 2023, monthNumber: 5},
                { id: '9', name: 'June', year: 2023, monthNumber: 6},
            ], 
            currentMonthId: 1,
            currentMonthNumber: 1,
            currentYearNumber: 2023,
        }
    },
    mounted() {
        this.setCurrentMonth()
    },
    methods: {
        setCurrentMonth(monthId) {
            let date
            if (monthId) {
                const month = this.months.find(month => {
                    if (month.id == monthId) {
                        return true
                    }
                })

                date = new Date(month.year + '-' + month.monthNumber + '-' + 1)
            } else {
                date = new Date()
            }
            const currentYearNumber = date.getFullYear()
            const currentMonthNumber = date.getMonth()+1

            const {id, year, monthNumber} = this.months.find(month => {
                if (month.year == currentYearNumber && month.monthNumber == currentMonthNumber) {
                    return true
                }
            })

            this.currentMonthId = id
            this.currentYearNumber = year
            this.currentMonthNumber = monthNumber
        },
        left() {
            this.setCurrentMonth(this.currentMonthId-1)
        },
        right() {
            this.setCurrentMonth(+this.currentMonthId+1)
        }
    },
    computed: {
        currentMonthsRange() {
            return this.months.filter(month => {
                // id - не круто, чекать только по году и номеру месяца
                if (month.id == this.currentMonthId || month.id == this.currentMonthId-1 || month.id == +this.currentMonthId+1) {
                    return month  
                } else if (this.currentMonthNumber == 1 && month.monthNumber == 12 && month.year == this.currentYearNumber-1) {
                    return month
                }
            })
        }
    }
}
</script>

<style scoped>
.month-gallery__wrapper {
    display: flex;
}
.month-gallery__navigation {
    display: flex;
    justify-content: space-between;
}
.left, .right {
    padding: 20px;
    background-color: #15151d;
    border-radius: 12px;
    cursor: pointer;
}
</style>