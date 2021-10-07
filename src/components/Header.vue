<template>
    <header>
        <div class="container">
            <div class="row">
                <div class="col padding-20 logo">
                    <a href="#"><img src="https://fontmeme.com/permalink/211007/e0f90358ce3490bb6bab27460a167c80.png" alt="Boolflix Logo" border="0"></a>
                </div>
                <div class="col padding-20">
                    <form>
                        <div class="input-group mb-3 d-flex flex-nowrap justify-content-end">
                            <input type="text" placeholder="Cerca" v-model="inputText">
                            <div class="input-group-append mx-1">
                                <button class="btn btn-dark" type="submit" @click.prevent="$emit('search', inputText)"><i class="fas fa-search"></i></button>
                            </div>
                        </div>
                    </form>
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

.padding-20{
    padding: 20px;
}

input[type=text] {
    color: white;
    padding: 0 10px;
    border: 1px solid rgb(219, 217, 217);
    background-color: $bgColor;
}

button {
    background-color: $bgColor; 
}
</style>