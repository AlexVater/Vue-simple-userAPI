<template>
    <div class="container">
        <h3 class="text-white">Users</h3>
        <div class="custom-flex">
            <div class="card w-25 m-1 bg-dark shadow border border-success" v-for="user in users" v-bind:key="user.id">
                <div class="card-body text-white">
                    <h4 class="card-title text-success">{{user.name}}</h4>
                    <p>{{user.email}}</p>
                    <p class="mb-0">{{user.address.city}}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Users',
    data() {
        return {
            users: null,
        }
    }, 
    created: function() {
        axios
            .get('https://jsonplaceholder.typicode.com/users')
            .then(res => {
                this.users = res.data
            })
    }
}
</script>

<style>
    h3 {
        margin-bottom: 5%;
    }

    .custom-flex {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
    }

    .c-border {
        border: 1px solid rgb(0, 252, 210);
    }
</style>