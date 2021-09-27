<template>
    <header>
        <h1>BOOLFLIX</h1>
        <div>
            <input @keyup.enter= "$emit('query', query)" type="text" v-model= "query" placeholder="Film/Serie TV">
            <label for="text">
                <button @click= "$emit('query', query)">Cerca</button>
            </label>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            query: ""
        }
    }
}
</script>

<style scoped lang="scss">
    header {
    height: 10%;
    background-color: #424c55;
    display: flex;
    justify-content: space-between;
    align-items: center;
        h1 {
            color: red;
            margin-left: 20px;
        }
        input {
            height: 40px;
            padding: 5px 20px;
        }
        label {
            margin-right: 50px;
            button {
                color: white;
                background-color: rgb(211, 15, 15);
                height: 40px;
                padding: 0 20px;
                border: none;
            }
        }
    }
</style>