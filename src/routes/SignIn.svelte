<script>
    import FaHome from 'svelte-icons/fa/FaHome.svelte';
    import FaFacebook from 'svelte-icons/fa/FaFacebook.svelte';
    import FaApple from 'svelte-icons/fa/FaApple.svelte';
    import FaBars from 'svelte-icons/fa/FaBars.svelte';
    import Icon from '@iconify/svelte';
    import { goto } from '$app/navigation';
    let showPassword = false;
    let rememberMe = false;
    let isLoading = false;
    let name = '';
    let password = '';

    const handlePasswordInput = (event) => {
        password = event.target.value;
    }

    const togglePasswordVisibility = () => {
        showPassword = !showPassword;
    }

    const handleRememberMeChange = () => {
        rememberMe = !rememberMe;
    }

    const handleSignIn = (event) => {
        event.preventDefault();

        isLoading = true;
        const user = { name, password };
        localStorage.setItem('user', JSON.stringify({ name: user.name }));
        setTimeout(() => {
            isLoading = false;
            goto('/dashboard')
        }, 7000);
    }
</script>


<style lang="postcss"></style>

<div class="flex flex-col align-middle w-full h-auto md:h-[100vh] px-5 md:px-20 py-5 md:py-10">
        
    <nav class="justify-end align-middle w-full hidden md:flex lg:flex">
        <ul class="flex justify-between align-middle w-1/2">
            <li> <a href="/"> <p>Help</p> </a></li>
            <li> <a href="/"> <p>Contact us</p> </a> </li>
            <li>
                <select name="lang" id="lang" form="" class="border-0 outline-none">
                    <option value="english"><p>English</p></option>
                    <option value="french"><p>French</p></option>
                    <option value="portugese"><p>Portugese</p></option>
                    <option value="spanish"><p>Spanish</p></option>
                </select>
            </li>
            <li> <a href="/"> <p>Sign up</p> </a> </li>
            <li><div class="w-5 h-5"> <a href="/"> <FaHome /> </a> </div></li>
        </ul>
    </nav>

    <div class="flex md:hidden lg:hidden justify-end align-middle">
        <div class="w-5 h-auto text-primary"> <FaBars /> </div>
    </div>

    <div class="flex flex-col-reverse md:flex-row justify-center align-middle py-5 md:pt-28">
        <div class="flex flex-col flex-1 h-[50vh] align-middle justify-center px-0 md:px-20">
            <h1 class="font-bold uppercase text-lg md:text-2xl">Welcome back!</h1>
            <p class="mb-10">Don't have an account, <a href="/" class="text-primary">Sign up</a></p>
            <form>
                <div class="mb-5">
                    <h3 class="mb-2">Username</h3>
                    <input type="text" required bind:value={name} placeholder="cascadingGeek" class={`w-full h-auto border text-primary outline-none rounded-2xl px-3 py-1 ${name === '' ? "border-red" : "border-primary"}`}/>
                </div>
                <div class="mb-5">
                    <h3 class="mb-2">Password</h3>
                    <div class="w-auto h-auto relative">
                        <input type={showPassword ? "text" : "password"} required value={password} on:input={handlePasswordInput} placeholder="password" class={`w-full h-auto border rounded-2xl px-3 py-1 text-primary outline-none ${password === '' ? "border-red" : "border-primary"}`} />
                        <button class="absolute right-5 top-[7px]" on:click={togglePasswordVisibility}>
                            <Icon icon={showPassword ? "teenyicons:eye-outline" : "formkit:eyeclosed"}  class="text-primary text-xl "/>
                        </button>
                        
                    </div>
                </div>
            
                <div class="flex justify-between align-middle mb-5">
                    <div class="flex ">
                        <input type="radio" bind:group={rememberMe} on:change={handleRememberMeChange} class="mr-5" id="rememberMeCheckbox">
                        <p>Remember me</p>
                    </div>
                    <a href="/"> Forgot password? </a>
                </div>
                <button type="submit" class={`w-full h-auto rounded-2xl px-3 py-1 mb-5 ${name === '' || password === '' ? "bg-secondary text-primary" : "bg-primary text-white"}`} disabled={name === '' || password === ''} on:click={handleSignIn}>Sign in</button>
            </form>
            <div class="w-full h-auto">
                <div class="flex justify-center align-middle mb-5">
                    <div class="flex justify-between text-center align-middle w-[70%] md:w-1/2">
                        <span class="w-1/6 bg-primary h-[2px] my-auto"></span>
                        <p class="text-center mt-auto">or continue with</p>
                        <span class="w-1/6 bg-primary h-[2px] my-auto"></span>
                    </div>
                </div>
                <div class="flex justify-center align-middle">
                    <div class="flex justify-between align-middle w-[70%] md:w-1/2">
                        <button class="border rounded-lg border-primary w-auto h-auto px-5 py-2 flex justify-center align-middle">
                            <img src="https://image.similarpng.com/very-thumbnail/2020/12/Illustration-of-Google-icon-on-transparent-background-PNG.png" alt="Google account" class="w-5 h-5">
                        </button>
                        <button class="border rounded-lg border-primary w-auto h-auto px-5 py-2 flex justify-center align-middle">
                            <div class="w-5 h-5 text-primary"> <FaFacebook /> </div>
                        </button>
                        <button class="border rounded-lg border-primary w-auto h-auto px-5 py-2 flex justify-center align-middle">
                            <div class="w-5 h-5"> <FaApple /> </div>
                        </button>
                    </div>
                </div>
            </div>
            {#if isLoading}
                {#key isLoading}
                    <div class="fixed top-0 left-0 w-screen h-screen bg-opacity-70  bg-primary z-50 flex flex-col justify-center items-center">
                        <img src="https://cdn.pixabay.com/animation/2022/07/29/03/42/03-42-18-223_512.gif" alt="loader" class="w-20 h-auto">
                    </div>
                {/key}
            {/if}
        </div>
        <div class="flex flex-col flex-1 h-[50vh]">
            <img src="/form_image.svg" alt="Form_img" class="w-auto h-auto"/>
        </div>
    </div>
</div>