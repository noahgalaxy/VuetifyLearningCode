<template>
    <div class="team">
        <h1>this is team</h1>
        <v-container fluid class="my-5">
            <v-layout row wrap>
                <v-flex xs12 sm6 md4 lg3 v-for="person in teams" :key="person.name">
                    <v-card  class="text-center ma-3">
                        <v-responsive class="pt-4">
                            <v-avatar size="100" class="grey lighten-2">
                                <img :src="person.avatar" >
                            </v-avatar>
                        </v-responsive>
                        <v-card-text>
                            <div class="subheading">{{person.name}}</div>
                            <div class="grey--text">{{person.role}}</div>
                        </v-card-text>
                        <v-card-actions>
                            <v-btn text flat color="grey" >
                                <v-icon small left>mdi-message</v-icon>
                                <span>Message</span>
                            </v-btn>
                        </v-card-actions>
                    </v-card>
                </v-flex>
            </v-layout>
        </v-container>
    </div>
</template>
<script>
    export default {
        name: "Team",
        data(){
            return{
                teams:[
                    {name: 'The Net Ninja', role: 'Web developer', avatar: '/avatar-1.png'},
                    {name: 'Ryu', role: 'Graphic designer', avatar: '/avatar-2.png'},
                    {name: 'Fisheep', role: 'Web developer', avatar: '/avatar-3.png'},
                    {name: 'Gouken', role: 'Social media maverick', avatar: '/avatar-4.png'},
                    {name: 'Yoshi', role: 'Sales guru', avatar: '/avatar-5.png'},
                ]
            }

        }
    }
</script>

<style scoped>

</style>