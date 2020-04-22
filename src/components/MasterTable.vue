<template>
    <div id="master-table">
        <table class="striped-table">
            <thead>
                <tr>
                    <th>Rank</th>
                    <th>Pos.</th>
                    <th></th>
                    <th>Name</th>
                    <th>Team</th>
                    <th>Bye</th>
                    <th>Projection</th>
                    <th></th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="item in items" :key="item.rank">
                     <td>{{ item.rank }}</td>
                </tr>
                <tr v-for="item in items" :key="item.position">
                     <td>{{ item.position }}</td>
                </tr>
                <tr>
                    <td>1</td>
                    <td>RB</td>
                    <td class="headshot-container">
                        <img class="headshot" src="@/assets/images/christian_mccaffrey.png">
                    </td>
                    <td>Christian McCaffrey</td>
                    <td>CAR</td>
                    <td>7</td>
                    <td>336.01</td>
                    <td><button>Draft</button></td>
                </tr>
                <tr>
                    <td>2</td>
                    <td>RB</td>
                    <td class="headshot-container">
                        <img class="headshot" src="@/assets/images/saquon_barkley.png">
                    </td>
                    <td>Saquon Barkley</td>
                    <td>NYG</td>
                    <td>8</td>
                    <td>348.32</td>
                    <td><button>Draft</button></td>
                </tr>
                <tr>
                    <td>3</td>
                    <td>WR</td>
                    <td class="headshot-container">
                        <img class="headshot" src="@/assets/images/michael_thomas.png">
                    </td>
                    <td>Michael Thomas</td>
                    <td>NO</td>
                    <td>9</td>
                    <td>271.19</td>
                    <td><button>Draft</button></td>
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
    }
}


</script>

<style>

.headshot {
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