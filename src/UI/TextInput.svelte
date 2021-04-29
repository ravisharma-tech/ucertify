<script>
    export let controlType = null;
    export let id;
    export let label;
    export let rows = null;
    export let value;
    export let type = null;
</script>

<div class="form-control">
    <label for="{id}">{label}</label>
    {#if controlType === 'textarea'}
    <textarea rows="{rows}"  id="{id}" value={value} on:input />   
    {:else}
    <input type="{type}" id="{id}" value={value} on:input>
    {/if}
</div>


<style>
    input {
        display : block;
        width : 100%;
        font : inherit;
        border : none; 
        border-bottom : 2px solid #ccc;
        background-color :#ffffff;
        padding : 0.15rem 0.25rem;
        transition: border-color 0.1s easy-out;
        height : 2.5rem;
        border-radius : 0.25rem;
    }

    textarea {
        display : block;
        width : 100%;
        font : inherit;
        border : none; 
        border-bottom : 2px solid #ccc;
        background-color :#ffffff;
        padding : 0.15rem 0.25rem;
        transition: border-color 0.1s easy-out;
        border-radius : 0.25rem;
    }

    input:focus,
    textarea:focus {
        border-color : purple;
        outline : none;
    }

    label{
        display : block;
        margin-bottom : 0.25rem;
        width : 100%;
    }
    .form-control {
        padding : 0.5rem 0;
        width : 100%;
        margin : 0.05rem 0;
    }
</style>