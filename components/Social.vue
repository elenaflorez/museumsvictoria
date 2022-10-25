<template>
    <div class="linkContainer">
        <div>

        </div>
        <a href="https://www.instagram.com/canberra_modern/">
            <img class="iLink" src="@/Images/Instagram Image.png" alt="Banner" /> 
        </a>
        <a href="https://www.facebook.com/canberramodern/">
            <img class="fbLink" src="@/Images/Facebook Icon.png" alt="Banner" /> 
        </a>
    </div>
</template>

<script>

</script>

<style>
    .fbContainer {
        grid-column-start: 3;
    }
    .iContainer {
        grid-column-start: 4;
    }
    .fbLink {
        width:50%;
    }
    .iLink {
        width:35%;
        padding-top:10px;
    }
    .linkContainer {
        text-align:center;
        padding-top:20px;
        display:grid;
        grid-template-columns: 70% 10% 10% 10%;
        /* display: flex;
        flex-direction: row; */
        background-color: #539844;
        width:100%;
        border-top-left-radius: 10px;
        border-top-right-radius: 10px;
        box-shadow: 0 -8px 8px -4px #e3e3e3;
        /* position: absolute; */
        bottom: 0;
    }
</style>