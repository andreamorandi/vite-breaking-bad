<script>
import { store } from "../store";

export default {
    name: "AppSearch",
    data() {
        return {
            store,
            categoryOptions: ["Breaking Bad", "Better Call Saul"]
        };
    },
};
</script>

<template>
    <div class="d-flex justify-content-center">
        <input type="text" placeholder="Filter by name" class="form-control" v-model="store.searchKey">
        <select class="form-select" aria-label="Default select example" v-model="store.searchCategory">
            <option selected value="">Select series</option>
            <option v-for="(categoryOption,index) in categoryOptions" :key="index" :value="categoryOption">{{ categoryOption }}</option>
        </select>
        <button class="btn btn-primary" @click="$emit('performSearch')">Search</button>
    </div>
</template>

<style lang="scss" scoped>
input,
select {
    width: 30%;
    margin: 0 2rem;
}
</style>