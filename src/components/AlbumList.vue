<template>
    <div>
        <div class="flex-wrap">
            <FilterSelect :topicList="getUniqueTopicValues('genre')" :selectTopic="'genre'" @search="filterAlbumByTopic"/>
            <FilterSelect :topicList="getUniqueTopicValues('author')" :selectTopic="'author'" @search="filterAlbumByTopic"/>
            
        </div>
        <div class="flex-wrap">
            <AlbumCard v-for="(album, index) in filteredAlbumList" :key="index"
            :albumInfo="album"/>
        </div>
    </div>
</template>

<script>
import AlbumCard from './AlbumCard.vue';
import FilterSelect from './FilterSelect.vue';

import axios from 'axios';


export default {

    components : {
        AlbumCard,
        FilterSelect,
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

        getUniqueTopicValues(topic){

            let topicList = [];

            this.albumList.forEach(element => {
                if (!topicList.includes(element[topic])){
                    topicList.push(element[topic])
                }                
            });

            return topicList;


        },

        filterAlbumByTopic(needle, topic){
            if(needle==="all" || needle == null){
                this.filteredAlbumList = [...this.albumList];
            } else {
                this.filteredAlbumList = [...this.albumList].filter( (album) => album[topic] === needle);
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
        justify-content: center;
        flex-wrap: wrap;
    }
</style>