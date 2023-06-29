<template>
    <div>
        <button class="btn btn-primary m-auto mx-4" @click="followUser">Follow</button>
    </div>
</template>

<script>
    export default {
        props: ['userId', 'follows'],
        mounted() {
            console.log('Component mounted.')
        },

        data: function (){
            return {
                status : this.follows,
            }
        },

        methods: {
            followUser() {
                axios.post('/follow/' + this.userId)
                    // {
                    // user_id: this.user_id
                // })
                .then(response => {
                    console.log(response.data);
                })
                .catch(error => {
                    console.log(error);
                });
            }
        }
    }
</script>
