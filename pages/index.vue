<template>
    <div class="flex flex-col h-screen w-screen justify-center items-center">

        <BaseTable @show-details="show" :TableData="tableData">
            <button @click="clear" class="m-2 rounded outline-0 text-3xl bg-lime-600 text-emerald-200 p-3">
                Clear
            </button>
        </BaseTable>

        <div class="text-3xl text-emerald-900" v-if="displayData != ''">
            <h1>Details:</h1>
            <p><b>Roll no:</b> {{displayData[0]}} </p>
            <p><b>Name:</b> {{displayData[1]}} </p>
            <p><b>Std:</b> {{displayData[2]}} </p>
        </div>
    </div>
</template>

<script lang="ts">
import BaseTable from "@/components/baseTable.vue"
export default {
    name:'Index',
    components:{
        BaseTable
    },
    data(){
        return{
            tableData:{
                headings:["Roll no", "Name", "Std"],
                data:[
                    ["4503", "Rhea Menon", "SYBsc"],
                    ["4517", "Shivam Gupta", "SYBSc"],
                    ["4516", "Harshal Gondkar", "SYBSc"],
                    ["4515", "Jyoti Ghosh", "SYBSc"],
                    ["4514", "Tejas Pophale", "SYBSc"],
                ]
            },
            displayData:''
        }
    },
    methods:{
        show(e){
            this.displayData=e
            console.log(this.displayData)
        },
        clear(){
            this.displayData=''
        }
    }
}
</script>