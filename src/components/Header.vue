<template>
    <header>
        <div class="container">
            <div class="row">
                <div class="col padding-20">
                    <div class="input-group mb-3 justify-content-end">
                        <input type="text" placeholder="Cerca film" v-model="inputText">
                        <div class="input-group-append">
                            <button class="btn btn-outline-secondary" type="button" @click="$emit('search', inputText)">Cerca</button>
                        </div>
                    </div>
                </div> 
            </div>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',
    data(){
        return {
            inputText: ""
        }
    }
}
</script>

<style lang="scss" scoped>
.padding-20{
    padding: 20px;
}
</style>