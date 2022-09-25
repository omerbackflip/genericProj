<template>
    <nav>
        <v-app-bar app dark>
            <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
            <v-spacer></v-spacer>
            <v-row >

                <v-col col="2">
                    <template>
                    <div class="mt-2 text-center">
                        <v-menu offset-y>
                        <template v-slot:activator="{ on, attrs }">
                            <v-btn icon v-bind="attrs" v-on="on" class="float-right">
                                <v-icon>mdi-dots-vertical</v-icon>
                            </v-btn>
                        </template>
                        <!-- <v-list>
                            <template v-slot:activator="{ on, attrs }">
                                <v-btn v-bind="attrs" v-on="on">
                                    <v-icon left>expand_more</v-icon>
                                    <span>Menu1</span>
                                </v-btn>
                            </template> -->
                            <v-list>
                                <v-list-item v-for="link in links" :key="link.text" router :to="link.route">
                                    <v-list-item-title>{{link.text}}</v-list-item-title>
                                </v-list-item>
                            </v-list>
                        <!-- </v-list> -->

                        </v-menu>
                    </div>
                    </template>
                </v-col>
            </v-row>

        </v-app-bar>

        <v-navigation-drawer app v-model="drawer" class="primary">
            <v-list>
                <v-list-item v-for="link in links" :key="link.text" router :to="link.route">
                    <v-list-item-action>
                        <v-icon class="white--text">{{link.icon}}</v-icon>
                    </v-list-item-action>
                    <v-list-item-content>
                        <v-list-item-title class="white--text">{{link.text}}</v-list-item-title>
                    </v-list-item-content>
                </v-list-item>
            </v-list>
        </v-navigation-drawer>
    </nav>
    
</template>



<script>
export default {
    data() {
        return {
            drawer: false,
            links: [
                {icon: 'folder', text: 'טבלת הטבלאות', route: '/tableList'},
            ],
        }
    },
    methods:{
        setAddNewRow() {
            this.$root.$emit('addNewRow',{ newRow: true});
        },
        onYearChange(event) {
            this.$root.$emit('yearChange',event);
        },
    },
    computed: {
    }
}
</script>

<style scoped>
    .plus-button{
        font-size: 29px !important;
        padding-top: 0px;
        padding-left: 15px;
        border: 1px solid;
        margin-top: 8px;
        margin-left: 15px;
        height: 42px !important;
    }
    .year-input{
        padding: 0;
        border: 1px solid;
        margin-top: 7px;
        color: white;
        font-size: 12px;
    }
    .year-input:nth-child(1){
        height: 42px !important;
    }
    .cursor-pointer{
        cursor: pointer ;
    }
</style>


