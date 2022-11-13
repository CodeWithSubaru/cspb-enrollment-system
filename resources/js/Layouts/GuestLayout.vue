<script setup>
import { Link, Head } from "@inertiajs/inertia-vue3";
</script>

<template>
    <main class="login">
        <div class="login-left">
            <div class="logo">
                <Link href="/">
                    <img src="img/logo.png" />
                    <h2>Enrollment System</h2>
                </Link>
            </div>

            <main class="">
                <slot />
            </main>
        </div>
        <aside class="login-right">
            <div class="overlay"></div>
            <div class="clouds">
                <img
                    src="/img/cloud-login-long.png"
                    class="cloud-long"
                    alt="Long Cloud"
                />
                <img
                    src="/img/cloud-login-short.png"
                    class="cloud-short"
                    alt="Short Cloud"
                />
            </div>
            <div class="person">
                <img
                    src="/img/student-top-of-books.png"
                    class="student"
                    alt="student-top-of-books"
                />
            </div>
        </aside>
    </main>
</template>

<style scoped>
.login {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: 100vh;
}

/* Left Login */
.login-left {
    background: #b18c3d;
    display: flex;
    flex-direction: column;
}

.login-left .logo {
    padding: 2rem;
}

.login-left .logo a {
    display: inline-flex;
    align-items: center;
    column-gap: 1rem;
}

.login-left .logo a img {
    height: 130px;
}

.login-left .logo a h2 {
    color: #fff;
    font-size: 3.2rem;
}

.login-left main {
    padding: 0 14rem;
    flex: 1;
}

/* Login Right */
.login-right {
    background-image: url(/img/background-login.jpg);
    background-size: cover;
    position: relative;
}
.login-right .overlay {
    content: "";
    display: block;
    background: #f2d0d0;
    height: 100vh;
    width: 100%;
    mix-blend-mode: multiply;
}

.clouds,
.person {
    position: absolute;
    z-index: 10;
}

.clouds {
    display: flex;
    justify-content: space-between;
    width: 100%;
    top: 1rem;
}

.clouds .cloud-long {
    height: 14rem;
    margin-top: 8rem;
    margin-left: 12rem;
}

.clouds .cloud-short {
    height: 14rem;
    margin-top: 18rem;
    margin-right: 12rem;
}

.person {
    bottom: 2rem;
    display: flex;
    justify-content: center;
    width: 100%;
}

@media (max-width: 1210px) {
    .login {
        grid-template-columns: 1fr;
    }

    .login-left main {
        padding: 0 8rem 8rem;
    }
}

@media (max-width: 460px) {
    .login-left {
        min-height: 100vh;
    }

    .login-left main {
        padding: 3rem;
        max-width: 460px;
    }

    .login-left .logo a img {
        height: 100px;
    }
}
</style>
