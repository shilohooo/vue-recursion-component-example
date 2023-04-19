<template>
    <ul class="folders">
        <li>Folders</li>
        <my-folder v-bind:folder="folder"></my-folder>
    </ul>
</template>

<script>
import MyFolder from './Folder.vue'
export default {
    name: 'MyRoot',
    components: { MyFolder },
    props: {
        folder: {
            type: Object,
            required: true,
            default: () => { },
            validator: val => typeof val === 'object'
        }
    },
    data() {
        return {

        }
    }
}
</script>

<style scoped>
ul.folders {
    padding: 1rem;
    margin: 0;
    box-sizing: border-box;
    width: 100%;
    list-style: none
}

ul.folders>li:first-child {
    padding: 1rem 1rem 1rem 0
}
</style>