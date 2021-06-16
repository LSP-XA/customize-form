<template>
  <div>
    <div class="demo-item">
      <label>v-model: </label><input-model v-model="modelVal" />
    </div>
    <div class="demo-item">
      <label>sync: </label><input-sync :value.sync="syncVal" />
    </div>
    <div class="demo-item">
      <label>switch hoc comp: </label>
      <el-switch
        v-model="hocType"
        active-value="input"
        inactive-value="checkbox"
        active-text="input"
        inactive-text="checkbox"
      />
      <span style="margin-left: 20px">value:{{hocVal}}</span>
    </div>
    <div class="demo-item">
      <label>hoc: </label>
      <input-hoc :type="hocType" v-model="hocVal">
        <template v-slot:suffix>
          <i class="el-input__icon el-icon-date"></i>
        </template>
      </input-hoc>
    </div>
  </div>
</template>

<script>
import 'element-ui/lib/theme-chalk/switch.css';
import ElSwitch from 'element-ui/lib/switch';
import InputModel from '../components/input-model.vue';
import InputSync from '../components/input-sync.vue';
import InputHoc from '../components/input-hoc.vue';

export default {
  components: { InputModel, InputSync, InputHoc, ElSwitch },
  data() {
    return {
      modelVal: '',
      syncVal: '',
      hocVal: '',
      hocType: 'input',
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
