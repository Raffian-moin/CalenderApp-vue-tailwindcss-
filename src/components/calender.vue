<template>
  <div class="calender m-auto">
    <h1 class="text-2xl my-3 text-center">Vue Calender</h1>
    <section class="mx-2 flex justify-between">
    <h2 class="font-bold">{{currentMonthName}}</h2>
    <h2 class="font-bold">{{currentYear}}</h2>

    </section>
    <section class="flex content-center">
    <p class="my-2 h-10 text-center" style="width:14.28%" v-for="day in days" :key="day.index">{{day}}</p>
    </section>
    <section class="flex flex-wrap">
      <p class="h-10 text-center" style="width:14.28%" v-for="num in daysOfMonth(currentYear,currentMonth)" :key="num.index">{{num}}</p>
    </section>
    <section class="mx-2 flex justify-between">
      <p @click="previous">previous</p>
      <p @click="next">next</p>
    </section>
  </div>
</template>

<script>
export default {
  name: 'Calender',
  props: {
    msg: String
  },
  data(){
    return{
      currentYear:new Date().getFullYear(),
      currentMonth:new Date().getMonth()+1,
      currentMonthName:new Date().toLocaleString("default", { month: "long" }),
      days:['sat','sun','mon','tue','wed','thur','fri'],
    }
  },

  methods:{
    daysOfMonth:function(year,month){
      return new Date(year,month, 0).getDate(); // 0 + number of days
    },
  },
    computed:{
      next:function(){
        return this.currentMonth++;
      },
      previous:function(){
        return this.currentMonth--;
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
