<script setup>
import { Tabs, TabsContent, TabsList, TabsTrigger } from '@/components/ui/tabs'
const loading = ref(false)
const list = [
    {
        title: 'Today',
        component: resolveComponent("TabsToday"),
    },
    {
        title: 'Week'
    },
    {
        title: 'Month'
    },
    {
        title: 'Year'
    },
]
let data = ref([
                16.0, 18.2, 23.1, 27.9, 32.2, 36.4, 39.8, 38.4, 35.5, 29.2,
                22.0, 17.8
            ])
let categories = ref({
    "today": [],
    "week": [],
    "month": [],
    "year": [],
})
let currentCategory = ref([
    'Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep',
    'Oct', 'Nov', 'Dec'
])
const chartOptions = computed(() => (
    {
        chart: {
            type: 'line',
            animation: {
                enabled: false
            }
        },
        title: {
            text: ''
        },
        xAxis: {
            categories: currentCategory
        },
        yAxis: {
            gridLineColor: 'transparent',
            title: {
                text: ''
            }
        },
        plotOptions: {
            line: {
                marker: {
                    enabled: false
                },
                dataLabels: {
                    enabled: true
                },
                enableMouseTracking: false
            }
        },
        series: [{ //data
            name: 'line',
            lineWidth: '4px',
            color: {
                linearGradient: {},
                stops: [

                    [0, 'red']
                ]
            },
            data: data.value
        }]
    }
))

function generateRandomData(number = ){
let values = []
for(let i = 0; i < number + 1; i++){
    values.push(Math.floor(Math.random() * 100))
}
console.log(values)
data.value = values
return values;
}
onMounted(() => {
    generateRandomData()
})
</script>
<template>
    <div class="grid w-full gap-4">
        <header class="flex items-start justify-between">
            <div class="grow">
                <p>Hi,welcome back Deryjon</p>
                <h1>Dashboard</h1>
            </div>
            <div class="w-[120px] h-[36px] bg-neutral-200"></div>
        </header>
        <main class="grid gap-4">
            <Tabs default-value="Today">
                <TabsList class="max-w-[400px]">
                    <TabsTrigger v-for="(item, index) in list" :key="index" :value="item.title">
                        {{ item.title }}</TabsTrigger>
                </TabsList>
                <TabsContent v-for="(item, index) in list" :key="index" :value="item.title">
                    <highchart :options="chartOptions" />
                </TabsContent>
            </Tabs>
            <!-- <div class="flex items-center gap-4">
                <div class="w-[120px] h-[36px] bg-neutral-200" v-for="(item, index) in 3" :key="index"></div>
            </div>
            <section>
                <div class="w-full h-[360px] bg-neutral-200"></div>
            </section> -->
        </main>
        <footer>
            <div class="flex items-center gap-4">
                <div class="w-full h-[260px] bg-neutral-200" v-for="(item, index) in 3" :key="index"></div>
            </div>
        </footer>
    </div>
</template>