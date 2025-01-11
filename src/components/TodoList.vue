<script setup lang="ts">
    import ListItem from './ListItem.vue';
    import { ref } from 'vue';
    import type { Ref } from 'vue';
    type Item = {
        title: string;
        checked?: boolean;
    }
    const GroupsItems: Ref<Item[]> = ref([
        { title: 'Leer un libro al mes', checked: false},
        { title: 'Hacer ejercicio', checked: true},
        { title: 'Aprender algo nuevo'},
    ]);

    const updateItem = (element: Item): void => {
        const updateItem = findItemList(element)
        if (updateItem){
            toggleItemChecked(updateItem);
        }
    }

    const findItemList = (element: Item): Item | undefined => {
        return GroupsItems.value.find((elementItemInList) => elementItemInList.title === element.title);
    }

    const toggleItemChecked = (element: Item): void => {
        element.checked = !element.checked;
    }

</script>

<template>
    <ul>
        <li :key="index" v-for="(element, index) in GroupsItems">
            <ListItem :isChecked="element.checked" @updateItem="() => updateItem(element)">
                {{ element.title }}
            </ListItem>
        </li>
    </ul>
</template>

<style scoped>
</style>