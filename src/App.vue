<template>
  <div id="app">
    <div class="grid-container">
      <div class="grid-item clock">
        <Clock/>
      </div>
      <div class="grid-item calendar">
        <Calendar/>
      </div>
      <div class="grid-item tasks">
        <!-- <app-tasks></app-tasks> -->
      </div>
      <div class="grid-item links">
        <!-- <app-links></app-links> -->
      </div>
      <div class="grid-item feed">
        <!-- <app-feed></app-feed> -->
        <Feed/>
      </div>

    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Clock from './components/Clock.vue'
import Feed from './components/Feed.vue'
import Calendar from './components/Calendar.vue'

export default {
  name: 'app',
  components: {
      HelloWorld,
      Clock,
      Feed,
      Calendar
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  /* margin-top: 60px; */
}

@import url('https://fonts.googleapis.com/css?family=Montserrat:400,700|Quicksand:400,700|Raleway|Titillium+Web:400,700');

* {                              
 font-family: 'Quicksand', sans-serif;
}

// For debugging
.red { background-color: red }
.green { background-color: green }
.blue { background-color: blue }

html,body,#app {
    height: 100%;
}


body {
 background: url('http://localhost:8000/static/background.jpg') no-repeat center center fixed;
 -webkit-background-size: cover;
 -moz-background-size: cover;
 -o-background-size: cover;
 background-size: cover;
 margin: 0;                                              
 padding: 0;
}

a {
    text-decoration: none;
    color: #557;
}

a:hover {
    text-decoration: underline;
}

a:visited {
    color: #aaa;
}

.background {
    width: 100%;
    height: 100%;
    position: absolute;
    z-index: -100;
}

.grid-container {
    display: grid;
    grid-gap: 20px 20px;
    grid-template-columns: 400px auto 300px;
    grid-template-rows: 150px auto 300px;
    height: 100%;
    max-width: 1500px;
    margin: auto;
    padding: 30px;
    box-sizing: border-box;
    grid-template-areas:
        "a b c"
        "d b c"
        "d e e";
    // background-color: rgba(255, 255, 255, 0.8);
    // box-shadow: 1px 1px 20px #aaa;
}

.grid-item {
    display: inline-grid;
    padding: 15px;
    background-color: rgb(255, 255, 255);
    border-radius: 4px;
    // border: 2px solid rgba(200,200,200,0.8);
    // box-shadow: 3px 3px rgba(100,100,100,0.5);
    //text-shadow: 0px 0px 4px white;
    box-shadow: 1px 1px 5px #AAA;
}

.grid-item.clock {
    grid-area: a;
    align-content: center;
}

.grid-item.calendar {
    overflow: auto;
    grid-area: d;
}

.grid-item.tasks {
    grid-area: c;
}

.grid-item.links {
    grid-area: e;
}

.grid-item.feed {
    overflow: auto;
    grid-area: b;
}
</style>
