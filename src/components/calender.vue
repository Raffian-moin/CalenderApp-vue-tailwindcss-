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
     <!--  <p class="h-10 text-center" style="width:14.28%" v-for="firstDayOfMonth(currentYear,currentMonth) in daysOfMonth(currentYear,currentMonth)" :key="num.index">{{num}}</p> -->

      <p
        class="text-center"
        style="width: 14.28%"
        v-for="num in firstDayOfMonth()"
        :key="num"
      ></p>
      <p
        class="text-center"
        style="width: 14.28%"
        v-for="num in daysOfMonth()"
        :class="currentDateClass(num)"
        :key="num"
      >
        {{ num }}
      </p>
    </section>
    <section class="mx-2 flex justify-between">
      <button @click="previous">previous</button>
      <button @click="next">next</button>
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
      currentMonth:new Date().getMonth(),
      
      days:['sat','sun','mon','tue','wed','thur','fri'],
    }
  },

  methods:{
    daysOfMonth:function(){
      return new Date(this.currentYear,this.currentMonth+1, 0).getDate(); // 0 + number of days
    },
    firstDayOfMonth(){
      return new Date(this.currentYear,this.currentMonth,1).getDay()+1;
    },
      next:function(){
        
       if(this.currentMonth==11){
          this.currentMonth=0;
          this.currentYear++;
        }else{
          this.currentMonth++;
        }
      },
      previous:function(){
        // currentMonthName:new Date(this.).toLocaleString("default", { month: "long" }),
        if(this.currentMonth==0){
          this.currentMonth=11;
          this.currentYear--;
        }else{
          this.currentMonth--;
        }
        
        
      },
      currentDateClass:function(num){
      const calenderFullDate = new Date(this.currentYear,this.currentMonth,num).toDateString();
      const currentDate = new Date().toDateString();
      return calenderFullDate===currentDate?"text-yellow-600":"";
    },
  },
  computed:{
    currentMonthName:function(){
      return new Date(this.currentYear,this.currentMonth).toLocaleString("default", { month: "long" });
    },
    
  },
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
