
<template>
    <header>
        <h1>{{ title }}</h1>
        <ButtonItem @btn-click="$emit('toggle-add-task')" :text="boolean ? 'Close' : 'Add task'" :color="boolean? 'red':'green'" />
    </header>
</template>

<script>
import ButtonItem from './Button';

export default {
    name: 'HeaderItem',
    props: {
        title: String, // Define title as a string prop
        boolean: Boolean // Define boolean as a boolean prop
    },
    components: {
        ButtonItem,
    }
}
</script>


<!-- only for this component -->
<style scoped>
    header{
        display:flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }
</style>
