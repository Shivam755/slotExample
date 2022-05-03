<template>
    <table class="rounded text-2xl">
        <tr class="rounded bg-emerald-900 text-emerald-200" >
            <th class="border-2 border-emerald-900 px-3 py-2 rounded" v-for="header in TableData.headings" :key="header">{{header}}</th>
            <th class="border-2 border-emerald-900 px-3 py-2 rounded"> </th>
        </tr>
        <tr class="bg-emerald-200 text-emerald-900" v-for="row in TableData.data" :key="row[0]">
            <td class="border-2 border-emerald-900 px-3 py-2 rounded" v-for="dat in row" :key="dat">{{dat}}</td>
            <td class="border-2 border-emerald-900 px-3 py-2 rounded">
                <button @click.prevent="showDetails(row)" class="m-2 rounded outline-0 text-3xl bg-lime-600 text-emerald-200 p-3">
                    Show data
                </button>
            </td>
        </tr>
        <tr>
            <td>
                <slot></slot>
            </td>
        </tr>
    </table>
    
</template>

<script lang="ts">
export default {
    name:"BaseTable",
    props:{
        TableData:{
            type:Object,
            default: {
                headings:["None"],
                data:[['No data to display']]
            }
        }
    },
    methods:{
        showDetails(row){
            this.$emit('show-details', row)
        }
    }
}
</script>