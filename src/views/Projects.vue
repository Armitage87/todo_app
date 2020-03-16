<template>
  <div class="projects">
    <h1 class="subheading grey--text">Projects</h1>


    <v-container class="my-5">
        <v-expansion-panels>
          <v-expansion-panel v-for="project in myProjects" :key="project.title">
            <v-expansion-panel-header>{{ project.title }}</v-expansion-panel-header>
            <v-expansion-panel-content class="px-4 grey--text">
              <div class="font-weight-bold">Due by date: {{ project.due }}</div>
              <div>{{ project.content }}</div>
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
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
    computed: {
      myProjects() {
        return this.projects.filter(project => {
          return project.person === 'Harv' 
        })
      }
    }
}
</script>
