<script setup lang="ts">
    import ListItem from './ListItem.vue';
    type Item = {
        title: string;
        checked?: boolean;
    }
    const GroupsItems: Item[] = [
        { title: 'Leer un libro al mes', checked: true},
        { title: 'Hacer ejercicio', checked: false},
        { title: 'Aprender algo nuevo'},
    ]
</script>

<template>
    <ul>
        <li :key="index" v-for="(item, index) in GroupsItems">
            <ListItem :isChecked="item.checked">
                {{ item.title }}
            </ListItem>
        </li>
    </ul>
</template>

<style scoped>
</style>