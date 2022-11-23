<template>
    <div class="popup">
        <select v-model="formData.category">
            <option v-bind:value="cat" v-for="cat, idx of categories" v-bind:key="idx">
                {{ cat }}
            </option>
        </select>
        <input v-model="formData.count" type="text" />
        <div class="btngroup">
            <button v-on:click="$emit('close')">Отмена</button>
            <button v-on:click="$emit('add', formData)">Добавить</button>
        </div>

    </div>
</template>

<script>
export default {
    name: "Popup",
    props: {
        categories: Array
    },
    data() {
        return {
            formData: {
                category: this.categories[0],
                count: 0
            }
        }
    }
}
</script>

<style lang="scss">
.popup {
    width: 600px;
    height: 200px;
    padding: 30px;
    background-color: white;
    border: 1px solid #444;
    border-radius: 10px;
    position: absolute;
    top: 300px;
    left: calc(50% - 300px);

    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: stretch;
}
</style>