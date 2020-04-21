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
                </tr>
            </thead>
            <tbody>
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
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    name: 'master-table'
}
</script>

<style>

.headshot {
    height: auto;
    width: 50px;
    vertical-align: sub;
}

.headshot-container {
    padding: 0px;
    display: flexbox;
    justify-content: center;
}

th, td {
    text-align:center;
}

</style>