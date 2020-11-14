<template>
    <div>
        <div class="w-100 h-64 overflow-hidden">
            <img src="https://images.unsplash.com/photo-1605014093414-29b156556886?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1267&q=80" alt="user bg" class="object-cover w-full">
        </div>
    </div>
</template>

<script>
    export default {
        name: "Show",

        data: () => {
            return {
                user: null,
                loading: true,
            }
        },

        mounted() {
            axios.get('/api/users/' + this.$route.params.userId)
                .then( res => {
                    this.user = res.data;
                })
                .catch(error => {
                    console.log('Unable to fetch User');
                })
                .finally(() => {
                    this.loading = false;
                });
            axios.get('/api/posts/' + this.$route.params.userId)
                .then( res => {
                    this.psots = res.data;
                })
                .catch(error => {
                    console.log('Unable to fetch Posts');
                })
                .finally(() => {
                    this.loading = false;
                });
        }

    }
</script>

<style scoped>

</style>
