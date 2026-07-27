<template>
    <div class="nav-bar">
        <input type="text" v-model="search" placeholder="Search..." />
        <div class="icon">
            <svg
                xmlns="http://www.w3.org/2000/svg"
                width="20"
                height="20"
                fill="currentColor"
                class="bi bi-heart-fill"
                viewBox="0 0 16 16"
            >
                <path
                    fill-rule="evenodd"
                    d="M8 1.314C12.438-3.248 23.534 4.735 8 15-7.534 4.736 3.562-3.248 8 1.314"
                />
            </svg>
            <svg
                xmlns="http://www.w3.org/2000/svg"
                width="25"
                height="25"
                fill="currentColor"
                class="bi bi-arrow-right-short"
                viewBox="0 0 16 16"
            >
                <path
                    fill-rule="evenodd"
                    d="M4 8a.5.5 0 0 1 .5-.5h5.793L8.146 5.354a.5.5 0 1 1 .708-.708l3 3a.5.5 0 0 1 0 .708l-3 3a.5.5 0 0 1-.708-.708L10.293 8.5H4.5A.5.5 0 0 1 4 8"
                />
            </svg>
            <span style="color: var(--accent)">{{ data }}</span>
        </div>
    </div>

    <Item :items="filterItems" @favorites="favorite" />
</template>

<script setup>
import { computed, ref } from "vue";
import wallpapers from "/src/data/wallpapers.js";
import Item from "./Item.vue";

const search = ref("");
const data = ref(0);

const filterItems = computed(function () {
    return wallpapers.filter((item) => {
        return item.name.toLowerCase().includes(search.value.toLowerCase());
    });
});

function favorite(item) {
    if (item.length != 0) {
        data.value += 1;
        console.log(item);
    }
}
</script>

<style scoped>
.nav-bar {
    width: 100%;
    height: 10vh;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 1rem;
}

.nav-bar input {
    background-color: var(--bg);
    outline: none;
    border: 1px solid var(--accent);
    color: var(--text);
    font-size: 16px;
    padding: 0.5rem 1rem;
}

.nav-bar svg {
    color: var(--accent);
}

.nav-bar .icon {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 3px;

    padding: 0.31rem 1rem;
    border: 1px solid var(--accent);

    span {
        font-size: 20px;
    }
}
</style>
