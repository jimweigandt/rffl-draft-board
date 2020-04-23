<template>
    <div id="master-table">
        <HeadshotPictures />
        
        <!-- <div v-for="item in items" :key="item.headshot">
            <img :src="require(`../assets/images/${item.headshot}`)" alt="yo">
        </div> -->


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