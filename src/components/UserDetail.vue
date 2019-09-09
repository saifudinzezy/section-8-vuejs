<template>
    <div class="component">
        <h3>You may view the User Details here</h3>
        <p>Many Details</p>
        <!-- pangil key utk mengubah nilai name yg nantinya akan dipanggil oleh parent -->
        <p>User name: {{ switchName() }}</p>
    </div>
</template>

<script>
    export default {
        //key untuk parrent
        props: ['myName'],
        methods: {
            switchName(){
                return this.myName.split("").reverse().join("");
            }
        },
    }
</script>

<style scoped>
    div {
        background-color: lightcoral;
    }
</style>
