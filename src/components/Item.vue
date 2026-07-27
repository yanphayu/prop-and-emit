<template>
    <div class="container">
        <div v-for="item in items" :key="item.id" class="card">
            <img loading="lazy" :src="item.image" :alt="item.name" class="card-image" />
            <div class="card-name">{{ item.name }}</div>
            <button @click="favorite(item)" class="card-btn">Favorite</button>
        </div>
    </div>
</template>

<script setup>

const { items } = defineProps({
    items: Array,
});

const emit = defineEmits({
    favorites: null
})

function favorite(item){
    emit('favorites',item);
}
</script>

<style scoped>
.container {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
    justify-items: center;
    align-items: center;
    gap: 1rem;
    padding-block: 1rem;
}

.card {
    max-width: 350px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding-bottom: 10px;
    gap: 10px;
    color: var(--text);
    border: 1px solid var(--accent);
}

.card-image {
    width: 100%;
    object-fit: cover;
}

.card-btn {
    outline: none;
    border: 1px solid var(--accent);
    background-color: var(--bg);
    color: var(--text);
    padding: 5px 10px;
    cursor: pointer;
}

.card-btn:hover {
    background-color: var(--accent-hover);
}

.card-btn:active {
    background-color: var(--accent-active);
}
</style>
