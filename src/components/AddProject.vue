<template>
    <v-row justify="center">
        <v-btn
                class="success--text"
                @click.stop="dialog = true"

        >
            add project
        </v-btn>
        <v-dialog
                v-model="dialog"
                max-width="600"
        >
            <v-card>
                <v-card-title class="headline">Add a new project</v-card-title>

                <v-card-text>
                    <v-form class="px-3" ref="MyForm">
                        <v-text-field label="Title" v-model="title" prepend-icon="mdi-folder" :rules="titleRules"></v-text-field>
                        <v-textarea label="Imfomation" v-model="content" prepend-icon="mdi-pencil"></v-textarea>


                        <v-col cols="12" lg="3" md="6">
                            <v-menu>
                                <template v-slot:activator="{ on, attrs }">
                                    <v-text-field
                                            prepend-icon="mdi-call-split"
                                            :value="due"
                                            clearable
                                            label="Due date"
                                            readonly
                                            v-bind="attrs"
                                            v-on="on"
                                    ></v-text-field>
                                </template>
                                <!--                            <v-text-field slot="activator" label="Due date">-->
                                <v-date-picker v-model="due"></v-date-picker>
                                <!--                            </v-text-field>-->
                            </v-menu>
                        </v-col>
                    </v-form>
                </v-card-text>

                <v-card-actions>
                    <v-spacer></v-spacer>

                    <v-btn
                            color="primary darken-1"
                            outlined
                            @click="submit"
                            class="mr-7"
                            :loading="submitBtnLoader"
                    >
                        add project
                    </v-btn>
                </v-card-actions>
            </v-card>
        </v-dialog>
    </v-row>
</template>


<script>
    import format from 'date-fns/format'

    export default {
        name: "AddProject",
        data () {
            return {
                dialog: false,
                title:'',
                content:'',
                due: null,
                titleRules:[
                    title => title.length >=3 || 'title长度需要大于3个字符',
                    title => title.length <=10 || 'title长度需要小于10个字符'
                ],
                submitBtnLoader:false,
            }
        },
        computed:{
        },
        methods:{
            submit(){
                // 这里是给表单需要验证通过之后才能可以提交，给表单增加了一个refs='MyForm',然后表单提交的时候通过下面的来判断是否通过了验证
                if(this.$refs.MyForm.validate()){
                    this.submitBtnLoader = true
                    new Promise((resolve, reject) => {
                        setTimeout(function(){
                            console.log('正在请求');
                            resolve("这是需要传送的参数，传送给then")
                        }, 7000)
                    }).then((res)=>{
                        console.log("从上面接收到的参数为：",res);
                        console.log(this.title, this.content)
                        this.submitBtnLoader = false
                        this.dialog = false;

                        // 向父组件发送通知，添加成功
                        this.$emit('projectAddedSuccess', true)
                    })

                }

            }
        }
    }
</script>

<style scoped>

</style>