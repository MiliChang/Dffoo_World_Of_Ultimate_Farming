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
                        <img v-for="hero in heroes" :key="hero.id" class="item" :src="'dist/img/heroes_pic/'+hero.img" :title="hero.name+' '+hero.name_en" width="80">
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
                    <img v-for="hero in super_sync" :key="hero.id" class="item" :src="'dist/img/heroes_pic/'+hero.img" :title="hero.name+' '+hero.name_en" width="80">
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
                        <img v-for="hero in main" :key="hero.id" class="item" :src="'dist/img/heroes_pic/'+hero.img" :title="hero.name+' '+hero.name_en" width="80">
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
                        <img v-for="hero in normal" :key="hero.id" class="item" :src="'dist/img/heroes_pic/'+hero.img" :title="hero.name+' '+hero.name_en" width="80">
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
                        <img v-for="hero in garbage" :key="hero.id" class="item" :src="'dist/img/heroes_pic/'+hero.img" :title="hero.name+' '+hero.name_en" width="80">
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
                    <span v-for="hero in heroes" v-if="hero.id == garbageHeroId">
                        <img :src="'dist/img/heroes_pic/'+hero.img" :title="hero.name+' '+hero.name_en" width="80">
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
                {
                    id: 3,
                    name: '瑪麗亞',
                    name_en: 'Maria',
                    img: 'maria.png',
                },
                {
                    id: 4,
                    name: '雷翁哈特',
                    name_en: '',
                    img: 'leonhart.png',
                },
                {
                    id: 5,
                    name: '洋蔥騎士',
                    name_en: 'Onion Knight',
                    img: 'onion_knight.png',
                },
                {
                    id: 6,
                    name: '賽希爾（暗黑騎士）',
                    name_en: 'Cecil (Dark Knight)',
                    img: 'cecil_dark.png',
                },
                {
                    id: 7,
                    name: '艾吉',
                    name_en: 'Edge',
                    img: 'edge.png',
                },
                {
                    id: 8,
                    name: '楊',
                    name_en: 'Yang',
                    img: 'yang.png',
                },
                {
                    id: 9,
                    name: '凱因',
                    name_en: 'Kain',
                    img: 'kain.png',
                },
                {
                    id: 10,
                    name: '帕羅姆',
                    name_en: 'Palom',
                    img: 'palom.png',
                },
                {
                    id: 11,
                    name: '莉迪亞',
                    name_en: 'Rydia',
                    img: 'rydia.png',
                },
                {
                    id: 12,
                    name: '賽希爾（聖騎士）',
                    name_en: 'Cecil (Paladin)',
                    img: 'cecil_paladin.png',
                },
                {
                    id: 13,
                    name: '蘿莎',
                    name_en: 'Rosa',
                    img: 'rosa.png',
                },
                {
                    id: 14,
                    name: '戈爾貝札',
                    name_en: 'Golbez',
                    img: 'golbez.png',
                },
                {
                    id: 15,
                    name: '巴茲',
                    name_en: 'Bartz',
                    img: 'bartz.png',
                },
                {
                    id: 16,
                    name: '加拉夫',
                    name_en: 'Galuf',
                    img: 'galuf.png',
                },
                {
                    id: 17,
                    name: '法利斯',
                    name_en: 'Faris',
                    img: 'faris.png',
                },
                {
                    id: 18,
                    name: '可露兒',
                    name_en: 'Krile',
                    img: 'krile.png',
                },
                {
                    id: 19,
                    name: '蕾娜',
                    name_en: 'Lenna',
                    img: 'lenna.png',
                },
                {
                    id: 20,
                    name: '基加美修',
                    name_en: 'Gilgamesh',
                    img: 'gilgamesh.png',
                },
                {
                    id: 21,
                    name: '蒂娜',
                    name_en: 'Terra',
                    img: 'terra.png',
                },
                {
                    id: 22,
                    name: '暗影',
                    name_en: 'Shadow',
                    img: 'shadow.png',
                },
                {
                    id: 23,
                    name: '薩查',
                    name_en: 'Setzer',
                    img: 'setzer.png',
                },
                {
                    id: 24,
                    name: '馬修',
                    name_en: 'Sabin',
                    img: 'sabin.png',
                },
                {
                    id: 25,
                    name: '凱炎',
                    name_en: 'Cyan',
                    img: 'cyan.png',
                },
                {
                    id: 26,
                    name: '艾德加',
                    name_en: 'Edgar',
                    img: 'edgar.png',
                },
                {
                    id: 27,
                    name: '莎莉絲',
                    name_en: 'Celes',
                    img: 'celes.png',
                },
                {
                    id: 28,
                    name: '凱夫卡',
                    name_en: 'Kefka',
                    img: 'kefka.png',
                },
                {
                    id: 29,
                    name: '莉露姆',
                    name_en: 'Relm',
                    img: 'relm.png',
                },
                {
                    id: 30,
                    name: '洛克',
                    name_en: 'Locke',
                    img: 'locke.png',
                },
                {
                    id: 31,
                    name: '蒂法',
                    name_en: 'Tifa',
                    img: 'tifa.png',
                },
                {
                    id: 32,
                    name: '克勞德',
                    name_en: 'Cloud',
                    img: 'cloud.png',
                },
                {
                    id: 33,
                    name: '尤菲',
                    name_en: 'Yuffie',
                    img: 'yuffie.png',
                },
                {
                    id: 34,
                    name: '文森特',
                    name_en: 'Vincent',
                    img: 'vincent.png',
                },
                {
                    id: 35,
                    name: '艾麗絲',
                    name_en: 'Aerith',
                    img: 'aerith.png',
                },
                {
                    id: 36,
                    name: '賽菲羅斯',
                    name_en: 'Sephiroth',
                    img: 'sephiroth.png',
                },
                {
                    id: 37,
                    name: '席德',
                    name_en: 'Cid',
                    img: 'cid.png',
                },
                {
                    id: 38,
                    name: '扎克斯',
                    name_en: 'Zack',
                    img: 'zack.png',
                },
                {
                    id: 39,
                    name: '凱特・西',
                    name_en: 'Cait Sith',
                    img: 'cait_sith.png',
                },
                {
                    id: 40,
                    name: '巴雷特',
                    name_en: 'Barret',
                    img: 'barret.png',
                },
                {
                    id: 41,
                    name: '',
                    name_en: 'Laguna',
                    img: 'laguna.png',
                },
                {
                    id: 42,
                    name: '',
                    name_en: 'Squall',
                    img: 'squall.png',
                },
                {
                    id: 43,
                    name: '',
                    name_en: 'Zell',
                    img: 'zell.png',
                },
                {
                    id: 44,
                    name: '',
                    name_en: 'Irvine',
                    img: 'irvine.png',
                },
                {
                    id: 45,
                    name: '',
                    name_en: 'Quistis',
                    img: 'quistis.png',
                },
                {
                    id: 46,
                    name: '',
                    name_en: 'Raijin',
                    img: 'raijin.png',
                },
                {
                    id: 47,
                    name: '',
                    name_en: 'Fujin',
                    img: 'fujin.png',
                },
                {
                    id: 48,
                    name: '',
                    name_en: 'Seifer',
                    img: 'seifer.png',
                },
                {
                    id: 49,
                    name: '雪菲',
                    name_en: 'Selphie',
                    img: 'selphie.png',
                },
                {
                    id: 50,
                    name: '莉諾雅',
                    name_en: 'Rinoa',
                    img: 'rinoa.png',
                },
                {
                    id: 51,
                    name: '比比',
                    name_en: 'Vivi',
                    img: 'vivi.png',
                },
                {
                    id: 52,
                    name: '',
                    name_en: 'Zidane',
                    img: 'zidane.png',
                },
                {
                    id: 53,
                    name: '',
                    name_en: 'Steiner',
                    img: 'steiner.png',
                },
                {
                    id: 54,
                    name: '',
                    name_en: 'Eiko',
                    img: 'eiko.png',
                },
                {
                    id: 55,
                    name: '',
                    name_en: 'Garnet',
                    img: 'garnet.png',
                },
                {
                    id: 56,
                    name: '',
                    name_en: 'Kuja',
                    img: 'kuja.png',
                },
                {
                    id: 57,
                    name: '',
                    name_en: 'Freya',
                    img: 'freya.png',
                },
                {
                    id: 58,
                    name: '',
                    name_en: 'Beatrix',
                    img: 'beatrix.png',
                },
                {
                    id: 59,
                    name: '',
                    name_en: 'Yuna',
                    img: 'yuna.png',
                },
                {
                    id: 60,
                    name: '',
                    name_en: 'Wakka',
                    img: 'wakka.png',
                },
                {
                    id: 61,
                    name: '',
                    name_en: 'Tidus',
                    img: 'tidus.png',
                },
                {
                    id: 62,
                    name: '',
                    name_en: 'Seymour',
                    img: 'seymour.png',
                },
                {
                    id: 63,
                    name: '',
                    name_en: 'Auron',
                    img: 'auron.png',
                },
                {
                    id: 64,
                    name: '',
                    name_en: 'Jecht',
                    img: 'jecht.png',
                },
                {
                    id: 65,
                    name: '',
                    name_en: 'Lulu',
                    img: 'lulu.png',
                },
                // {
                //     id: 66,
                //     name: '',
                //     name_en: 'Paine',
                //     img: 'paine.png',
                // },
                {
                    id: 67,
                    name: '',
                    name_en: 'Shantotto',
                    img: 'shanttoto.png',
                },
                {
                    id: 68,
                    name: '',
                    name_en: 'Prishe',
                    img: 'prishe.png',
                },
                {
                    id: 69,
                    name: '',
                    name_en: 'Lion',
                    img: 'lion.png',
                },
                {
                    id: 70,
                    name: '',
                    name_en: 'Lilisette',
                    img: 'lilisette.png',
                },
                {
                    id: 71,
                    name: '',
                    name_en: 'Vaan',
                    img: 'vaan.png',
                },
                {
                    id: 72,
                    name: '',
                    name_en: 'Penelo',
                    img: 'penelo.png',
                },
                {
                    id: 73,
                    name: '',
                    name_en: 'Balthier',
                    img: 'balthier.png',
                },
                {
                    id: 74,
                    name: '',
                    name_en: 'Ashe',
                    img: 'ashe.png',
                },
                {
                    id: 75,
                    name: '',
                    name_en: 'Vayne',
                    img: 'vayne.png',
                },
                {
                    id: 76,
                    name: '',
                    name_en: 'Fran',
                    img: 'fran.png',
                },
                {
                    id: 77,
                    name: '薩茲',
                    name_en: 'Sazh',
                    img: 'sazh.png',
                },
                {
                    id: 78,
                    name: '霍普',
                    name_en: 'Hope',
                    img: 'hope.png',
                },
                {
                    id: 79,
                    name: '班尼拉',
                    name_en: 'Vanille',
                    img: 'vanille_.png',
                },
                {
                    id: 80,
                    name: '冰雪',
                    name_en: 'Snow',
                    img: 'snow.png',
                },
                {
                    id: 81,
                    name: '雷光',
                    name_en: 'Lightning',
                    img: 'lightning.png',
                },
                {
                    id: 82,
                    name: '莎拉',
                    name_en: 'Serah',
                    img: 'serah.png',
                },
                {
                    id: 83,
                    name: '牙',
                    name_en: 'Fang',
                    img: 'fang.png',
                },
                // {
                //     id: 84,
                //     name: '諾艾爾',
                //     name_en: 'Noel',
                //     img: 'noel.png',
                // },
                {
                    id: 85,
                    name: '雅・修特拉',
                    name_en: 'Y\'shtola',
                    img: 'yshtola.png',
                },
                {
                    id: 86,
                    name: '依達',
                    name_en: 'Yda',
                    img: 'yda.png',
                },
                {
                    id: 87,
                    name: '',
                    name_en: 'Thancred',
                    img: 'thancred.png',
                },
                {
                    id: 88,
                    name: '',
                    name_en: 'Papalymo',
                    img: 'papalymo.png',
                },
                {
                    id: 89,
                    name: '',
                    name_en: 'Alisaie',
                    img: 'alisaie.png',
                },
                {
                    id: 90,
                    name: '',
                    name_en: 'Noctis',
                    img: 'noctis.png',
                },
                {
                    id: 91,
                    name: '',
                    name_en: 'Rem',
                    img: 'rem.png',
                },
                {
                    id: 92,
                    name: '',
                    name_en: 'King',
                    img: 'king.png',
                },
                {
                    id: 93,
                    name: '',
                    name_en: 'Ace',
                    img: 'ace.png',
                },
                {
                    id: 94,
                    name: '',
                    name_en: 'Cater',
                    img: 'cater.png',
                },
                {
                    id: 95,
                    name: '',
                    name_en: 'Seven',
                    img: 'seven.png',
                },
                {
                    id: 96,
                    name: '',
                    name_en: 'Deuce',
                    img: 'deuce.png',
                },
                {
                    id: 97,
                    name: '',
                    name_en: 'Ramza',
                    img: 'ramza.png',
                },
                {
                    id: 98,
                    name: '',
                    name_en: 'Agrias',
                    img: 'agrias.png',
                },
                {
                    id: 99,
                    name: '',
                    name_en: 'Layle',
                    img: 'layle.png',
                },
                {
                    id: 100,
                    name: '',
                    name_en: 'Yuri',
                    img: 'yuri.png',
                },
                {
                    id: 101,
                    name: '',
                    name_en: 'Lannandreynn.png',
                    img: 'lannandreynn.png',
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
