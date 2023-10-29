<template>
  <div class="day column" @click="setActiveDay(day.id)">
  <div class="day-banner has-text-centered">{{ day.abbvTitle }}</div>
    <div class="day-details">
    <div class="day-number">{{ day.id }}</div>
    <CalendarEvent v-for="event in day.events"
        :key="day.events.indexOf(event)"
        :event="event"
        :day="day" />
    </div>
  </div>
</template>

<script>
import { store } from "../store.js";
import CalendarEvent from './CalendarEvent.vue';

    export default {
        name: 'CalendarDay',
        props: ['day'],
        methods: {
         setActiveDay (dayId) {
           store.setActiveDay(dayId);
         }
        },
        components: {
           CalendarEvent
        },
    }
</script>

<style lang="scss" scoped>
   .day {
       background-color: #4A4A4A;
       color: #FFF;
       border-left: 1px solid #8F8F8F;
       border-bottom: 1px solid #8F8F8F;
       border-radius: 4.4px;
       font-size: 12px;
       cursor: pointer;
       &:hover {
          background: darken(#4A4A4A,3%);
       }
       .day-banner {
           background-color: #333333;
           color: #FFF;
           padding: 10px;
           text-transform: uppercase;
           letter-spacing: 1px;
           font-size: 12px;
           font-weight: 600;
        }
        .day-details {
           padding: 10px;
        }
        &:last-child {
           border-right: 1px solid #8F8F8F;
        }
        .day-event {
           margin-top: 6px;
           margin-bottom: 6px;
           display: block;
           color: #4C4C4C;
           padding: 5px;
           border-radius: 4.4px;
           .details {
              display: block;
            }
            .icons .fa {
               padding: 0 2px;
               font-size: .8rem;
            }
            input {
               background: none;
               border: 0;
               border-bottom: 1px solid #FFF;
               width: 100%;
               &:focus {
                outline: none;
               }
            }
        }
    }
</style>