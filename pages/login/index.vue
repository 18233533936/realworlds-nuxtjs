<template>
  
<div class="auth-page">
    <div class="container page">
        <div class="row">

            <div class="col-md-6 offset-md-3 col-xs-12">
                <h1 class="text-xs-center">{{ isLogin ? 'Sign in' : 'Sign up' }}</h1>
                <p class="text-xs-center">
                    <nuxt-link v-if="isLogin" to="/register">Need an account?</nuxt-link>
                    <nuxt-link v-else to="/login">Have an account?</nuxt-link>
                </p>

                <ul class="error-messages">
                    <template
                    v-for="(messages, field) in errors"
                    >
              <li
                v-for="(message, index) in messages"
                :key="index"
              >{{ field }} {{ message }}
            </li>
            </template>
</ul>

<form @submit.prevent="onSubmit">
    <fieldset v-if="!isLogin" class="form-group">
        <input class="form-control form-control-lg" v-model="user.username" type="text" placeholder="Your Name" required>
    </fieldset>
    <fieldset class="form-group">
        <input class="form-control form-control-lg" v-model="user.email" type="email" placeholder="Email" required>
    </fieldset>
    <fieldset class="form-group">
        <input class="form-control form-control-lg" v-model="user.password" type="password" placeholder="Password" required>
    </fieldset>
    <button class="btn btn-lg btn-primary pull-xs-right">
                        {{ isLogin ? 'Sign in' : 'Sign up' }}
                    </button>
</form>
</div>

</div>
</div>
</div>
</template>

<script>
    import {
        login,
        register
    } from '@/api/user'
    //仅在客户端加载
    const Cookie = process.client ? require('js-cookie') : undefined
    export default {
        middleware: 'notAuthenticated',
        name: 'LoginIndex',
        computed: {
            isLogin() {
                return this.$route.name === 'login'
            }
        },
        props: [''],
        data() {
            return {
                user: {
                    // username: '',
                    email: 'fanxiaoliang1@126.com',
                    password: 'fan123456'
                },
                errors: {}
            }
        },

        components: {},

        beforeMount() {},

        mounted() {},

        methods: {
            // 表单登录
            async onSubmit() {
                try {
                    const {
                        data
                    } = this.isLogin ?
                        await login({
                            user: this.user
                        }) :
                        await register({
                            user: this.user
                        })
                    console.log(data)
                    this.$store.commit('setUser', data.user)

                    // 保存登录状态 TODO8/
                    Cookie.set('user', JSON.stringify(data.user))
                        // 成功以后跳转到首页
                    this.$router.push('/')
                } catch (error) {
                    this.errors = error.response.data.errors
                }

            }
        },

        watch: {}

    }
</script>
<style lang='' scoped>

</style>