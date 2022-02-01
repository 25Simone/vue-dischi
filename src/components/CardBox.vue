<template>
<!-- CARD -->
    <div class="card col-2">
        <!-- CARD IMAGE -->
        <div class="card-image">
            <img :src="disk.poster" alt='disk cover'>
        </div>
        <!-- CARD DATA -->
        <div class="card-data">
            <h3>{{disk.title}}</h3>
            <p>
                {{disk.author}}
                <br>
                {{disk.year}}
            </p>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        disk: Object
    }
}
</script>

<style lang="scss" scoped>
@import '@/style/variables.scss';

.card{
    border: none;
    background: #2e3a46;
    margin: 15px 20px;
    padding: 20px;
    display: flex;
    flex-direction: column;
    cursor: pointer;
    .card-image{
        width: 100%;
        img{
            width: 100%;
        }
    }
    .card-data{
        display: flex;
        flex-direction: column;
        align-items: center;
        h3{
            text-align: center;
            color: $primary-text-color;
        }
        p{
            color: $secondary-text-color;
            font-size: 22px;
            text-align: center;
        }
    }
}
</style>