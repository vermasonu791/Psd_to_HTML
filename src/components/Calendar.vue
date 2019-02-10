<template>
  <div class="calendar-area">
    <div class="calendar">
      <v-date-picker v-model="picker" :reactive="reactive"></v-date-picker>
      <div class="event-sub">
        <div class="event-heading">Upcoming Event-Submission</div>
        <div class="spacer"></div>
        <div class="deadline">Deadline</div>
      </div>

      <div class="submit-date">
        <div class="topic" v-for="(event,index) in event" :key="index">
          <div class="topic-name">{{event.name}}</div>
          <div class="spacer"></div>
          <div class="time">{{event.time}}</div>
        </div>
       
      </div>
      <div class="event-sub">
        <div class="event-heading">Upcoming Event-Exam</div>
        <div class="spacer"></div>
        <div class="deadline">Time</div>
      </div>
      <div class="submit-date">
        <div class="date">20 April 2013</div>
        <div class="topic" v-for="exam in exam" :key="exam.id">
          <div class="topic-name">{{exam.exam}}</div>
          <div class="spacer"></div>
          <div class="time">{{exam.time}}</div>
        </div>
      </div>
      <div class="event-sub" v-show="show">
        <div class="event-heading">Upcoming Events</div>
        <div class="spacer"></div>
        <div class="deadline">Time</div>
      </div>
      <div class="submit-date" v-show="show">
        <div class="date">20 April 2013</div>
        <div class="topic" v-for="(event,i) in exam" :key="i">
          <div class="topic-name">{{event.exam}}</div>
          <div class="spacer"></div>
          <div class="time">{{event.time}}</div>
        </div>
      </div>
      <div class="down-arrow">
        <button @click="showEvent">
          <v-icon v-show="arrowdown">arrow_drop_down</v-icon>
          <v-icon v-show="show">arrow_drop_up</v-icon>
        </button>
      </div>
    </div>
    <div class="recently-shared">
      <div class="heading">Recently shared Resources</div>
      <div class="resources">
          <img src="../assets/img1.jpeg" alt="">
          <div class="title-name">It is a long established</div>
      </div>
      <div class="resources">
          <img src="../assets/img2.jpg" alt="">
          <div class="title-name">It is a long established</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      picker: new Date().toISOString().substr(0, 10),
      landscape: true,
      reactive: true,
      event: [
        { name: "Lorem ipsum", time: "13:00" },
        { name: "Lorem ipsum", time: "22:00" }
      ],
      exam: [
        { exam: "Math", time: "13:00" },
        { exam: "History", time: "15:00" }
      ],
      show: false,
      arrowdown: true
    };
  },
  methods: {
    showEvent() {
      if (this.show == false) {
        this.show = true;
        this.arrowdown = false;
      } else {
        this.show = false;
        this.arrowdown = true;
      }
    }
  }
};
</script>

<style>
.calendar-area {
  width: 100%;
  padding: 10px;
}
.calendar {
  border: 1px solid #ededed;
  border-radius: 3px;
}
.v-picker {
  width: 100%;
}
.v-date-picker-title {
  color: black;
}
.event-sub {
  display: flex;
  padding: 8px 4px;
  background-color: #f3f3f3;
  border-top: 1px solid #ededed;
  border-bottom: 1px solid #ededed;
}
.event-sub .event-heading {
  font-size: 12px;
  color: black;
  font-weight: 600;
}

.submit-date {
  padding: 8px 4px;
}
.submit-date .event {
  font-size: 12px;
  color: black;
  font-weight: 600;
}
.topic {
  display: flex;
  margin-top: 4px;
  margin-bottom: 4px;
}
.topic .topic-name,
.time {
  color: #95a5a6;
}
.down-arrow {
  text-align: center;
  border-top: 1px solid #ededed;
}
.down-arrow button {
  display: block;
  width: 100%;
  outline: 0;
  color: #ededed;
}

.recently-shared {
  border: 1px solid #ededed;
  background-color: #fff;
  width: 100%;
  padding: 10px;
  margin-top: 20px;
  border-radius: 3px;
}
.recently-shared .heading {
  font-size: 12px;
  color: black;
  font-weight: 600;
}
.resources{
    display: flex;
    width: 100%;
    margin-top: 5px;
}
.resources img{
    width: 100px;
    height: 60px;
    margin-right: 8px;
}
.resources .title-name{
    color: #95a5a6;
}
</style>

