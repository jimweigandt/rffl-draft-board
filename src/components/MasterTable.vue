<template>
    <div id="master-table">
        <table class="striped-table">
            <thead>
                <tr>
                    <th v-on:click="sortTable(col)">Rank</th>
                    <th>Pos.</th>
                    <th></th>
                    <th v-on:click="sortTable(col)">Name</th>
                    <th>Team</th>
                    <th>Bye</th>
                    <th>Projection</th>
                    <th></th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="item in items" :key="item.rank">
                     <td>{{ item.rank }}</td>
                     <td>{{ item.position }}</td>
                     <td><img id="headshot" :src="require(`../assets/images/${item.headshot}`)" alt="yo"></td>
                     <td>{{ item.player }}</td>
                     <td>{{ item.team }}</td>
                     <td>{{ item.bye }}</td>
                     <td>{{ item.projection }}</td>
                     <td> <button>Draft</button> </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import MasterTableTest from './json/MasterTableTest.json'

export default {
    name: 'master-table',
    data() {
        return {
            items: MasterTableTest
        }
    },
    methods: {
        "sortTable": function sortTable(col) {
            this.rows.sort(function(a, b) {
                if (a[col] > b[col]) {
                    return 1;
                } else if (a[col] < b[col]) {
                    return -1;
                }
                return 0;
            })
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

button {
    vertical-align: sub;
}

</style>