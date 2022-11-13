<script setup>
import Checkbox from "@/Components/Checkbox.vue";
import GuestLayout from "@/Layouts/GuestLayout.vue";
import InputError from "@/Components/InputError.vue";
import InputLabel from "@/Components/InputLabel.vue";
import PrimaryButton from "@/Components/PrimaryButton.vue";
import TextInput from "@/Components/TextInput.vue";
import { Head, Link, useForm } from "@inertiajs/inertia-vue3";

defineProps({
    canResetPassword: Boolean,
    status: String,
});

const form = useForm({
    email: "",
    password: "",
    remember: false,
});

const submit = () => {
    form.post(route("login"), {
        onFinish: () => form.reset("password"),
    });
};
</script>

<template>
    <GuestLayout>
        <Head title="Log in" />

        <div v-if="status" class="mb-4 font-medium text-sm text-green-600">
            {{ status }}
        </div>

        <form @submit.prevent="submit">
            <div>
                <h1>Login</h1>
                <p>Please login your credentials</p>
            </div>
            <div class="form-group">
                <InputLabel for="email" value="Email" />
                <TextInput
                    id="email"
                    type="email"
                    class="mt-1 block w-full"
                    v-model="form.email"
                    autofocus
                    pattern="[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,4}$"
                    aria-required="true"
                    placeholder="Enter valid email address"
                />
                <InputError class="mt-2" :message="form.errors.email" />
            </div>

            <div class="form-group">
                <InputLabel for="password" value="Password" />
                <TextInput
                    id="password"
                    type="password"
                    class="mt-1 block w-full"
                    v-model="form.password"
                    pattern=".{8,}"
                    required
                    placeholder="Enter password"
                />
                <InputError class="mt-2" :message="form.errors.password" />
            </div>

            <div class="form-group checkbox">
                <Checkbox
                    name="remember"
                    id="remember"
                    v-model:checked="form.remember"
                />
                <InputLabel for="remember">Remember me</InputLabel>
            </div>

            <PrimaryButton :disabled="form.processing"> Log in </PrimaryButton>

            <div class="link-action">
                <Link :href="route('register')" class=""> Register </Link>
                <Link
                    v-if="canResetPassword"
                    :href="route('password.request')"
                    class=""
                >
                    Forgot your password?
                </Link>
            </div>
        </form>
    </GuestLayout>
</template>

<style scoped>
form {
    height: 100%;
    flex: 1;
    display: flex;
    flex-direction: column;
    row-gap: 3rem;
}

form h1 {
    font-size: 4rem;
    color: #fff;
}

form p {
    font-size: 2.4rem;
    color: #f2d0d0;
}

.form-group label,
.form-group checkbox {
    font-size: 2rem;
    display: block;
    font-weight: 500;
    color: #fff;
    margin-left: 2rem;
    margin-bottom: 1rem;
    letter-spacing: 0.01em;
}

.form-group input:not([type="checkbox"]),
button {
    border-radius: 1.4rem;
    padding: 2.8rem 3.2rem;
    color: #586980;
    font-weight: 700;
    line-height: 24px;
    font-size: 2rem;
    border: 4px solid var(--color);
    transition: border-color 0.65s;
}

input::placeholder {
    color: transparent;
}

.form-group.checkbox {
    display: flex;
    align-items: center;
    justify-content: flex-start;
}

.form-group.checkbox label {
    margin-bottom: 0;
    margin-left: 1.6rem;
}

.form-group.checkbox input {
    width: 25px;
    height: 24px;
    border-radius: 0.4rem;
}

.form-group.checkbox input:checked {
    color: #956205;
}

.form-group input:focus-visible,
.form-group.checkbox input:focus-visible {
    outline-color: var(--color);
    box-shadow: none;
}

.form-group:has(:invalid) {
    --color: red;
}

.form-group:has(:invalid:not(:focus)) {
    animation: shake 0.65s;
}

.form-group:has(:focus) {
    --color: #fff;
}

.form-group:has(:valid) {
    --color: #16cc49;
}

.form-group:has(:placeholder-shown:not(:focus)) {
    animation: none;
}

.form-group:has(:placeholder-shown:not(:focus)) {
    animation: none;
}

/* Button */

button {
    background-color: #737373;
    color: #fff;
    cursor: not-allowed;
}

form:valid button {
    background: #16cc49;
    color: #fff;
    border: none;
    font-weight: 400;
    font-size: 2.4rem;
    cursor: pointer;
}

/* Links */

.link-action {
    margin-top: 2rem;
    display: flex;
    justify-content: space-between;
}

.link-action a {
    color: #fff;
    font-size: 2rem;
    font-weight: 500;
    letter-spacing: 0.01em;
    text-decoration: none;
}

.link-action a:hover {
    text-decoration: underline;
}

@keyframes shake {
    0%,
    100% {
        transform: translateX(0);
    }

    10%,
    30%,
    50%,
    70%,
    90% {
        transform: translateX(-4px);
    }

    20%,
    40%,
    60%,
    80% {
        transform: translateX(4px);
    }
}

@media screen and (max-width: 460px) {
    .form-group input:not(.checkbox),
    button {
        padding: 1.4rem;
    }
}
</style>
