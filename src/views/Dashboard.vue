<template>
  <div class="dashboard">
    <h1 class="subheading grey--text">Dashboard</h1>
    <v-container class="my-5">
      <v-row class="mb-3" no-gutters wrap>
        <v-tooltip top>
          <template v-slot:activator="{ on }">
            <v-btn small outlined color="grey" @click="sortBy('title')" v-on="on">
              <v-icon left small>folder</v-icon>
              <span class="caption text-lowercase">By Project Name</span>
            </v-btn>
          </template>
          <span>Sort projects by Project name</span>
        </v-tooltip>
        <v-tooltip top>
          <template v-slot:activator="{ on }">
            <v-btn small outlined color="grey" @click="sortBy('person')" v-on="on">
              <v-icon left small>person</v-icon>
              <span class="caption text-lowercase">By Person</span>
            </v-btn>
          </template>
          <span>Sort projects by owner</span>
        </v-tooltip>
      </v-row>

        <v-card outlined v-for="project in projects" :key="project.title">
          <v-row wrap no-gutters :class="`pa-3 project ${project.status}`">
            <v-flex xs12 md6>
              <div class="caption grey--text">Project Title</div>
              <div>{{ project.title }}</div>
            </v-flex>
            <v-flex xs6 sm4 md2>
              <div class="caption grey--text">Person</div>
              <div>{{ project.person }}</div>
            </v-flex>
            <v-flex xs6 sm4 md2>
              <div class="caption grey--text">Due by</div>
              <div>{{ project.due }}</div>
            </v-flex>
            <v-flex xs2 sm4 md2>
              <div class="right">
                <v-chip small :color="`${project.status}`" class="white--text caption my-2">{{ project.status }}</v-chip>
              </div>
            </v-flex>
          </v-row>
          <v-divider></v-divider>
        </v-card>
    </v-container>
    
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  data() {
    return {
      projects: [
        { title: 'Design a new website', person: 'Harv', due: '31st Mar 2020', status: 'ongoing', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'Code up the homepage', person: 'BarBar', due: '10th Apr 2020', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'Design video thumbnails', person: 'Rob', due: '20th Mar 2020', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'Create a community forum', person: 'Dave', due: '20th Apr 2020', status: 'overdue', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'Design a new component', person: 'Harv', due: '1st Apr 2020', status: 'ongoing', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'}
      ]
    }
  }, 
  methods: {
    sortBy(prop) {
      this.projects.sort((a, b) => a[prop] < b[prop] ? -1 : 1)
    }
  }
}
</script>

<style>

.project.complete {
  border-left: 4px solid #3cd1c2;
}

.project.ongoing {
  border-left: 4px solid orange;
}

.project.overdue {
  border-left: 4px solid tomato;
}

.v-chip.ongoing {
    background: #ffaa2c !important;
  }
.v-chip.complete {
    background: #3cd1c2 !important;
  }
.v-chip.overdue {
    background: #f83e70 !important;
  }
</style>