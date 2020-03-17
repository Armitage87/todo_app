<template>
  <div class="text-center">
    <v-dialog
      v-model="dialog"
      width="500"
    >
      <template v-slot:activator="{ on }">
        <v-btn
          color="success"
          dark
          v-on="on"
        >
          Create new project
        </v-btn>
      </template>

      <v-card>
        <v-card-title
          class="headline grey lighten-2"
          primary-title
        >
          Create new project
        </v-card-title>
        <v-card-text>
            <v-form class="px-3" ref="form">
                <v-text-field label="Title" v-model="title" prepend-icon="folder" :rules="inputRules"></v-text-field>
                <v-textarea label="Information" v-model="information" prepend-icon="edit" :rules="inputRules"></v-textarea>
                <v-menu v-model="menu2"
                  :close-on-content-click="false"
                  max-width="290">
                    <template v-slot:activator="{ on }">
                      <v-text-field
                        :value="date"
                        clearable
                        label="Due date"
                        readonly
                        prepend-icon="date_range"
                        v-on="on"
                        @click:clear="date = null"
                      ></v-text-field>
                    </template>
                    <v-date-picker
                      v-model="date"
                      @change="menu2 = false"
                    ></v-date-picker>
                  </v-menu>
            </v-form>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            text
            @click=submit
            class="success"
            :loading="loading"
          >
            Add Project
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
import db from '@/fb'

export default {
    data() {
        return {
            title: '',
            information: '',
            date: null,
            inputRules: [
              v => v.length >= 3 || 'Minimum length is 3 characters'
            ],
            loading: false,
            dialog: false,
            menu2: false
        }
    },
    methods: {
        submit() {
            if(this.$refs.form) {
              this.loading = true;
              const project = {
                title: this.title,
                content: this.information,
                due: this.date,
                person: 'Harv',
                status: 'ongoing'

              }
              db.collection('projects').add(project).then(() => {
                this.loading = false;
                this.dialog = false;
                this.$emit('projectAdded')
              })
            }
            
        }
    }
}
</script>