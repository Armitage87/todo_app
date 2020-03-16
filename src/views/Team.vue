<template>
  <div class="team">
    <h1 class="subheading grey--text">Team</h1>
    <v-container class="my-5">
        <v-row wrap>
          <v-flex xs12 sm6 md4 lg3 v-for="person in team" :key="person.name">
            <v-card flat outlined class="text-center ma-3">
              <v-responsive class="pt-4">
                <v-avatar size="100" class="grey lighten-2">
                  <img :src="person.avatar" alt="">
                </v-avatar>
              </v-responsive>
              <v-card-text>
                <div class="subheading">{{ person.name }}</div>
                <div class="grey--text">{{ person.role }}</div>
              </v-card-text>
              <v-card-actions>
                <v-btn depressed color="white">
                  <v-icon small left>message</v-icon>
                  <span>Message</span>
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-row>
    </v-container>
    
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  data() {
    return {
      team: [
        { name: 'Harvey', role: 'Lead web developer', avatar: '/avatar-1.png' },
        { name: 'Rob', role: 'Graphic designer', avatar: '/avatar-2.png' },
        { name: 'Barry', role: 'Web developer', avatar: '/avatar-3.png' },
        { name: 'Edvin', role: 'Social media wunderkind', avatar: '/avatar-4.png' },
        { name: 'Dave', role: 'Head of HR', avatar: '/avatar-5.png'}
      ]
    }
  }
}
</script>
