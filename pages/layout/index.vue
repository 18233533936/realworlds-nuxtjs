<template>
    <div>
        <!-- 公共顶部 -->
        <nav class="navbar navbar-light">
            <div class="container">
                <!-- <a class="navbar-brand" href="index.html">conduit</a> -->
                <nuxt-link
                class="navbar-brand"
                to="/"
                >Home</nuxt-link>
                <ul class="nav navbar-nav pull-xs-right">
                    <li class="nav-item">
                        <!-- Add "active" class when you're on that page" -->
                        <nuxt-link
                        class="nav-link"
                        to="/"
                        exact
                        >Home</nuxt-link>
                    </li>
                    <template v-if="user">
                    <li class="nav-item">
                        <nuxt-link
                            class="nav-link"
                            to="/editor"
                        >
                        <!-- <a class="nav-link" href=""> -->
                            <i class="ion-compose"></i>&nbsp;New Article
                        <!-- </a> -->
                    </nuxt-link>
                    </li>
                    <li class="nav-item">
                        <!-- <a class="nav-link" href=""> -->
                            <nuxt-link
                            class="nav-link"
                            to="/settings"
                          >
                            <i class="ion-gear-a"></i>&nbsp;Settings
                        </nuxt-link>
                        <!-- </a> -->
                    </li>
                    <li class="nav-item">
                        <nuxt-link class="nav-link" to="/profile/123">
                          <img
                            class="user-pic"
                            :src="user.image"
                          >
                         {{user.username}}
                        </nuxt-link>
                      </li>
                    </template>
<template v-else>
                        <li class="nav-item">
                            <nuxt-link
                                class="nav-link"
                                to="/login"
                            >Sign in
                            </nuxt-link>
                            <!-- <a class="nav-link" href="">
                                Sign in</a> -->
                        </li>
                        <li class="nav-item">
                            <nuxt-link
                                class="nav-link"
                                to="/register"
                            >Sign up</nuxt-link>
                            <!-- <a class="nav-link" href="">Sign up</a> -->
                        </li>
                    </template>

</ul>
</div>
</nav>
<!-- 公共顶部 -->

<!-- 中间公共部分子路由 -->
<nuxt-child></nuxt-child>
<!-- 中间公共部分子路由 -->


<!-- 公共底部 -->

<footer>
    <div class="container">
        <a href="/" class="logo-font">conduit</a>
        <span class="attribution">
          An interactive learning project from <a href="https://thinkster.io">Thinkster</a>. Code &amp; design licensed under MIT.
        </span>
    </div>
</footer>

<!-- 公共底部 -->
</div>
</template>

<script>
    import {
        mapState
    } from 'vuex'
    export default {
        name: 'LayoutIndex',
        props: [''],
        data() {
            return {

            };
        },

        components: {},

        computed: {
            ...mapState(['user'])
        },

        beforeMount() {},

        mounted() {},

        methods: {},

        watch: {}

    }
</script>
<style lang='' scoped>

</style>