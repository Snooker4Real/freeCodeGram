<template>
    <div>
        <button class="btn btn-primary m-auto mx-4" @click="followUser" v-text="buttonText"></button>
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
                    this.status = !this.status;
                    console.log(response.data);
                })
                .catch(errors => {
                    if (errors.response.status == 401) {
                        window.location = '/login';
                    }
                });
            }
        },

        computed: {
            buttonText() {
                if (this.status) {
                    return 'Unfollow';
                } else {
                    return 'Follow';
                }
            }
        }
    }
</script>
