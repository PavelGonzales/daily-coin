<template lang="pug">
  div
    v-data-table.elevation-1(:headers='headers',
                             :items='items',
                             :search='search',
                             :pagination.sync='pagination',
                             hide-actions='')
      template(slot='headerCell', scope='props')
        span(v-tooltip:bottom="{ 'html': props.header.text }")
          | {{ props.header.text }}
      template(slot='items', scope='props')
        td {{ props.item.date }}
        td.text-xs-right {{ props.item.day }}
        td.text-xs-right {{ props.item.fact }}
        td.text-xs-right {{ props.item.balance }}
    .text-xs-center.pt-2
      v-pagination(v-model='pagination.page', :length='pages')

</template>

<script>
  export default {
    data () {
      return {
        search: '',
        pagination: {
          rowsPerPage: 30
        },
        selected: [],
        headers: [
          {
            text: 'Дата',
            align: 'left',
            sortable: false,
            value: 'date'
          },
          { text: 'В день', value: 'day' },
          { text: 'По факту', value: 'fact' },
          { text: 'Остаток', value: 'balance' },
        ],
        items: [
          {
            value: false,
            date: 'Frozen Yogurt',
            day: 159,
            fact: 6.0,
            balance: 24,
          },
          {
            value: false,
            date: 'Ice cream sandwich',
            day: 237,
            fact: 9.0,
            balance: 37,
          },
          {
            value: false,
            date: 'Eclair',
            day: 262,
            fact: 16.0,
            balance: 23,
          },
          {
            value: false,
            date: 'Cupcake',
            day: 305,
            fact: 3.7,
            balance: 67,
          },
          {
            value: false,
            date: 'Gingerbread',
            day: 356,
            fact: 16.0,
            balance: 49,
          },
          {
            value: false,
            date: 'Jelly bean',
            day: 375,
            fact: 0.0,
            balance: 94,
          },
          {
            value: false,
            date: 'Lollipop',
            day: 392,
            fact: 0.2,
            balance: 98,
          },
          {
            value: false,
            date: 'Honeycomb',
            day: 408,
            fact: 3.2,
            balance: 87,
          },
          {
            value: false,
            date: 'Donut',
            day: 452,
            fact: 25.0,
            balance: 51,
          },
          {
            value: false,
            date: 'KitKat',
            day: 518,
            fact: 26.0,
            balance: 65,
          }
        ]
      }
    },
    computed: {
      pages () {
        return this.pagination.rowsPerPage ? Math.ceil(this.items.length / this.pagination.rowsPerPage) : 0
      }
    }
  }
</script>

<style lang="stylus">
  @import './../stylus/main'

</style>
