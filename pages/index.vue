<template>
    <section class="section">
        <div class="container">
            <div class="columns is-multiline">
                <div
                    class="column is-one-quarter"
                    v-for="(article, index) in meals"
                    :key="index">
                        <a :href="article.url" target="_blank">
                            <div class="card">
                                <div class="card-image">
                                    <figure class="image is-3by2">
                                        <img :src="article.strMealThumb" :alt="article.strMeal">
                                    </figure>
                                </div>
                                <div class="card-content">
                                    <div class="content">{{ article.strMeal }}</div>
                                </div>
                            </div>
                        </a>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
    export default {
        async asyncData({ app }) {
            const { meals } = await app.$axios.$get(
                `https://www.themealdb.com/api/json/v1/1/lookup.php?i=52772`
            );

            return { meals };
        },
    };
</script>