<template>
    <div class="temperature">
        <p>22°</p>
    </div>
</template>

<script>
export default {
    name: "Temperature"
}
</script>

<style scoped>
    .temperature{
        width: 100%;
        display: flex;
        justify-content: center;
        margin-top: 50px;
    }

    p{
        font-size: 80px;
        font-weight: bold;
        border-bottom: 2px solid white;
    }
</style>
