<template>





   <div class="text-center"> 
    <v-dialog
      v-model="dialog"
      width="600"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn

          color="success"
          flat
          v-bind="attrs"
          v-on="on"
        >
          Add new project
        </v-btn>
      </template>

      <v-card>
        <v-card-title class="text-h5 grey lighten-2">
          Add New Project
        </v-card-title>

        <v-card-text>
          <v-form class="px-3" ref="form">
            <v-text-field label="Title" v-model="title" prepend-icon="mdi-format-title" :rules="inputRules"></v-text-field>
            <v-textarea label="information" v-model="info" prepend-icon="mdi-information" :rules="inputRules"></v-textarea>
            
            <v-menu
        ref="menu"
        v-model="menu"
        :close-on-content-click="false"
        :return-value.sync="date"
        transition="scale-transition"
        offset-y
        min-width="auto"
      >
        <template v-slot:activator="{ on, attrs }">
          <v-text-field
            v-model="date"
            label="Due Date"
            prepend-icon="mdi-calendar"
            readonly
            v-bind="attrs"
            v-on="on"
            :rules="inputRules"
            
          ></v-text-field>
        </template>
        <v-date-picker
          v-model="date"
          no-title
          scrollable
        >
          <v-spacer></v-spacer>
          <v-btn
            text
            color="primary"
            @click="menu = false"
          >
            Cancel
          </v-btn>
          <v-btn
            text
            color="primary"
            @click="$refs.menu.save(date)"
          >
            OK
          </v-btn>
        </v-date-picker>
      </v-menu>

            <v-divider></v-divider>
            <v-btn flat class="success mt-3 mx-0" @click="submit">Add Project</v-btn>
          </v-form>
        </v-card-text>

        

        
      </v-card>
    </v-dialog>
  </div> 
</template>

<script>
export default {
    data(){
        return{
            title:'',
            info:'',
            date:'',
            menu: false,

            inputRules:[
                v => v && v.length >= 0 || "empty field"
            ]
        }
    },

    methods:{
        submit(){
            if(this.$refs.form.validate()){
                console.log(this.title, this.info)
            }
        }
    },
    

}
</script>

<style>

</style>