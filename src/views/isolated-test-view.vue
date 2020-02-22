<template lang="pug">
//- This is an isolated test view. Just for testing purpose.
div
  button(type='button' class='stylin' @click="changeView()") Error Prone
  vue-cal.vuecal--blue-theme(
    :selected-date="selectedDate"
    default-view="week"
    :events="events"
    :time-from="8 * 60"
    :time-to="20 * 60"
    :hide-weekdays="daysDisplayed"
    hideTitleBar
    hideViewSelector
    style="min-height: 400px;max-height: 65vh")
</template>

<script>
import VueCal from '@/components/vue-cal'

const now = new Date()

export default {
  components: { VueCal },
  data: () => ({
    hiddenDays: false,
    selectedDate: now,
    events: [
      {
        startDate: now.subtractHours(24),
        endDate: now.subtractHours(20),
        title: 'Event 1'
      },
      {
        startDate: now.subtractHours(3),
        endDate: now.subtractHours(1),
        title: 'Event 2'
      }
    ]
  }),

  computed: {
    daysDisplayed () {
      if (this.hiddenDays) {
        return [6, 7]
      }
      return []
    }
  },
  methods: {
    log (...params) {
      console.log(params)
    },
    changeView () {
      this.hiddenDays = !this.hiddenDays
    }
  }
}
</script>

<style lang="scss">
.stylin {
  background-color: red;
  font-size: 50px;
}
.vuecal__event {
  background-color: rgba(160, 220, 255, 0.5);
  border: 1px solid rgba(0, 100, 150, 0.15);
}
.business-hours {background-color: rgba(255, 255, 0, 0.2);}
.v-application--wrap {min-height: 0;}
footer {display: none !important;}
</style>
