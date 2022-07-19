<template>
    <div class="card">
        <img src="https://previews.123rf.com/images/niroworld/niroworld1405/niroworld140500052/29004635-vintage-music-record-concept-with-a-red-vinyl-lp-album-disc-and-light-reflection.jpg" alt="">
        <h3>NOME</h3>
        <p>Artista</p>
        <p>Anno</p>

    </div>
</template>

<script>
export default {

}
</script>

<style lang="scss">
    @import '../assets/styles/variables.scss';

    div.card {
        width: calc((100% - 1.5rem * 2 * 5) / 5);
        padding: 1rem 0.5rem;
        margin: 0.5rem 1.5rem;
        text-align: center;

        background-color: $accentColor;

        img {
            width: 80%;
        }

        h3 {
            margin: 0.5rem 0;
        }
    }


</style>