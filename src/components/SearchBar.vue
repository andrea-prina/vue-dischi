<template>
    <div id="search-bar">
        <input type="text" placeholder="Type the genre and press ENTER to search"
        v-model.trim="searchQuery"
        @keyup.enter="$emit('search', searchQuery)"/>
    </div>
</template>

<script>
export default {

    data : function(){
        return {
            searchQuery : "",
        }
    },

    methods : {
        log(string){
            console.log(string);
        }
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

        input {
            color: #FFF;
            background-color: $backgroundColor;
            border: 0;

            &[type="text"]{
                width: 50%;
                line-height: 1.5rem;
                border-bottom: 2px solid $accentColor;
            }

        }
    }

</style>