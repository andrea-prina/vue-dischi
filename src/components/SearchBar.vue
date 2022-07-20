<template>
    <div id="search-bar">
        <!-- <input type="select" placeholder="Type the genre and press ENTER to search"
        v-model.trim="searchQuery"
        @keyup.enter="$emit('search', searchQuery)"/> -->

        <select name="genres"
        v-model="selectedGenre"
        @change = "$emit('search', selectedGenre)">
            <option value="all">Select a genre</option>
            <option v-for="(album, index) in albumsList" :value="album.genre" :key="index">{{album.genre}}</option>
        </select>
    </div>
</template>

<script>
export default {

    data : function(){
        return {
            selectedGenre : "all",
        }
    },

    methods : {
        log(string){
            console.log(string);
        }
    },

    props : {
        albumsList : Array,
    }

}
</script>

<style lang="scss">
    @import '../assets/styles/variables.scss';

    #search-bar {
        width: 100%;
        display: flex;
        justify-content: center;
        margin-bottom: 2rem;

        select {
            color: #FFF;
            background-color: $backgroundColor;
            border: 0;
            width: 30%;
            border-bottom: 2px solid $accentColor;
            }

        }

</style>