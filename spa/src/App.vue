<template>
    <main id="app" class="h-screen flex flex-col">
        <div class="flex flex-none flex-row bg-lines justify-between h-full" style="height:70px;" v-if="$store.data.isUser">
            <div class="flex h-full items-center">
                    <img src="/assets/img/ctMinaBanner.gif" />
            </div>
            <div class="flex h-full text-right items-center">
                <img src="/assets/img/news.gif" />
            </div>
        </div>
        <div class="flex flex-row flex-grow" style="height:calc(100vh - 70px) !important">
            <div class="flex flex-1">
                <router-view v-if="this.$route.name !== 'world-browser'"></router-view>
                <world-browser-page v-show="this.$route.name === 'world-browser'"></world-browser-page>
            </div>
            <div class="flex-none w-60 bg-lines overflow-y-auto" v-if="$store.data.isUser">
                <div class="flex flex-col">
                    <div class="flex justify-center">
                        <img src="/assets/img/logo-action.gif" />
                    </div>
                    <div class="flex flex-row justify-center">
                        <img src="/assets/img/b2dchat.gif" />
                        <img src="/assets/img/b3dchat.gif" />
                    </div>
                    <div class="flex justify-center">
                        <div class="menu">
                            <router-link class="menuLink" to="/myinfo" style="top:78px;"></router-link>
                        </div>
                    </div>
                    <div class="flex justify-center">
                        <img src="/assets/img/outlandico.jpeg" />
                    </div>
                    <div class="px-8">
                        <select class="w-full text-black" @change="changeJumpGate()" v-model="jumpGate">
                            <option value="">JUMP GATE</option>
                            <option value=""></option>
                            <option v-for="option in jumpGateData" :value="option.slug">{{ option.title }}</option>
                        </select>
                    </div>
                    <div>
                        <br/>
                        <a href="https://discord.gg/gcgAZ7UuNA" class="btn-ui" target="_blank">Discord</a>
                        <a href="https://www.reddit.com/r/cybertown/" class="btn-ui" target="_blank">Reddit</a>
                        <a href="https://github.com/CybertownRevival/ct-spa/issues" class="btn-ui" target="_blank">Report a Bug</a>
                        <br/>
                        <router-link to="/logout" class="btn-ui">Logout</router-link>
                        <br/>
                        <br/>
                        <p align="center">

                            <a href="https://kdaws.com/" target="_blank" class="text-center inline-block p-3 rounded-sm" style="margin: 0 auto">
                                <img src="/assets/img/kda-logo-white.png" style="width:96px;height:auto;" title="Hosted by KDA Web Services"/>
                            </a>
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </main>
</template>

<script>

import WorldBrowserPage from "./pages/WorldBrowserPage.vue";

/*eslint no-undef: 0*/
/*eslint no-unused-vars: 0*/
export default {
    name: 'App',
    components: {
        WorldBrowserPage
    },
    data: () => {
        return {
            jumpGateData: [
                {
                    'title': 'COLONIES:',
                    "slug": ""
                },
                {
                    'title': '(coming soon)',
                    "slug": ""
                },
                {
                    'title': '-----------------------',
                    "slug": ""
                },
                {
                    'title': 'The Plaza',
                    "slug": "enter"
                },
                {
                    'title': 'Flea Market',
                    "slug": "fleamarket"
                },
                {
                    'title': 'Bank',
                    "slug": "bank"
                },
                {
                    'title': 'Sunset Beach',
                    "slug": "beach"
                },
                {
                    'title': 'Water Park',
                    "slug": "waterpark"
                },
                {
                    'title': 'Theme Park',
                    "slug": "themepark"
                },
                {
                    'title': 'City Hall',
                    "slug": "cityhall"
                },
                {
                    'title': 'Performing Arts',
                    "slug": "theatre"
                },
                {
                    'title': 'The Pool',
                    "slug": "pool"
                },
                {
                    'title': 'The Stadium',
                    "slug": "stadium"
                },
                {
                    'title': 'The Post Office',
                    "slug": "postoffice"
                },
                {
                    'title': 'Game Show',
                    "slug": "gameshow"
                },
                {
                    'title': '(more coming soon)',
                    "slug": ""
                },
                /* For the curious developers. These worlds need fixing to work (see dev tools console)
                {
                    'title': 'Black Market',
                    "slug": "blackmarket"
                },
                {
                    'title': 'Mall',
                    "slug": "mall"
                },
                {
                    'title': 'Employment Office',
                    "slug": "employment"
                },
                {
                    'title': 'Outlands',
                    "slug": "outlands"
                },
                {
                    'title': 'Le Cafe',
                    "slug": "cafe"
                },
                {
                    'title': 'Library (missing wrl)',
                    "slug": "library"
                },
                {
                    'title': 'Jail',
                    "slug": "jail"
                },
                {
                    'title': 'Fun Park',
                    "slug": "funpark"
                },
                {
                    'title': 'Fun Park',
                    "slug": "funpark"
                },

                 */
                {
                    'title': '-----------------------',
                    "slug": ""
                },
                {
                    'title': 'HOME DEMOS:',
                    "slug": ""
                },
                {
                    "slug": "home03",
                    'title': 'Home 1'
                },
                {
                    "slug": "home00",
                    'title': 'Home 1 (Furnished)'
                },
                {
                    "slug": "home04",
                    'title': 'Home 2'
                },
                {
                    "slug": "home01",
                    'title': 'Home 2 (Furnished)'
                },
                {
                    "slug": "home05",
                    'title': 'Home 3'
                },
                {
                    "slug": "home02",
                    'title': 'Home 3 (Furnished)'
                },
                {
                    "slug": "home06",
                    'title': 'Home 4'
                },
                {
                    "slug": "home07",
                    'title': 'Home 5'
                },
                {
                    "slug": "home0a",
                    'title': 'Home 6'
                }
            ],
            jumpGate: ''
        };
    },
    methods: {
        changeJumpGate() {
            if(this.jumpGate !== '') {
                this.$router.push({path: '/place/'+this.jumpGate});
                this.jumpGate = '';
            }
        }
    },
    mounted() {
        //todo populate jumpgate with worlds

        X3D(() => {
                console.log('starting X3d');
                this.$store.data.x3dReady = true;
            },
            (error) => {
                console.error(error);
            });
        require('./libs/x_ite_mods/spec_color.js');
        require('./libs/x_ite_mods/relax_route.js');
        require('./libs/x_ite_mods/relax_is.js');
        require('./libs/x_ite_mods/arrow_keys.js');
        require('./libs/x_ite_mods/viewpoint_bind.js');
        require('./libs/x_ite_mods/allow_sf_string.js');
        //require('./libs/x_ite_mods/speed_multiplier.js');
        require('./libs/x_ite_mods/bxx_speed_avatar.js');
        require('./libs/x_ite_mods/default_gravity.js');
        require('./libs/x_ite_mods/extend_context_menu.js');
        require('./libs/x_ite_mods/bxx_auth.js');
        //require('./libs/x_ite_mods/fix_stairs.js');

    }
}
</script>
