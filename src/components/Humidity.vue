<template>
    <div class="humandity">
        <p>{{humandity}}%</p>
    </div>
</template>

<script>
export default {
    name: "Humandity",

    props: ['humandity']
}
</script>

<style>
    .humandity{
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

         @media only screen and (min-width: 600px) {
        .humandity{
            width: 30%;
            height: 150px;
            margin-right: 50px;
        }
    }
</style>