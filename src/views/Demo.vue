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
            
            <template v-slot:[`item.calories`]="{ data }">
                <v-chip :color="getColor(data.calories)" dark>
                    {{ data.calories }}
                </v-chip>
            </template>
        </l-table>
    </div>
  </div>
</template>

<script>
import InputModel from '../components/input-model.vue';
import InputSync from '../components/input-sync.vue';
import InputHoc from '../components/input-hoc.vue';
import LTable from '../components/LTable/LTable';
export default {
  components: { InputModel, InputSync, InputHoc,LTable },
  data() {
    return {
      modelVal: '',
      syncVal: '',
      hocVal: '',
    };
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
