<template>
  <div class="dashboard">
    <h1>dashboard page</h1>


    <v-container class="my-5">

<!--      <v-tooltip bottom>-->
<!--        <template v-slot:activator="{ on, attrs }">-->
<!--          <v-btn-->
<!--                  color="primary"-->
<!--                  dark-->
<!--                  v-bind="attrs"-->
<!--                  v-on="on"-->
<!--          >Button</v-btn>-->
<!--        </template>-->
<!--        <span>Tooltip</span>-->
<!--      </v-tooltip>-->

      <v-layout row class="mb-3">

        <v-tooltip top>
          <template v-slot:activator="{ on, attrs }">
            <v-btn text small color="grey" @click="sortBy('title')" dark v-bind="attrs" v-on="on" >
              <v-icon left small > mdi-folder</v-icon>
              <span class="caption text-lowercase">By project name</span>
            </v-btn>
          </template>
          <span class="caption text-lowercase">Sort project by project name</span>
        </v-tooltip>

        <v-tooltip top>
          <template v-slot:activator="{ on, attrs }">
            <v-btn  small text color="grey" @click="sortBy('person')" dark v-bind="attrs" v-on="on" >
              <v-icon left small> mdi-account-circle</v-icon>
              <span class="caption text-lowercase">By person</span>
            </v-btn>
          </template>
          <span class="caption text-lowercase">Sort project by person</span>
        </v-tooltip>

      </v-layout>

      <v-card flat class="pa-3" v-for="project in Projects" :key="project.title">
        <v-layout row wrap :class="`pa-3 project ${project.status}`">
          <v-flex xs12 md6>
            <div class="caption grey--text">
              project title
            </div>
            <div>
              {{project.title}}
            </div>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <div class="caption grey--text">Person</div>
            <div>{{project.person}}</div>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <div class="caption grey--text">Due by</div>
            <div>{{project.due}}</div>
          </v-flex>
          <v-flex xs2 sm4 md2>
            <div class="float-md-right float-sm-right">
              <v-chip small :class="`${project.status} white--text caption my-2`">{{project.status}}</v-chip>
            </div>
          </v-flex>
        </v-layout>
<!--        这个是添加横线-->
        <v-divider></v-divider>
      </v-card>
    </v-container>

  </div>
</template>

<script>


export default {
  name: 'Dashboard',
  components: {
  },
  data(){
    return{
      Projects:[
        {title:"Design a new website", person:"The Net Ninja", due:"1st Jan 2020", status:"origin"},
        {title:"Code up the homepage", person:"Chun li", due:"10th Jan 2020", status:"complete"},
        {title:"Design video thunbnails", person:"Fisheep", due:"2nd Jan 2020", status:"complete"},
        {title:"Create a community forum", person:"Abby", due:"13rd Oct 2020", status:"origin"},
      ]
    }
  },
  methods:{
    sortBy(prop){
      this.Projects.sort((a,b) => a[prop] < b[prop] ? -1 : 1)
    }
  }
}
</script>
<style>
  .project.complete{
    border-left: 4px solid #3cd1c3;
  }
  .project.origin{
    border-left: 4px solid orange;
  }

  .v-chip.v-chip--no-color.complete{
    background: #3cd1c3;
  }
  .v-chip.v-chip--no-color.origin{
    background: orange;
  }
</style>
