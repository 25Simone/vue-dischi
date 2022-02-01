<template>
    <header class="container-fluid">
        <img id='logo' src="@/assets/Spotify-Icon-Logo.svg" alt="logo spotify">
        <div class="select-area">
            <!-- GENRES SELECTION -->
            <select
            name="select-genre"
            id="select-genre"
            v-model="selectedGenre"
            @change="$emit('filterGenre', selectedGenre)"
            >
            <option value="">All</option>
            <option
            v-for="(genre, index) in genres"
            :key="index"
            :value="genre"
            >
            {{genre}}
            </option>
            <!-- <option value="Jazz">Jazz</option>
            <option value="">Pop</option>
            <option value="">Rock</option>
            <option value="">Metal</option> -->
            </select>
        </div>
    </header>
</template>

<script>
export default {
    data() {
        return {
            selectedGenre: '',
        }
    },
    props: {
        genres: Array
    }
}
</script>

<style lang="scss" scoped>
header{
    background: #2e3a46;
    display: flex;
    justify-content: space-around;
    align-items: center;
    padding: 0px 20px;
    > #logo{
        width: 100px;
    }
    .select-area{
        display: flex;
    }
}
</style>