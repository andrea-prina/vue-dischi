<template>
    <div class="flex-wrap">
        <AlbumCard v-for="(album, index) in albumList" :key="index"
        :albumInfo="albumList[index]"/>
    </div>
</template>

<script>
import AlbumCard from './AlbumCard.vue';

import axios from 'axios';


export default {

    components : {
        AlbumCard,
    },

    data : function() {

        return {
            albumList : [],
        }
    },

    methods : {
        getAlbumInfo(){
            axios.get("https://flynn.boolean.careers/exercises/api/array/music")
            .then((result) => {
                this.albumList = result.data.response;
                
            }).catch((err) => {
                console.warn(err);
            });
        }
    },

    created(){
        this.getAlbumInfo();
    }

}
</script>

<style lang="scss">

    .flex-wrap {
        display: flex;
        flex-wrap: wrap;
    }
</style>