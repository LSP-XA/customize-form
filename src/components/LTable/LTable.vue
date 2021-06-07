<script>
export default {
    name: 'LTable',
    render(h) {
        return h('div', {
            staticClass: 'l-table'
        }, [this.renderTable(h)])
    },

    data() {
        return {
            singleSelect: false,
            selected: [],
            headers: [
                {
                    text: 'Dessert (100g serving)',
                    align: 'start',
                    sortable: false,
                    value: 'name',
                },
                { text: 'Calories', value: 'calories' },
                { text: 'Fat (g)', value: 'fat' },
                { text: 'Carbs (g)', value: 'carbs' },
                { text: 'Protein (g)', value: 'protein' },
                { text: 'Iron (%)', value: 'iron' },
            ],
            desserts: [
                {
                    name: 'Frozen Yogurt',
                    calories: 159,
                    fat: 6.0,
                    carbs: 24,
                    protein: 4.0,
                    iron: '1%',
                },
                {
                    name: 'Ice cream sandwich',
                    calories: 237,
                    fat: 9.0,
                    carbs: 37,
                    protein: 4.3,
                    iron: '1%',
                },
                {
                    name: 'Eclair',
                    calories: 262,
                    fat: 16.0,
                    carbs: 23,
                    protein: 6.0,
                    iron: '7%',
                },
                {
                    name: 'Cupcake',
                    calories: 305,
                    fat: 3.7,
                    carbs: 67,
                    protein: 4.3,
                    iron: '8%',
                },
                {
                    name: 'Gingerbread',
                    calories: 356,
                    fat: 16.0,
                    carbs: 49,
                    protein: 3.9,
                    iron: '16%',
                },
                {
                    name: 'Jelly bean',
                    calories: 375,
                    fat: 0.0,
                    carbs: 94,
                    protein: 0.0,
                    iron: '0%',
                },
                {
                    name: 'Lollipop',
                    calories: 392,
                    fat: 0.2,
                    carbs: 98,
                    protein: 0,
                    iron: '2%',
                },
                {
                    name: 'Honeycomb',
                    calories: 408,
                    fat: 3.2,
                    carbs: 87,
                    protein: 6.5,
                    iron: '45%',
                },
                {
                    name: 'Donut',
                    calories: 452,
                    fat: 25.0,
                    carbs: 51,
                    protein: 4.9,
                    iron: '22%',
                },
                {
                    name: 'KitKat',
                    calories: 518,
                    fat: 26.0,
                    carbs: 65,
                    protein: 7,
                    iron: '6%',
                },
            ],
            pageOptions: {
                pageSize: 10,
                pageIndex: 1,
            },
            loading: false,
            tableHeight:500
        }
    },
    created() {},
    mounted() {
        console.log(this.$refs.table)
        console.log(document.body.offsetHeight,'body height')
        this.tableHeight = document.body.offsetHeight
        this.$refs.table.$el.addEventListener('scroll', () => {
            // let isBottom = this.$refs.table.offsetHeight + this.$refs.table.scrollTop === this.$refs.table.scrollHeight
            console.log(123123)
            // if (isBottom) {
            //     console.log(123123)
            //     this.loading = true
            // }
        })
    },
    methods: {
        getData() {
            setTimeout(() => {
                this.desserts.push(
                    {
                        name: 'Donut',
                        calories: 452,
                        fat: 25.0,
                        carbs: 51,
                        protein: 4.9,
                        iron: '22%',
                    },
                    {
                        name: 'KitKat',
                        calories: 518,
                        fat: 26.0,
                        carbs: 65,
                        protein: 7,
                        iron: '6%',
                    },
                )
            }, 1000)
        },
        renderTable(h) {
            return h('v-data-table', {
                staticClass: 'elevation-1',
                ref: 'table',
                props: {
                    headers: this.headers,
                    items: this.desserts,
                    ['single-select']: this.singleSelect,
                    ['item-key']: "name",
                    ['show-select']: true,
                    ['checkbox-color']: "success",
                    ['hide-default-footer']: true,
                    ['disable-pagination']: true,
                    height: this.tableHeight,
                    ['fixed-header']: true,
                    value: this.selected,
                },
                on: {
                    input: (e) => {
                        this.$emit('input', e)
                    },
                },
                scopedSlots: this.$scopedSlots,
            })
        },
    },
}
</script>

<style lang="less">
.l-table {
    width: 100%;
    height: calc(100% - 200px);

    overflow: auto;
    .loading {
        height: calc(100% - 20px);
    }
}
</style>
