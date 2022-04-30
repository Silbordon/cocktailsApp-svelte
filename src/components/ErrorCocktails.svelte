7 lines (6 sloc)  152 Bytes
   
<script lang="ts">
    export let err: Error;
</script>

<div class="alert alert-danger animate__animated animate__jello" role="alert">
    {err}
</div>