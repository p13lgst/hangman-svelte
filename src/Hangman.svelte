<script>
    export let lifes;
</script>

<style>
    .hangman {
        height: 350px;
        width: 231px;
        position: relative;
        margin: 0 auto 7px;
    }

    .gallows {
        position: relative;
    }

    .gallows .top {
        background: black;
        height: 7px;
        width: 140px;
        position: absolute;
        top: 17.5px;
        left: 66.5px;
    }

    .gallows .left {
        background: black;
        height: 315px;
        width: 7px;
        top: 17.5px;
        left: 66.5px;
        position: absolute;
    }

    .gallows .bottom {
        background: black;
        height: 7px;
        width: 140px;
        top: 325.5px;
        position: absolute;
    }

    .gallows .corner {
        background: black;
        height: 7px;
        width: 65.8px;
        top: 40px;
        transform: rotate(-45deg);
        left: 59.5px;
        position: absolute;
    }

    .gallows .rod {
        background: black;
        width: 3px;
        height: 52.5px;
        position: absolute;
        top: 18.2px;
        left: 196px;
    }

    .man {
        position: relative;
        top: 68.8px;
        left: 177.1px;
    }

    .man .head {
        height: 35px;
        width: 35px;
        border: 3px solid black;
        border-radius: 50%;
        position: absolute;
    }

    .man .body {
        position: absolute;
        width: 3px;
        height: 63.7px;
        background: black;
        left: 18.9px;
        top: 40px;
    }

    .man .left-arm,
    .man .left-leg {
        position: absolute;
        background-color: black;
        height: 49px;
        width: 3px;
        left: 5px;
        transform: rotate(35deg);
    }

    .man .right-arm,
    .man .right-leg {
        position: absolute;
        background-color: black;
        height: 49px;
        width: 3px;
        left: 32.9px;
        transform: rotate(-35deg);
    }

    .man .left-arm,
    .man .right-arm {
        top: 42px;
    }

    .man .left-leg,
    .man .right-leg {
        top: 98px;
    }

</style>

<div class="hangman">
    <div class="gallows">
        <div class="top"></div>
        <div class="left"></div>
        <div class="corner"></div>
        <div class="bottom"></div>
        <div class="rod"></div>
    </div>
    <div class="man">
        {#if lifes <= 5}
        <div class="head"></div>
        {/if}
        {#if lifes <= 4}
        <div class="body"></div>
        {/if}
        {#if lifes <= 3}
        <div class="left-arm"></div>
        {/if}
        {#if lifes <= 2}
        <div class="right-arm"></div>
        {/if}
        {#if lifes <= 1}
        <div class="left-leg"></div>
        {/if}
        {#if lifes <= 0}
        <div class="right-leg"></div>
        {/if}
    </div>
</div>