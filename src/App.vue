
<template>
  <main>
    <dinoHeader/>
    <div id="main">
      <section>
        <h2>Job Listings</h2>
        <ul id="job-listings">
          <jobListing 
          v-for="job in jobs" 
          :key='job.id' 
          :job='job' />
        </ul>
      </section>
      <jobForm v-on:addJob="postJob" />
    </div>
  </main>
</template>

<script>
import dinoHeader from './components/dinoHeader.vue';
import jobListing from './components/jobListing.vue';
import jobForm from './components/jobForm.vue';
export default {
  name: 'App',
  components: {
    dinoHeader,
    jobListing,
    jobForm
  },
  data() {
    return {
      jobs: [],
      apiURL: '../static/listings.json'
    };
  },
  methods: {
    postJob: function (title,pay,description) {
      this.jobs.push({'id': this.jobs.length+1, 'title': title, 'pay': pay, 'description': description})
    }
  },
  mounted() {
    fetch(this.apiURL)
      .then(result => result.json())
      .then(result => this.jobs = result);
  }
};
</script>
  
<style>
html {
  margin: 0;
  padding: 0;
}

body {
  margin: 0 30px 0 30px;
  padding: 0;
  font-family: sans-serif;
  color: #1B997A;
  display: grid;
  grid-template-rows: 15% 75% 10%;
}

/* Header */

header {
  grid-row: 1 / 2;
  display: grid;
  grid-template-columns: 25% 50% 15%;
  grid-template-rows: 50% 50%;
  padding-top: 10px;
}

header img {
  grid-row: 1/3;
  grid-column: 1/2;
  height: 100px;
  width: auto;
}

header h1 {
  grid-row: 1/2;
  grid-column: 2/3;
  margin: 0;
  color: #C261CC;
  font-family: serif;
}

/* Main */

#main {
  grid-row: 2/3;
  display: grid;
  grid-template-columns: 5% 42.5% 5% 42.5% 5%;
}

#main section {
  grid-column: 2/3;
}

#main section h2 {
  margin: 0;
  color: #61CCB1;
}

#job-listings li {
  display: flex;
  flex-flow: column;
  border-radius: 6px;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.3);
  margin-bottom: 10px;
  padding: 10px;
}

ul {
  list-style: none;
}

h4 {
  margin: 0;
}

small {
  color: black;
  font-size: .5rem;
  margin-left: 10px;
}

p {
  font-size: .8rem;
}

/* Aside */

#side-bar {
  grid-column: 4/5;
}

form {
  display: flex;
  flex-flow: column;
  justify-content: space-around;
}

/* Footer */

footer {
  position: fixed;
  bottom: 0;
  padding: 5px;
}

footer small {
  margin: 0 auto;
}

</style>
