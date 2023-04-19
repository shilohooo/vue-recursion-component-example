<template>
    <li class="folder" v-bind:class="[folder.leaf ? 'is-leaf' : 'is-folder']">
        <span v-on:click="expand()">{{ folder.text }}</span>

        <ul class="sub-folders" v-if="folder.children && folder.children.length" v-show="folder.expanded">
            <my-folder v-for="(child, index) in folder.children" v-bind:folder="child" :key="index"></my-folder>
        </ul>
        <div class="folder-empty" v-else v-show="!folder.leaf && folder.expanded">No Data</div>
    </li>
</template>

<script>
export default {
    name: "MyFolder",
    props: {
        folder: {
            type: Object,
            required: false,
            default: () => { },
            validator: val => typeof val === 'object'
        }
    },
    data() {
        return {
            childFolder: undefined
        }
    },
    mounted() {
        this.childFolder = this.folder
    },
    methods: {
        expand() {
            if (this.folder.leaf) {
                return;
            }

            this.childFolder.expanded = !this.childFolder.expanded;
        }
    }
}
</script>

<style scoped>
li.is-folder {
    padding: 1rem;
    border-left: 1px solid #d3d3d3;
    margin-bottom: 0.5rem
}

li.is-folder>span {
    padding: 0.5rem;
    border: 1px solid #d3d3d3;
    cursor: pointer;
    display: inline-block
}

li.is-leaf {
    padding: 0 0 0 1rem;
    color: #000;
}

ul.sub-folders {
    padding: 1rem 1rem 0 0;
    margin: 0;
    box-sizing: border-box;
    width: 100%;
    list-style: none
}

div.folder-empty {
    padding: 1rem 1rem 0 1rem;
    color: #000;
    opacity: 0.5
}
</style>