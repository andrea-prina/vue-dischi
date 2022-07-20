<template>
    <div>
        <SearchBar @search="filterAlbumByGenre"/>
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
            if(needle==="" || needle == null){
                this.filteredAlbumList = [...this.albumList];
            } else {
                this.filteredAlbumList = [...this.albumList].filter( (album) => album.genre.toLowerCase().includes(needle));
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