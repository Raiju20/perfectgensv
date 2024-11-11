<script>
    export let app_function;
    import AnimeGif from "./AnimeGif.svelte";
</script>

<div class='wrapper'>
<h1>
    Компонент 2
</h1>
<AnimeGif/>
</div>

<style>
    .wrapper{
        border:1px solid silver;
        border-radius: 30px;
        padding:30px;
    }
</style>