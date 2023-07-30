<script>

    import Icon from '@iconify/svelte';

    const SideBarContents = [
        {
            icon: "ant-design:pie-chart-filled",
            text: "Dashboard",
            link: "/dashboard",
        },
        {
            icon: "humbleicons:chart",
            text: "Leaderboard",
            link: "/inprogress",
        },
        {
            icon: "mdi:cart-outline",
            text: "Order",
            link: "/inprogress",
        },
        {
            icon: "teenyicons:bag-outline",
            text: "Products",
            link: "/inprogress",
        },
        {
            icon: "ph:chart-line",
            text: "Sales Report",
            link: "/inprogress",
        },
        {
            icon: "quill:chat",
            text: "Messages",
            link: "/inprogress",
        },
        {
            icon: "material-symbols:settings",
            text: "Settings",
            link: "/inprogress",
        },
        {
            icon: "humbleicons:logout",
            text: "Sign Out",
            link: "/",
        },
    ]

    let activeIndex = 0;

    const handleBg = (index) => {
        activeIndex = index;
    }

</script>

<style lang="postcss"></style>

<div class="w-1/6 h-[100vh] p-5 bg-white hidden md:block lg:block">
    <div class="mb-10 w-full h-6">
        <a href="/">
            <img src="/logo.svg" alt="logo" class="h-full w-3/4 mx-auto">
        </a>
    </div>
    <div class="mb-10">
        {#each SideBarContents as sideBarContent, index}
            <a href={sideBarContent.link} key={index}>
                <div class={`w-full rounded-xl mb-2 hover:bg-secondary text-[#737791] ${index === activeIndex ? "bg-primary text-white" : ""}`} on:click={() => handleBg(index)}>
                    <div class="w-auto mx-auto flex justify-start align-middle px-3 py-[10px]">
                        <Icon icon={sideBarContent.icon} class="text-lg mr-2"/>
                        <h3 class="text-xs"> {sideBarContent.text} </h3>
                    </div>
                </div>
            </a>
        {/each}
    </div>
    <div class="w-full h-auto bg-primary rounded-xl px-3 py-5 flex flex-col justify-center align-middle">
        <div class="mb-5 w-full h-4">
            <img src="/logo.svg" alt="logo" class="h-full w-3/4 mx-auto">
        </div>
        <p class="mb-5 text-xs text-center text-white">Get access to all features on Brisheam</p>
        <button class="text-primary text-xs bg-white rounded-lg px-3 py-2 mx-auto"> Get Pro </button>
    </div>
</div>