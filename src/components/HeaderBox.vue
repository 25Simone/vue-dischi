<template>
    <header class="container-fluid">
        <img id='logo' src="@/assets/Spotify-Icon-Logo.svg" alt="logo spotify">
        <div class="select-area">
            <!-- GENRES SELECTION -->
            <label>
                Select by Genre
                <select
                class="me-3"
                name="select-genre"
                id="select-genre"
                v-model="selectedGenre"
                @change="$emit('filterGenre', selectedGenre)"
                >
                    <option value="all">All</option>
                    <option
                    v-for="(genre, index) in genres"
                    :key="index"
                    :value="genre.toLowerCase()"
                    >
                    {{genre}}
                    </option>
                    </select>
            </label>
        </div>
    </header>
</template>

<script>
export default {
    data() {
        return {
            selectedGenre: 'all',
            selectedArtist: 'all',
        }
    },
    props: {
        genres: Array,
        artists: Array,
    }
}
</script>

<style lang="scss" scoped>
header{
    background: #2e3a46;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0px 20px;
    > #logo{
        width: 100px;
    }
    .select-area{
        display: flex;
        label{
            font-size: 18px;
            font-weight: 500;
            color: #1ed660;
            select{
                border-radius: 10px;
                border-color: #1e2d3b;
            }
        }
    }
}
</style>