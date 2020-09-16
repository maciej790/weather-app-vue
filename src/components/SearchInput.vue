<template>
    <div class="searchinput">
        <input type="text" id="inp" placeholder="London">
    </div>
</template>

<script>
export default {
    name: "SearchInput"
}
</script>

<style>
.searchinput{
    width: 100%;
    display: flex;
    justify-content: center;
    margin-top: 25px;
}

#inp{
    width: 50%;
    text-align: center;
    border: none;
    border-bottom: 2.5px solid white;
    background-color: transparent;
    color: white;
    font-size: 25px;
    padding: 5px 0 5px 0;
}

::placeholder{
    color: white;
    font-size: 20px;

}
</style>