<script>
    import Icon from '@iconify/svelte';
    import FaBars from 'svelte-icons/fa/FaBars.svelte';

    const user = JSON.parse(localStorage.getItem('user')) || {};

</script>

<style></style>

<nav class="w-full h-auto flex items-center justify-between bg-white py-5 px-5 mb-10 sticky z-50 top-0 left-0">
    <h1 class="text-lg md:text-2xl font-bold">Dashboard</h1>
    <div class="flex justify-between align-middle w-auto">
        <div class="w-2/3 rounded-xl px-4 py-1 relative bg-secondary hidden md:flex mr-5">
            <button> <Icon icon="zondicons:search" class="text-primary mr-1 text-lg"/> </button>
            <input type="search" name="" id="" placeholder="Search here..." class="w-full h-auto py-1 px-2 bg-transparent outline-none">
        </div>
        <select name="lang" id="lang" form="" class="border-0 outline-none mr-5 md:mr-16">
            <option value="english"><p>English</p></option>
            <option value="french"><p>French</p></option>
            <option value="portugese"><p>Portugese</p></option>
            <option value="spanish"><p>Spanish</p></option>
        </select>
        <button class="bg-[#FFFAF1] w-12 h-auto rounded-lg px-3 py-1 mr-10 relative before:absolute before:w-[5px] before:h-[5px] before:rounded-[50%] before:bg-red before:top-2 before:right-2 hidden md:block">
            <Icon icon="mdi:bell" class="text-[#FFA412] text-lg"/>
        </button>
        <div class="hidden md:flex justify-center align-middle cursor-pointer">
            <img src="/profile.svg" alt="profile" class="rounded-lg w-10 h-auto mr-2">
            <div class="mr-10">
                <h5 class="font-semibold text-sm whitespace-normal text-ellipsis">{user.name}</h5>
                <p class="test-[8px]">Admin</p>
            </div>
            <div class="pr-5">
                <Icon icon="charm:chevron-down" class="text-[#333333] text-xl"/>
            </div>
        </div>
        <div class="flex md:hidden lg:hidden justify-end align-middle">
            <div class="w-5 h-auto text-primary"> <FaBars /> </div>
        </div>
    </div>
</nav>