<template>
    <main>
        <div class="wrapper">
            <AlbumList/>
        </div>
    </main>
</template>

<script>
import AlbumList from './AlbumList.vue';

export default {
    components : {
        AlbumList,
    }

}
</script>

<style lang="scss">
    @import '../assets/styles/variables.scss';

    main {
        background-color: $backgroundColor;
        height: calc(100vh - 3rem);
    }

    .wrapper {
        width: 60%;
        min-width: 1000px;
        margin: 0 auto;
        border: 1px solid red;
    }


</style>