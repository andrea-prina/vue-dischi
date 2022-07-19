<template>
    <div class="card">
        <img :src="albumInfo.poster" :alt="albumInfo.title">
        <h3>{{albumInfo.title}}</h3>
        <p>{{albumInfo.author}}</p>
        <p>{{albumInfo.year}}</p>

    </div>
</template>

<script>
export default {

    props : {
        albumInfo : Object,
    },

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
        color: #7b7978;

        img {
            width: 80%;
        }

        h3 {
            margin: 0.5rem 0;
            color: #FFF;
            text-transform: uppercase;
        }

        p {
            font-size: 0.8rem;
        }
    }


</style>