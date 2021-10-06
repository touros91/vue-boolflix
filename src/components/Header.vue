<template>
    <header>
        <div class="container">
            <div class="row">
                <div class="col logo padding-20">BOOLFLIX</div>
                <div class="col padding-20">
                    <div class="input-group mb-3 justify-content-end">
                        <input type="text" placeholder="Cerca film" v-model="inputText">
                        <div class="input-group-append mx-1">
                            <button class="btn btn-light" type="button" @click="$emit('search', inputText)"><i class="fas fa-search"></i></button>
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
@import '../assets/style/common.scss';

.logo {
    font-size: 30px;
    font-weight: bold;
    color: red;
}

.padding-20{
    padding: 20px;
}

input[type=text] {
    padding: 0 10px;
}
</style>