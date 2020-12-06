<template>
  <form ref="create_event" class="create_event">
    <input type="text"
           name="name_event"
           placeholder="Название мероприятия"
           v-model="eventName"
    />
    <input type="date"
           name="date_start"
           v-model="startDate"/>
    <input type="time"
           name="time_start"
           v-model="startTime"
    />
    <input type="time"
           name="time_end"
           v-model="endTime"/>
    <button @click.prevent="saveEvent()">Сохранить мероприятие</button>
  </form>
</template>

<script>
export default {
  name: 'CreateEventForm',
  props: ['changeDate'],
  data() {
    return {
      eventName: '',
      startDate: '',
      startTime: '',
      endTime: '',
    };
  },
  watch: {

    changeDate: {
      immediate: true,
      // eslint-disable-next-line no-unused-vars
      handler(val, oldVal) {
        this.startDate = val;
      },
    },
  },
  methods: {
    saveEvent() {
      const formData = {
        title: this.eventName,
        date_start: this.startDate,
        start_time: this.startTime,
        end_time: this.endTime,
      };
      this.$store.dispatch('createEvent', formData);
      this.eventName = '';
      this.startDate = '';
      this.startTime = '';
      this.endTime = '';
    },
    updateDay(date) {
      this.startDate = date;
    },

  },

};
</script>

<style lang="scss" scoped>
.create_event {
  display: flex;
  flex-direction: column;
}
</style>
