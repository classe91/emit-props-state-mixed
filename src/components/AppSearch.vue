<script>
import { store } from '../store.js'
export default {
    name: "AppSearch",
    data() {
        return {
            store,
            categories: [
                "PC",
                "Browser",
            ],
        }
    },
};
</script>
    
<template>
    <section class="search py-4">
        <div class="container">
            <div class="row">
                <div class="col-12">
                    <form class="d-flex justify-content-between align-items-center">
                        <div class="form-group">
                            <label class="text-light" for="platform">Platform selection:</label>
                            <select id="platform" v-model="store.categoryValue" @change="$emit('performSearch')"
                                class="form-select search-select">
                                <option value="">All</option>
                                <option v-for="(category, index) in this.categories" :key="index"
                                    :value="category.toLowerCase()">
                                    {{ category }}
                                </option>
                            </select>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </section>
</template>
    
<style scoped lang="scss">
@use '../styles/partials/variables' as *;

.search {
    background-color: $bg-color;
    flex-basis: 50%;
}

.search-container {
    width: 250px;
}

.search-select {
    max-width: 200px;
}
</style>
    