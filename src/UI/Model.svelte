<script>
   import {createEventDispatcher} from 'svelte';
   import Button from '../UI/Button.svelte';
   export let title; 
   const dispatch = createEventDispatcher();
   function closeModel() {
       dispatch ('cancel');
   }
</script>
<div class="model-backdrop" on:click={closeModel}>

</div>
<div class="model" >
    <h1>{title}</h1>
    <div class="content">
        <slot />
    </div>
    <footer>
        <slot name="footer">
            <Button type="button" caption="Close" on:click={closeModel}/>
        </slot>
    </footer>
</div>

<style>
    .model-backdrop {
        position: fixed;
        top : 0px;
        left : 0px;
        width : 100%;
        height : 100vh;
        background : rgba(0, 0, 0, 0.75);
        z-index : 10;
    }
    .model {
        position : fixed;
        top : 10vh;
        left : 10%;
        width : 88%;
        max-height : 80vh;
        background: #ffffff;
        border-radius : 5px;
        z-index : 100;
        box-shadow: 0px 2px 8px rgba(0, 0, 0, 0.26);
        overflow: scroll;
    }
    h1{
        padding : 1rem;
        margin : 0px;
        border-radius : 1px solid #cccccc;
    }
    .content {
        padding : 1rem;
    }
    footer {
        padding : 1rem;
    }
    @media (min-width : 768px) {
        .model {
            width : 40rem;
            left : calc(50% - 20rem);
        }
    }
</style>