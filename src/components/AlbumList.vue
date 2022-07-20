<template>
    <div>
        <SearchBar
        :albumsList="albumList"
        @search="filterAlbumByGenre"/>
        <div class="flex-wrap">
            <AlbumCard v-for="(album, index) in filteredAlbumList" :key="index"
            :albumInfo="album"/>
        </div>
    </div>
</template>

<script>
import AlbumCard from './AlbumCard.vue';
import SearchBar from './SearchBar.vue';

import axios from 'axios';


export default {

    components : {
        AlbumCard,
        SearchBar,
    },

    data : function() {

        return {
            albumList : [],
            filteredAlbumList : [],
            apiUrlAddress : "https://flynn.boolean.careers/exercises/api/array/music",
        }
    },

    methods : {
        getAlbumInfo(){
            axios.get(this.apiUrlAddress)
            .then((result) => {
                this.albumList = result.data.response;
                this.filteredAlbumList = [...this.albumList];
                
            }).catch((err) => {
                console.warn(err);
            });
        },

        filterAlbumByGenre(needle){
            if(needle==="all" || needle == null){
                this.filteredAlbumList = [...this.albumList];
            } else {
                console.log(needle);
                this.filteredAlbumList = [...this.albumList].filter( (album) => album.genre === needle);
            }
        }
    },

    created(){
        this.getAlbumInfo();
    }

}
</script>

<style lang="scss" scoped>

    .flex-wrap {
        display: flex;
        flex-wrap: wrap;
    }
</style>