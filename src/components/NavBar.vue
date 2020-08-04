<template>
    <nav>
        <v-snackbar v-model="snackbar" color="success" :timeout="timeout">
            {{projectAddMessage}}
            <v-btn class="purple--text" text>
                close
            </v-btn>
        </v-snackbar>
        <v-toolbar app flat>
<!--            这个是管理打开或者关闭抽屉的图标-->
            <v-app-bar-nav-icon class="grey--text" @click="drawer = !drawer"></v-app-bar-nav-icon>

            <v-toolbar-title class="text-uppercase">
                <span class="font-weight-light">
                    Todo
                </span>
                <span>Ninja</span>
            </v-toolbar-title>

<!--            这个相当于把这后面的放到另一边去了-->
            <v-spacer></v-spacer>

            <v-menu open-on-hover="open-on-hover">
                <template v-slot:activator="{ on, attrs }">
                    <v-btn
                            text
                            color="primary"
                            dark
                            v-bind="attrs"
                            v-on="on"
                    >
                        <v-icon>expand-more</v-icon>
                        menu
                    </v-btn>
                </template>
                <v-list>
                    <v-list-item
                            v-for="(link, index) in links"
                            :key="link.text"
                            @click=""
                            router
                            :to="link.route"
                    >
                        <v-icon small class="mr-3">{{link.icon}}</v-icon>
                        <v-list-item-title>{{ link.text }}</v-list-item-title>
                    </v-list-item>
                </v-list>
            </v-menu>

            <v-btn text color="grey">
                <span>Sign out</span>
                <v-icon right>mdi-exit-to_app</v-icon>
            </v-btn>
        </v-toolbar>

<!--        需要有这个app属性才能显示完全
            v-model="drawer"需要双向绑定一个属性，
            属性值位true表示打开，为false表示关闭；
-->
        <v-navigation-drawer temporary app v-model="drawer" class="primary">
            
            
            <v-layout column align-center>
                <v-flex class="mt-5">
                    <v-avatar size="100">
                        <img src="/avatar-1.png" alt="">
                    </v-avatar>
                    <p class="white--text mt-1">The Net Ninja</p>
                </v-flex>
            </v-layout>

            <v-layout column align-center class="mt-5 mb-3">
                <v-flex>
                    <add-project @projectAddedSuccess="projectAddedSuccess"></add-project>
                </v-flex>
            </v-layout>


            <v-list>

                <v-list-item v-for="item in links" :key="item.text" router :to="item.route">
                    <v-list-item-action>
                        <v-icon class="white--text">{{item.icon}}</v-icon>
                    </v-list-item-action>
                    <v-list-item-title class="white--text">
                        {{item.text}}
                    </v-list-item-title>
                </v-list-item>

            </v-list>
        </v-navigation-drawer>
    </nav>

</template>

<script>
    import AddProject from "./AddProject";


    export default {
        name: "NavBar",
        components:{
            AddProject,
        },
        data(){
            return{
                drawer: true,
                links:[
                    {icon: 'mdi-android', text: 'Dashboard', route:'/'},
                    {icon: 'mdi-folder', text: 'My Projects', route:'/projects'},
                    {icon: 'mdi-account-circle', text: 'Team', route:'/team'},
                ],
                dropdown_font: ['Arial', 'Calibri', 'Courier', 'Verdana'],
                dropdown_icon: [
                    { text: 'list', callback: () => console.log('list') },
                    { text: 'favorite', callback: () => console.log('favorite') },
                    { text: 'delete', callback: () => console.log('delete') },
                ],
                dropdown_edit: [
                    { text: '100%' },
                    { text: '75%' },
                    { text: '50%' },
                    { text: '25%' },
                    { text: '0%' },
                ],
                snackbar:false,
                projectAddMessage:'默认消息',
                successAddedMessage: 'Cool!! project added successfully!!',
                failedAddedMessage: 'project added 失败!!',
                timeout: 2000,
            }
        },
        methods:{
            projectAddedSuccess(isSuccess){
                console.log('父组件接收到了子组件的添加消息');
                // 关闭drawer以及打开snackbar
                this.drawer = false;
                this.snackbar = true
                isSuccess ? this.projectAddMessage = this.successAddedMessage : this.projectAddMessage = this.failedAddedMessage;
            }
        }
    }
</script>

<style scoped>

</style>