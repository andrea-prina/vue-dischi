<template>
    <select name="filterTopic"
    v-model="selectedTopic"
    @change = "$emit('search', selectedTopic, topic)">
        <option value="all">Select {{selectTopic}}</option>
        <option v-for="(option, index) in topicList" :value="option" :key="index">{{option}}</option>
    </select>
</template>

<script>
export default {

    data : function(){
        return {
            selectedTopic : "all",
            topic : this.selectTopic,
        }
    },

    props : {
        topicList : Array,
        selectTopic : String,
    }

}
</script>

<style lang="scss">
    @import '../assets/styles/variables.scss';

    select {
        width: 25%;
        margin: 1rem;
        color: #FFF;
        background-color: $backgroundColor;
        border: 0;
        border-bottom: 2px solid $accentColor;
        }


</style>