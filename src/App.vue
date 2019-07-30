<template>
    <div id="app">
        <b-container>
            <b-row>
                <draggable
                        id="waiting"
                        v-model="heroes"
                        ghost-class="ghost"
                        :sort="true"
                        draggable=".item"
                        :group="{ name: 'row' }"
                    >
                    <!-- <transition-group> -->
                        <img v-for="(hero, heroindex) in heroes" :key="hero.id" class="item" :src="'dist/img/heroes/'+hero.img" :title="hero.name+' '+hero.name_en" width="60">
                    <!-- </transition-group> -->
                </draggable>
            </b-row>

            <b-row>
                <div class="title">
                    超恩惠
                </div>
                <draggable
                        id="super_sync"
                        v-model="super_sync"
                        ghost-class="ghost"
                        :sort="true"
                        draggable=".item"
                        :group="{ name: 'row' }"
                    >
                    <img v-for="(hero, heroindex) in super_sync" :key="hero.id" class="item" :src="'dist/img/heroes/'+hero.img" :title="hero.name+' '+hero.name_en" width="60">
                </draggable>
            </b-row>

            <b-row>
                <b-col>
                    <div class="title">
                        主力
                    </div>
                    <draggable
                            id="main"
                            v-model="main"
                            ghost-class="ghost"
                            :sort="true"
                            draggable=".item"
                            :group="{ name: 'row' }"
                        >
                        <img v-for="(hero, heroindex) in main" :key="hero.id" class="item" :src="'dist/img/heroes/'+hero.img" :title="hero.name+' '+hero.name_en" width="60">
                    </draggable>
                </b-col>
                
                <b-col>
                    <div class="title">
                        堪用
                    </div>
                    <draggable
                            id="normal"
                            v-model="normal"
                            ghost-class="ghost"
                            :sort="true"
                            draggable=".item"
                            :group="{ name: 'row' }"
                        >
                        <img v-for="(hero, heroindex) in normal" :key="hero.id" class="item" :src="'dist/img/heroes/'+hero.img" :title="hero.name+' '+hero.name_en" width="60">
                    </draggable>
                </b-col>

                <b-col>
                    <div class="title">
                        廢柴
                    </div>
                    <draggable
                            id="garbage"
                            v-model="garbage"
                            ghost-class="ghost"
                            :sort="true"
                            draggable=".item"
                            :group="{ name: 'row' }"
                        >
                        <img v-for="(hero, heroindex) in garbage" :key="hero.id" class="item" :src="'dist/img/heroes/'+hero.img" :title="hero.name+' '+hero.name_en" width="60">
                    </draggable>
                </b-col>
            </b-row>

            <b-row>
                <b-button block variant="primary" @click="save">儲存</b-button>
                <b-button block variant="light" @click="clear">清除</b-button>
            </b-row>
        </b-container>
        

        

        
        <!-- <div id="garbage">
            <ul>            
                <li v-for="(garbageHeroId, index) in garbage" draggable="true">
                    <span v-for="(hero, heroindex) in heroes" v-if="hero.id == garbageHeroId">
                        <img :src="'dist/img/heroes/'+hero.img" :title="hero.name+' '+hero.name_en" width="60">
                    </span>
                </li>
            </ul>
        </div> -->
    </div>
</template>

<script>
import draggable from 'vuedraggable'

export default {
    name: 'app',
    data () {
        return {
            heroes: [
                {
                    id: 1,
                    name: '光之戰士',
                    name_en: 'WOL',
                    img: 'wol.png',
                },
                {
                    id: 2,
                    name: '弗利奧尼爾',
                    name_en: 'Firion',
                    img: 'firion.png',
                },
            ],
            super_sync: [],
            main: [],
            normal: [],
            garbage: []
        }
    },
    computed: {
    },
    mounted: function() {
        if (localStorage.save) {
            this.heroes = JSON.parse(localStorage.heroes);
            this.super_sync = JSON.parse(localStorage.super_sync);
            this.main = JSON.parse(localStorage.main);
            this.normal = JSON.parse(localStorage.normal);
            this.garbage = JSON.parse(localStorage.garbage);
        }
    },
    methods: {
        save: function(e) {
            localStorage.heroes = JSON.stringify(this.heroes);
            localStorage.super_sync = JSON.stringify(this.super_sync);
            localStorage.main = JSON.stringify(this.main);
            localStorage.normal = JSON.stringify(this.normal);
            localStorage.garbage = JSON.stringify(this.garbage);
            localStorage.save = true;
            this.$swal({
                text: '儲存成功！',
                type: 'success',
            });
        },
        clear: function(e) {
            this.$swal({
                text: '你確定要清除嗎？',
                type: 'question',
                showCancelButton: true,
                confirmButtonText: '確定',
                cancelButtonText: '取消',
            }).then((result) => {
                if(result.value) {
                    localStorage.clear();
                    window.location.reload();
                    this.$swal({
                        text: '清除成功!',
                        type: 'success',
                    });
                } else {
                   
                }
            })
            
        }
    },
    components: {
        draggable,
    },
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Noto+Sans+TC&display=swap&subset=chinese-traditional');
* {
    font-family: 'Noto Sans TC', sans-serif;
}
#waiting,
#super_sync,
#main,
#normal,
#garbage{
    min-height: 10px;
    width: 100%;
    background: #333;
    padding: 10px;
    img {
        &:hover {
            cursor: move;
        }
    }
}
.row {
    padding-top: 20px;
}
.title {
    width: 100%;
    // margin-top: 20px;
    margin-bottom: 10px;
    font-size: 1.5em;
    // font-weight: 400;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    display: inline-block;
    margin: 0 10px;
}

.ghost {
    opacity: 0.5;
    background: #c8ebfb;
}

</style>
