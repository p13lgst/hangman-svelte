<script>
    export let word;
    export let revealed;
</script>

<style>
    .wrapper {
        height: 30px;
        display: flex;
        justify-content: center;
    }
    
    .letter {
        font-size: 1.6em;
        width: 1em;
        border-bottom: 2px solid black;
    }

    .letter:not(:first-child) {
        margin-left: 7px;
    }
 
</style>

<div class="wrapper"> 
    {#each word as letter, i}
    <div class="letter">
    {#if revealed[i]}
    {letter}
    {/if}
    </div>
    {/each}
</div>