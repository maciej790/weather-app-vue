<template>
    <div class="location">
        <h2>{{InputLocation}} {{':'}}</h2>
    </div>
</template>

<script>
export default {
    name: "Location",

    props: ['InputLocation']
}
</script>

<style>
    .location{
    width: 100%;
    display: flex;
    justify-content: center;
    margin-top: 30px;
    letter-spacing: 2px;
    }
</style>