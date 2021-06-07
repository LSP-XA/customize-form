<template>
  <div>
    <div class="demo-item">
      <label>v-model: </label><input-model v-model="modelVal" />
    </div>
    <div class="demo-item">
      <label>sync: </label><input-sync :value.sync="syncVal" />
    </div>
    <div class="demo-item">
      <label>hoc: </label>
      <input-hoc v-model="hocVal">
        <template v-slot:suffix>
          <i class="el-input__icon el-icon-date"></i>
        </template>
      </input-hoc>
        <l-table>
          <template v-slot:[`item.calories`]="{ item }">
              <v-chip :color="getColor(item.calories)" dark>
                  {{ item.calories }}
              </v-chip>
          </template>
        </l-table>
              <v-chip color="red">
                  demo
              </v-chip>
    </div>
  </div>
</template>

<script>
import InputModel from '../components/input-model.vue';
import InputSync from '../components/input-sync.vue';
import InputHoc from '../components/input-hoc.vue';
import LTable from '../components/LTable/LTable.vue';

export default {
  components: { InputModel, InputSync, InputHoc, LTable },
  data() {
    return {
      modelVal: '',
      syncVal: '',
      hocVal: '',
    };
  },
  methods: {
    getColor (calories) {
      if (calories > 400) return 'red'
      else if (calories > 200) return 'orange'
      else return 'green'
    },
  },
};
</script>

<style lang="less">
.demo-item{
  display: flex;
  align-items: center;
  label{
    width: 100px;
  }
}
</style>
