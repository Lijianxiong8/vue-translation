<template>
    <div id="translateOutput">
        <h1 class="">{{translatedText}}</h1>
    </div>
</template>

<script>
export default {
    name:"translateOutput",
    props:[
        "translatedText"
    ]
}
</script>

<style scoped>
#translateOutput {
    font-size: 32px;
    color: rgb(194, 56, 56);
}
</style>