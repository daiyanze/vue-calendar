<template>
  <div class="__vev_calendar-wrapper">
    <cal-panel
      :calendar="calendarOptions"
      :selectedDay='selectedDay'
      @cur-day-changed="handleChangeCurDay"
      @month-changed="handleMonthChanged">
    </cal-panel>
  </div>
</template>

<script>
import { isEqualDateStr } from './utils/methods'
import CalendarPanel from './components/CalendarPanel.vue'

const inBrowser = typeof window !== 'undefined'
export default {
  name: 'vue-calendar',
  components: {
    'cal-panel': CalendarPanel
  },
  data () {
    return {
      selectedDay: ''
    }
  },
  props: {
    title: String
  },
  computed: {
    calendarOptions () {
      let dateObj = new Date()
      if (inBrowser) {
          return window.VueCalendarBarEventBus.CALENDAR_EVENTS_DATA
      } else {
        return {
          options: {
            locale: 'en', //zh
            color: ' #f29543'
          },
          params: {
              curYear: dateObj.getFullYear(),
              curMonth: dateObj.getMonth(),
              curDate: dateObj.getDate()
          }
        }
      }
    },
    calendarParams () {
      let dateObj = new Date()
      if (inBrowser) {
          return window.VueCalendarBarEventBus.CALENDAR_EVENTS_DATA.params
      } else {
        return {
          curYear: dateObj.getFullYear(),
          curMonth: dateObj.getMonth(),
          curDate: dateObj.getDate()
        }
      }
    }
  },
  created () {
    if (this.calendarParams.curEventsDate !== 'all') {
      this.handleChangeCurDay(this.calendarParams.curEventsDate)
    }
  },
  methods: {
    handleChangeCurDay (date) {
      this.selectedDay = date
      this.$emit('day-changed', {
        date: date
      })
    },
    handleMonthChanged (yearMonth) {
      this.$emit('month-changed', yearMonth)
    }
  }
}
</script>
<style lang="less">
@import "./static/style.less";
</style>
