<script>
    export let type = "button";
    export let caption;
    export let href = null;
    export let mode = null;
    export let color = null;
</script>


{#if href}
    <a href="{href}">{caption}</a>
{:else}
    <button class="{mode}" {color} type="{type}" on:click>{caption}</button>
{/if}

<style>
    button,
    a {
        font : inherit;
        border : 1px solid purple;
        background : purple;
        padding : 0.5rem 1rem;
        color : #ffffff;
        border-radius : 5px;
        box-shadow : 1px 1pxx 3px rgba(0, 0, 0, 0.26);
        cursor : pointer;
        text-decoration : none;
    }

    button:focus{
        outline : none; 
    }

    button:disabled,
    button:disabled:hover,
    button:disabled:active{
        background: #ccc;
        border-color: #ccc;
        color : #959595;
        box-shadow : none;
        cursor: not-allowed;
    } 

    button:hover,
    button:active,
    a:hover,
    a:active{
        background: purple;
        border-color: purple;
        box-shadow : 1px 1px 8px rgba(77, 51, 51, 0.26);
        color : #ffffff;
    }
</style>