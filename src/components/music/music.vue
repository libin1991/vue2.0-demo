<template>
    <div id="music">
        <md-layout class="layout-wrap" md-gutter>
            <md-layout md-flex-xsmall="50" md-flex-small="50" md-flex-medium="33" v-for="(album, index) in albums" :key="index">
                <img class="album-img" :src="album.bg" @click="showList(index)">
            </md-layout>
        </md-layout>
    </div>
</template>
<script>
    import Store from "../../assets/js/storage.js"

    export default {
        components: {},
        data() {
            return {
                albums: [{
                    name: "飙升榜",
                    id: 19723756,
                    bg: require("./img/soar_music.jpg")
                },
                    {
                        name: "新歌榜",
                        id: 3779629,
                        bg: require("./img/new_music.jpg")
                    },
                    {
                        name: "原创榜",
                        id: 2884035,
                        bg: require("./img/original_music.jpg")
                    },
                    {
                        name: "KTV麦榜",
                        id: 21845217,
                        bg: require("./img/ktv_music.jpg")
                    },
                    {
                        name: "华语金曲榜",
                        id: 4395559,
                        bg: require("./img/chinese_music.jpg")
                    },
                    {
                        name: "我的专辑",
                        id: 98833242,
                        bg: require("./img/my_music.jpg")
                    },
                ]
            };
        },
        computed: {},
        mounted: function () {
        },
        methods: {
            showList(index) {
                this.$router.push({
                    name: 'music-list',
                    params: {
                        listId: this.albums[index].id
                    }
                })
                // 存储当前列表id到本地
                Store.set('activeListId', this.albums[index].id);
            }
        }
    }
</script>
<style scoped lang="scss">
    #music {
        height: 100vh;
        box-sizing: border-box;
        padding: 64px 0 56px;
        text-align: center;
    }

    .md-layout {
        text-align: center;
        &.layout-wrap {
            overflow-y: scroll;
            -webkit-overflow-scrolling: touch;
            height: 100%;
        }
    }

    .album-img {
        width: 100%;
        max-height: 100%;
    }
</style>



