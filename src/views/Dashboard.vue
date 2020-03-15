<template>
  <div class="dashboard">
    <h1 class="subheading grey--text">Dashboard</h1>
    <v-container class="my-5">
        <v-card outlined class="pa-3">
          <v-row wrap no-gutters>
            <v-flex xs12 md6>
              <div class="caption grey--text">Project Title</div>
              <div>Create a new website</div>
            </v-flex>
            <v-flex xs6 sm4 md2>
              <div class="caption grey--text">Person</div>
              <div>Some random dude</div>
            </v-flex>
            <v-flex xs6 sm4 md2>
              <div class="caption grey--text">Due by</div>
              <div>01/04/2020</div>
            </v-flex>
            <v-flex xs2 sm4 md2>
              <div class="caption grey--text">Status</div>
              <div>Ongoing</div>
            </v-flex>
          </v-row>
        </v-card>
    </v-container>
    
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  name: 'Home'
}
</script>
