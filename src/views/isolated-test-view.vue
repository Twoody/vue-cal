<template lang="pug">
//- This is an isolated test view. Just for testing purpose.
vue-cal(
  :selected-date="selectedDate"
  :events="events"
  editable-events
  twelve-hour
  style="min-height: 400px;max-height: 65vh")
</template>

<script>
import VueCal from '@/components/vue-cal'

export default {
  components: { VueCal },
  data: () => ({
    selectedDate: '2019-01-01',
    events: [
      {
        // start: '2019-01-01 00:00',
        startDate: new Date('2019-01-01T00:00'),
        // Does Work
        end: '2019-01-01 24:00',

        // Does not work
        //  endDate: new Date('2019-01-02T00:00'),

        // Gets converted to the same as directly above; Does not work
        // endDate: new Date('2019-01-01T24:00'),

        // Does not work
        // end: '2019-01-02 00:00', // Does not work
        title: 'FooBar'
      }
    ]
  }),

  methods: {
  }
}
</script>

<style lang="scss">
.v-application--wrap {min-height: 0;}
footer {display: none !important;}
</style>
