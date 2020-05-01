<template>
    <div id="drafted-table">
        <h1 class="vertical-center">Master List Table</h1>
        <table class="striped-table">
            <thead>
                <tr>
                    <th>Pick</th>
                    <th>Round</th>
                    <th></th>
                    <th>Name</th>
                    <th>Team</th>
                    <th>Pos.</th>
                    <th>Bye</th>
                    <th>vs. ADP</th>
                    <th>vs. RFFL ADP</th>
                    <th></th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="item in sortedItems" :key="item.rank">
                     <td>{{ item.pick }}</td>
                     <td>{{ item.round }}</td>
                     <td><img id="headshot" :src="require(`../assets/images/${item.headshot}`)" alt="yo"></td>
                     <td>{{ item.name }}</td>
                     <td>{{ item.team }}</td>
                     <td>{{ item.position }}</td>
                     <td>{{ item.bye }}</td>
                     <td>{{ item.vsAdp }}</td>
                     <td>{{ item.vsRfflAdp }}</td>
                     <td> <button>Remove</button> </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import MasterTableTest from './json/MasterTableTest.json'

export default {
    name: 'drafted-table',
    data() {
        return {
            items: MasterTableTest,
            currentSort: 'name',
            currentSortDir:'asc',
            pageSize: 10,
            currentPage: 1
        }
    },
    methods: {
        //This function looks at the table header that gets clicked to see it's current sorted direction
        sort: function(s) {
            if(s === this.currentSort) {
                this.currentSortDir = this.currentSortDir === 'asc' ? 'desc':'asc';
            }
            this.currentSort = s;
        },
        //This function loads the next items in the array onto a new page
        nextPage: function() {
            if((this.currentPage * this.pageSize) < this.items.length) this.currentPage++;
        },

        //This function goes back to previous itmes in the array.
        prevPage: function() {
            if(this.currentPage > 1) this.currentPage--;
        }
    },
    computed: {
        sortedItems:function() {
            // eslint-disable-next-line vue/no-side-effects-in-computed-properties
            return this.items.sort((a,b) => {
                let modifier = 1;
                if(this.currentSortDir === 'desc') modifier = -1;
                if(a[this.currentSort] < b[this.currentSort]) return -1 * modifier;
                if(a[this.currentSort] > b[this.currentSort]) return 1 * modifier;
                return 0;
            }).filter((row, index) => {
                let start = (this.currentPage - 1) * this.pageSize;
                let end = this.currentPage * this.pageSize;
                if(index >= start && index < end) return true;
            });
        }
    }
}
</script>

<style>

th {
    font-size: 10pt;
    white-space: nowrap;
}


</style>