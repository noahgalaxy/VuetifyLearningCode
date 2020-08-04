<template>
  <div class="projects">
    <h1 class="v-subheader grey--text">This is an projects page</h1>

    <v-container fluid class="my-5 grey--text">
      <div class="mb-3">
        <v-btn color="purple" class="ml-4" text @click="showAll">Show all</v-btn>
      </div>

      <v-expansion-panels popout="popout" hover="hover" multiple="multiple" v-model="pannel">
        <v-expansion-panel
                v-for="(project,i) in MyProjects"
                :key="project.title"
        >
          <v-expansion-panel-header class="font-weight-bold">{{project.title}}</v-expansion-panel-header>
          <v-expansion-panel-content>
<!--            <v-card flat>-->
<!--              <v-card-title>-->
<!--                <div>这里是项目所属</div>-->
<!--              </v-card-title>-->
<!--              <v-card-text>-->
<!--                <div>这里是project就提内容</div>-->
<!--              </v-card-text>-->
<!--            </v-card>-->
            <div class="font-weight-bold grey--text">{{project.due}}</div>
            <div class="mt-2 font-weight-thin">{{project.content}}</div>
          </v-expansion-panel-content>
        </v-expansion-panel>
      </v-expansion-panels>
    </v-container>
  </div>
</template>

<script>
  export default {
    name: 'Projects',
    components:{
    },
    data(){
      return{
        currentUser: 'Fisheep',
        pannel: [],
        Projects:[
          {title:"Design a new website", person:"The Net Ninja", due:"1st Jan 2020", status:"origin", content:'使用vuetify的图标的时候官网没有图标样子当时找vuetify图标的时候，网站Material Design lcons怎么也打不开，找到一个备用网站备用网站如有其他问题，请私信博主，一起进步！'},
          {title:"Code up the homepage", person:"Chun li", due:"10th Jan 2020", status:"complete", content: '中新社北京8月3日电 大连市卫健委3日公布大连疫情流调和溯源工作的最新进展称，'},
          {title:"Design video thunbnails", person:"Fisheep", due:"2nd Jan 2020", status:"complete", content: '中国内地新增确诊病例43例 现有确诊病例781例'},
          {title:"Create a community forum", person:"Abby", due:"13rd Oct 2020", status:"origin", content: '大连疫情或始于海鲜加工车间 不排除境外输入引起的可能性'},
          {title:"Harray Poter", person:"Fisheep", due:"10th Jue 2020", status:"origin", content: '一份至高无上的荣誉，凝结着全国人民的钦佩与感恩。'},
          {title:"民族复兴道路上奔跑的缩影", person:"Fisheep", due:"10th Jue 2020", status:"complete", content: '从钟南山们的身上，我们看到了中华民族的精神光辉，他们不怕困难，他们无私奉献，他们开拓进取，他们忠于职守……抗疫路上每一步艰难的前行，都是中国人民在民族复兴道路上奔跑的缩影，那里有我们的艰辛与坚强。'},
        ]
      }
    },
    computed:{
      MyProjects(){
        return this.Projects.filter(project=>{
          return project.person == this.currentUser;
        })
      },
      MyProjectsIndexArray(){
        return this.MyProjects.map((project, i)=> i)
      }
    },
    methods:{
      showAll(){
        if(this.pannel.length === this.MyProjectsIndexArray.length){
          this.showNone()
        }else {
          this.pannel = this.MyProjectsIndexArray
        }
      },
      showNone(){
        this.pannel = []
      }
    }
  }
</script>
