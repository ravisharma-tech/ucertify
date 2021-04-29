<script>
    import {createEventDispatcher} from 'svelte';
    import Button from '../UI/Button.svelte';
    export let id;
    export let title;
    export let subtitle;
    export let description;
    export let imageUrl;
    export let address;
    export let contactEmail;
     export let isFav;
    const dispatch = createEventDispatcher();
</script>


<article>
    <header>
        <h1>{title}</h1>
        <h3>{subtitle}</h3>
        <p>Address : {address}</p>
    </header>
    <div class="image">
        <img src="{imageUrl}" alt="{title}">
    </div>
    <div class="content">
        <p>{description}</p>
    </div>
    <footer>
        <Button href="mailto:{contactEmail}" caption="Contact" /> 
        <Button type="button" caption="Show Details" />
        <Button type="button" caption="{isFav ? 'Unfavorite' : 'Favourite'}" on:click={() => dispatch('togglefavorite',id)}/>
    </footer>
</article>

<style>
    article {
        box-shadow : 0px 2px 8px rgba(0,0,0,0.26);
        border-radius : 5px;
        background-color: #ffffff;
        margin : 1rem;
        border-top : 3px solid purple; 
    }
    
    header p {
        font-size : 1rem;
        color : #808080;
    }

    header,
    .content,
    footer {
        padding : 1rem;
    }
    .image {
        width : 100%;
        height: 14rem;
    }
    .image img {
        width : 100%;
        height : 100%;
        object-fit : cover;
    }

    h1{
        font-size : 2rem;
        margin : 0.1rem 0;
        font-weight: 400; 
    }
    h3 {
        font-size : 1.25rem;
        color : #808080;
        margin : 0.1rem 0;
        font-weight: 400;
    }

    p {
        font-size : 1.25rem;
        margin : 0px;
    }
    div {
        text-align : right;
    }
</style>