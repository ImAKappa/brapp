<script>
    export let id;
    export let name = 'Jesus Christ';
    export let date = new Date();
</script>

<div class="birthday">
    <p>Id: {id}</p>
    <p>Name: {name}</p>
    <p>Date: {date}</p>
    <button class="delete-birthday">X</button>
</div>

<style>
    .birthday {
        border: 1px solid black;
    }
</style>