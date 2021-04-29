<script>
    import {createEventDispatcher} from 'svelte';
    import TextInput from '../UI/TextInput.svelte';
    import Button from '../UI/Button.svelte';
    import Model from '../UI/Model.svelte';
    let title= '';
	let subtitle = '';
	let address = '';
	let imageUrl = '';
	let contactEmail = '';
	let description = '';
    const dispatch = createEventDispatcher();
    function submitForm() {
            dispatch('save',{
                title : title,
                subtitle : subtitle,
                address : address,
                description : description,
                imageUrl : imageUrl
            });
    }
</script>
<Model title="Edit Meetup Data" on:cancel>
<form on:submit|preventDefault="{submitForm}">
    <TextInput 
    id = "title"
    label = "Title"
    value = {title}
    type="text"
    on:input={event => {title = event.target.value}} />
    
    <TextInput 
    id = "subtitle"
    label = "Sub - Title"
    value = {subtitle}
    type="text"
    on:input={event => {subtitle = event.target.value}} />

    <TextInput 
    id = "address"
    label = "Address"
    value = {address}
    type="text"
    on:input={event => {address = event.target.value}} />

    <TextInput 
    id = "imageUrl"
    label = "Image URL"
    value = {imageUrl}
    type="text"
    on:input={event => { imageUrl = event.target.value}} />

    <TextInput 
    id = "contactEmail"
    label = "Email"
    value = {contactEmail}
    type="email"
    on:input={event => {contactEmail = event.target.value}} />

    <TextInput 
    id = "description"
    label = "Description"
    value = {description}
    controlType = 'textarea'
    on:input={event => {description = event.target.value}} />
    <Button type="submit" caption="save"/>
</form>
</Model>
<style>
    form {
		width : 100%;
		max-width : 98%;
		margin-left : auto;
		margin-right : auto;
	}
</style>