<template>
    <div class="wind">
        <p>{{wind}}mph</p>
    </div>
</template>

<script>
export default {
    name: "Wind",

    props: ['wind']
}
</script>

<style>
    .wind{
        width: 60%;
        height: 120px;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-top: 50px;
        background-color: rgba(0, 255, 191, 0.5);
        border-radius: 15px;
    }

       p{
        font-size: 30px;
    }
</style>