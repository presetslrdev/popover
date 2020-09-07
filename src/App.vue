<template>
  <div id="app">
    <div class="test-content">
      <VuePopover :offset="20"
                  placement="bottom"
      >
        <button slot="popover">Table</button>
        <table class="paleBlueRows">
          <thead>
          <tr>
            <th>head1</th>
            <th>head2</th>
            <th>head3</th>
            <th>head4</th>
          </tr>
          </thead>
          <tfoot>
          <tr>
            <td>foot1</td>
            <td>foot2</td>
            <td>foot3</td>
            <td>foot4</td>
          </tr>
          </tfoot>
          <tbody>
          <tr>
            <td>cell1_1</td>
            <td>cell2_1</td>
            <td>cell3_1</td>
            <td>cell4_1</td>
          </tr>
          <tr>
            <td>cell1_2</td>
            <td>cell2_2</td>
            <td>cell3_2</td>
            <td>cell4_2</td>
          </tr>
          <tr>
            <td>cell1_3</td>
            <td>cell2_3</td>
            <td>cell3_3</td>
            <td>cell4_3</td>
          </tr>
          </tbody>
        </table>
      </VuePopover>
      <VuePopover :offset="20"
                  placement="left"
      >
        <button slot="popover">Input</button>
        <div class="d-flex">
          <input type="text">
          <button>Submit</button>
        </div>
      </VuePopover>
    </div>
  </div>
</template>

<script>
    import VuePopover from './plugins/VuePopover/index'

    export default {
        name: 'App',
        components: {
            VuePopover
        }
    }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  .test-content {
    display: flex;
    justify-content: space-around;
  }

  .d-flex {
    display: flex;
  }

  //table
  table.paleBlueRows {
    font-family: "Times New Roman", Times, serif;
    border: 1px solid #FFFFFF;
    width: 350px;
    height: 200px;
    text-align: center;
    border-collapse: collapse;
  }

  table.paleBlueRows td, table.paleBlueRows th {
    border: 1px solid #FFFFFF;
    padding: 3px 2px;
  }

  table.paleBlueRows tbody td {
    font-size: 13px;
  }

  table.paleBlueRows tr:nth-child(even) {
    background: #D0E4F5;
  }

  table.paleBlueRows thead {
    background: #0B6FA4;
    border-bottom: 5px solid #FFFFFF;
  }

  table.paleBlueRows thead th {
    font-size: 17px;
    font-weight: bold;
    color: #FFFFFF;
    text-align: center;
    border-left: 2px solid #FFFFFF;
  }

  table.paleBlueRows thead th:first-child {
    border-left: none;
  }

  table.paleBlueRows tfoot {
    font-size: 14px;
    font-weight: bold;
    color: #333333;
    background: #D0E4F5;
    border-top: 3px solid #444444;
  }

  table.paleBlueRows tfoot td {
    font-size: 14px;
  }
</style>
