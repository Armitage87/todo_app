<template>
    <nav>
        <v-snackbar v-model="snackbar" top :timeout="3000" color="success">
            <span>Awesome! You added a new project!</span>
            <v-btn text color="white" @click="snackbar=false">Close</v-btn>
        </v-snackbar>
    <v-app-bar app>
        <v-app-bar-nav-icon class="grey--text" @click="drawer=!drawer"></v-app-bar-nav-icon>
        <v-toolbar-title class="text-uppercase grey--text">
            <span class="font-weight-light">ITO</span>
            <span>DO</span>
        </v-toolbar-title>
        <v-spacer></v-spacer>
    <v-menu offset-y>
        <template v-slot:activator="{ on }">
            <v-btn
            color="grey"
            outlined
            v-on="on">
            <v-icon left>expand_more</v-icon>
            <span>Menu</span>
            </v-btn>
        </template>
        <v-list>
        <v-list-item v-for="link in links" :key="link.text" @click="on" router :to="link.route">
          <v-list-item-title>{{ link.text }}
          </v-list-item-title>
        </v-list-item>
      </v-list>
    </v-menu>
        <v-btn text color="grey">
            <span>Sign Out</span>
            <v-icon right>exit_to_app</v-icon>
        </v-btn>
    </v-app-bar>
    <v-navigation-drawer v-model="drawer" app class="indigo">
    <v-row>
        <v-col align="center">
        <v-flex class="mt-5">
            <v-avatar size="100">
                <img src="/avatar-1.png" alt="">
            </v-avatar>
            <p class="white--text subheading mt-1">Harv</p>
        </v-flex>
        <v-flex class="mt-4 mb-3">
            <popup @projectAdded="snackbar=true"/>
        </v-flex>
    </v-col>
    </v-row>
        <v-list>
            <v-list-item v-for="link in links" :key="link.text" router :to="link.route">
                <v-list-item-action>
                    <v-icon class="white--text">{{ link.icon }}</v-icon>
                </v-list-item-action>
                <v-list-item-content>
                    <v-list-item-title class="white--text">
                        {{ link.text }}
                    </v-list-item-title>
                </v-list-item-content>
            </v-list-item>
        </v-list>
    </v-navigation-drawer>
    </nav>
</template>

<script>
import Popup from './Popup.vue'

export default {
    components: {
        Popup
    },
    data() {
        return {
            drawer: false,
            links: [
                {icon: 'dashboard', text: 'Dashboard', route: '/'},
                {icon: 'folder', text: 'My Projects', route: '/projects'},
                {icon: 'person', text: 'Team', route: '/team'}
            ],
            snackbar: false

        }
    }
}
</script>