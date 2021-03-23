<template>
    <div>
        <h1>{{message}}</h1>
     </div>
</template>


<script>
export default {
   props: {
       message: {
           type: String, 
           required: true,
           default: 'Parameters of default',
       }
   }
}
</script>


<style lang="scss" scoped>
    h1 {
        margin-top: 25px;
        color: red;
    }
</style>