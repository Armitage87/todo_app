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
            <v-form class="px-3">
                <v-text-field label="Title" v-model="title" prepend-icon="folder"></v-text-field>
                <v-textarea label="Information" v-model="information" prepend-icon="edit"></v-textarea>
                <v-menu>
                    <template v-slot:activator="{ on }">
                        <v-text-field
                        v-model="computedDateFormatted"
                        :value="due"
                        label="Date (read only text field)"
                        hint="MM/DD/YYYY format"
                        persistent-hint
                        prepend-icon="event"
                        readonly
                        v-on="on"
                        ></v-text-field>
                    </template>
                    <v-date-picker v-model="due" no-title @input="menu2 = false"></v-date-picker>
                </v-menu>
            </v-form>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            text
            @click=submit
            class="success"
          >
            Add Project
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
    data() {
        return {
            title: '',
            information: '',
        }
    },
    methods: {
        submit() {
            console.log(this.title, this.information)
        }
    }
}
</script>