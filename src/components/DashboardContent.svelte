<script>
    import BarChart from '../components/BarChart.svelte';
	import AreaChart from '../components/AreaChart.svelte';
	import LineChart from '../components/LineChart.svelte';
	import NavBar from './NavBar.svelte';
	import Icon from '@iconify/svelte';


    const Cards = [
        {
            icon: "gala:chart",
            numbers: "1k",
            title: "Total sales",
            profit: "+8"
        },
        {
            icon: "icon-park-outline:transaction-order",
            numbers: "300",
            title: "Total order",
            profit: "+5"
        },
        {
            icon: "ant-design:tag-filled",
            numbers: "5",
            title: "product sold",
            profit: "+1.2"
        },
        {
            icon: "bxs:user-plus",
            numbers: "8",
            title: "new customers",
            profit: "0.5"
        },
    ]
</script>

<style></style>

<div class="bg-secondary w-full h-[100vh] overflow-y-auto relative">
    <NavBar />
    <div class="w-[95%] mx-auto rounded-xl flex flex-col mb-10 gap-5">
        <div class="flex justify-between align-middle w-full h-auto gap-5">
            <div class="w-full h-auto bg-white rounded-xl p-5 flex flex-col justify-between">
                <div class="flex justify-between align-middle mb-10">
                    <div class="flex flex-col">
                        <h1 class="font-bold mb-1"> Today's Sales </h1>
                        <p class="text-sm">Sales Summary</p>
                    </div>
                    <button class="border border-[#C3D3E2] px-3 py-1 rounded-lg flex justify-center align-middle h-8">
                        <Icon icon="bx:export" class="text-[#0F3659] text-xl mr-2 font-black"/>
                        <p class="text-[#0F3659] text-center text-sm font-medium">Export</p>
                    </button>
                </div>

                <div class="flex justify-between align-middle gap-3">
                    {#each Cards as card, index}
                        <div key={index} 
                        class={`
                        ${card.numbers == "1k" && "bg-[#FFE2E5]"} 
                        ${card.numbers == "300" && "bg-[#FFF4DE]"} 
                        ${card.numbers == "5" && "bg-[#DCFCE7]"} 
                        ${card.numbers == "8" && "bg-[#F3E8FF]"} 
                        px-3 py-6 flex flex-col justify-center align-middle w-1/4 h-auto rounded-xl`}>
                            <div 
                                class={`w-8 h-auto rounded-[50%] p-2 mb-2 
                                ${card.numbers == "1k" && "bg-[#FA5A7D]"} 
                                ${card.numbers == "300" && "bg-[#FF947A]"} 
                                ${card.numbers == "5" && "bg-[#3CD856]"} 
                                ${card.numbers == "8" && "bg-[#BF83FF]"} 
                            `}>
                                <Icon icon={card.icon} class="text-white text-base"/>
                            </div>
                            <h3 class="font-bold mb-2"> {card.numbers} </h3>
                            <h2 class="capitalize mb-2 text-xs"> {card.title} </h2>
                            <p class="text-[#4079ED] text-[10px]">{card.profit}% from yesterday</p>
                        </div>
                    {/each}
                </div>
            </div>
            <div class="w-3/5 h-auto bg-white rounded-xl p-5 flex flex-col justify-between">
                <h1 class="font-bold mb-5"> Visitor Insights </h1>
                <img src="/chart.svg" alt="chart" class="w-full h-auto">
            </div>
        </div>
        <div class="flex flex-col w-full h-auto gap-5">
            <div class="flex justify-between align-middle gap-5 w-auto h-auto">
                <div class="bg-white w-[45%] rounded-xl p-5 h-[200] flex flex-col">
                    <h1 class="font-bold mb-5"> Top Revenue </h1>
                    <BarChart />
                </div>
                <div class="flex justify-between align-middle gap-5 w-[55%] h-auto">
                    <div class="bg-white w-1/2 rounded-xl p-5 h-[200] flex flex-col">
                        <h1 class="font-bold mb-5"> Customer Satisfaction </h1>
                        <AreaChart />
                    </div>
                    <div class="bg-white w-1/2 rounded-xl p-5 h-[200] flex flex-col">
                        <h1 class="font-bold mb-5"> Target vs Reality </h1>
                        <LineChart />
                    </div>
                </div>
            </div>
            <div class="flex justify-between align-middle gap-5 h-72 w-full">
                <div class="bg-white w-[45%] rounded-xl h-full p-5 flex flex-col">
                    <h1 class="font-bold mb-5"> Top Products </h1>
                    <img src="/chart-4.svg" alt="chart" class="w-full h-auto">
                </div>
                <div class="flex justify-between align-middle gap-5 w-[55%] h-full">
                    <div class="bg-white w-1/2 rounded-xl p-5 h-full flex flex-col">
                        <h1 class="font-bold mb-16"> Sales Mapping by Country </h1>
                        <img src="/chart-5.svg" alt="chart" class="w-full h-auto">
                    </div>
                    <div class="bg-white w-1/2 rounded-xl p-5 h-full justify-between flex flex-col">
                        <h1 class="font-bold mb-5"> Volume vs Service Level </h1>
                        <img src="/chart-6.svg" alt="chart" class="w-full h-auto">
                    </div>
                </div>
            </div>
        </div>              
    </div>
</div>