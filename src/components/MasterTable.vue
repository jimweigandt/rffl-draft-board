<template>
    <div id="master-table">
        <h1 class="vertical-center">Master List Table</h1>
        <table class="striped-table">
            <thead>
                <tr>
                    <th class="th-true" @click="sort('rank')">Rank</th>
                    <th class="th-true" @click="sort('position')">Pos.</th>
                    <th class="th-true" @click="sort('positionRank')">Pos. Rk.</th>
                    <th></th>
                    <th class="th-true" @click="sort('player')">Name</th>
                    <th class="th-true" @click="sort('team')">Team</th>
                    <th class="th-true" @click="sort('bye')">Bye</th>
                    <th class="th-true" @click="sort('projection')">Projection</th>
                    <th class="th-true" @click="sort('projPpg')">Proj. PPG</th>
                    <th></th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="item in sortedItems" :key="item.rank">
                     <td>{{ item.rank }}</td>
                     <td>{{ item.position }}</td>
                     <td>{{ item.positionRank }}</td>
                     <td><img id="headshot" :src="require(`../assets/images/${item.headshot}`)" alt="yo"></td>
                     <td>{{ item.player }}</td>
                     <td>{{ item.team }}</td>
                     <td>{{ item.bye }}</td>
                     <td>{{ item.projection }}</td>
                     <td>{{ item.projPpg }}</td>
                     <td> <button>Draft</button> </td>
                </tr>
            </tbody>
        </table>
        <p class="vertical-center">
            <button class="page-buttons" @click="prevPage">Previous</button>
            <button class="page-buttons" @click="nextPage">Next</button>
        </p>
    </div>
</template>

<script>
import MasterTableTest from './json/MasterTableTest.json'

export default {
    name: 'master-table',
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

#headshot {
    height: auto;
    width: 75px;
    vertical-align: sub;
}

.headshot-container {
    padding: 0;
    display: flexbox;
    justify-content: center;
}

th, td {
    text-align:center;
}

.th-true:hover {
    background-color: #f7f7f7;
}

.page-buttons {
    margin: 0 50px 0 50px;
}

button {
    vertical-align: sub;
}

</style>