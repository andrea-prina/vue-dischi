<template>
    <div class="flex-wrap">
        <AlbumCard/>
        <AlbumCard/>
        <AlbumCard/>
        <AlbumCard/>
        <AlbumCard/>
        <AlbumCard/>
        <AlbumCard/>
        <AlbumCard/>
        <AlbumCard/>
        <AlbumCard/>
    </div>
</template>

<script>
import AlbumCard from './AlbumCard.vue'; 

export default {

    components : {
        AlbumCard,
    }

}
</script>

<style lang="scss">

    .flex-wrap {
        display: flex;
        flex-wrap: wrap;
    }
</style>