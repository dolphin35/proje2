<template>

  <div v-if="!hidden" v-show="!hidden" style="width: calc(55vw);">

    <b-table :items="items" :fields="fields" borderless head-row-variant="transparent"
             thead-class="text-white text-center"
             tbody-tr-class="background text-white table-row text-center rounded">
      <template #cell(ping)="row">
        <i :class="['bi bi-reception-4 mr-1', parseInt(row.value) > 80 ? 'text-danger' : parseInt(row.value) > 50 ? 'text-warning' : 'text-success']"></i><span>{{
          row.value
        }}</span>
      </template>
      <template #cell(image)="row">
        <img :src="row.value" alt="">
      </template>
    </b-table>
    <b-table :items="items" :fields="fields" borderless head-row-variant="transparent"
             thead-class="text-white text-center"
             tbody-tr-class="background-red text-white table-row text-center">
      <template #cell(ping)="row">
        <i :class="['bi bi-reception-4 mr-1', parseInt(row.value) > 80 ? 'text-danger' : parseInt(row.value) > 50 ? 'text-warning' : 'text-success']"></i><span>{{
          row.value
        }}</span>
      </template>
      <template #cell(image)="row">
        <img :src="row.value" alt="">
      </template>
    </b-table>
  </div>


</template>

<script>


export default {
  name: 'App',
  created() {
    document.addEventListener('keydown', (e) => {
      e.preventDefault()
      if (e.key == 'Tab') {
        this.hidden = false
      }

    })
    document.addEventListener('keyup', (e) => {
      e.preventDefault()
      if (e.key == 'Tab') {
        this.hidden = true
      }
    })
    setInterval(() => {
      this.items[0].ping = Math.round(Math.random() * 100)
      this.items[1].ping = Math.round(Math.random() * 100)
      this.items[2].ping = Math.round(Math.random() * 100)
    }, 1000)
  },
  data() {
    return {
      fields: [
        {key: 'image', label: '', class: 'text-left'},
        {key: 'name', label: '', class: 'table-row-name'},
        {key: 'score', label: 'Score'},
        {key: 'goals', label: 'Goals'},
        {key: 'assists', label: 'Assists'},
        {key: 'saves', label: 'Saves'},
        {key: 'shots', label: 'Shots'},
        {key: 'ping', label: 'Ping'},
      ],
      items: [
        {
          image: 'http://placekitten.com/g/75/75',
          name: 'Desstann',
          score: 999,
          goals: 99,
          assists: 0,
          saves: 0,
          shots: 0,
          ping: 23
        },
        {
          image: 'http://placekitten.com/g/75/76',
          name: 'Dolphin',
          score: 999,
          goals: 99,
          assists: 0,
          saves: 0,
          shots: 0,
          ping: 81
        },
        {
          image: 'http://placekitten.com/g/75/77'
          , name: 'Aldwyn', score: 0, goals: 0, assists: 0, saves: 0, shots: 0, ping: 60
        },
      ],
      hidden: true
    }
  }
}

</script>

<style lang="scss">
body {
  cursor: none;
  background: url('https://i.pinimg.com/originals/91/26/81/91268112d9f64aeb6f8871510cf92192.png');
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  display: grid;
  place-items: center;
  height: 100vh;
}

.table-row {
  td {
    padding: 0;
    font-weight: bold;
    font-size: 18px;
    vertical-align: middle;
  }
}

.table-row-name {
  width: 200px;
  text-align: left;
}

.background {
  box-shadow: 0 0 20px 0px #0000008c;
  background: rgb(2, 0, 36);
  background: linear-gradient(0deg, rgba(2, 0, 36, 1) 0%, rgba(1, 29, 122, 1) 100%);
}

.background-red {
  box-shadow: 0 0 20px 0px #0000008c;
  background: rgb(60, 27, 10);
  background: linear-gradient(0deg, rgba(60, 27, 10, 1) 0%, rgba(118, 43, 5, 1) 100%);
}
</style>
