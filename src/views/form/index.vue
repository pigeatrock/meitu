<template>
  <div class="app-container">
    <el-form ref="form" :model="form" label-width="120px">
      <h3>客户信息</h3>
      <el-form-item label="客户姓名：">
        <el-input v-model="form.name"/>
      </el-form-item>
      <el-form-item label="手机号码：">
        <el-input v-model="form.phone"/>
      </el-form-item>
      <el-form-item label="客户类型：">
        <el-select v-model="form.customer_type" placeholder="选择客户类型">
          <el-option label="个人用户" value="0"/>
          <el-option label="经销商" value="1"/>
        </el-select>
      </el-form-item>
      <el-form-item label="服务类型：">
        <el-select v-model="form.service_type" placeholder="选择服务类型">
          <el-option label="保内" value="0"/>
          <el-option label="保外" value="1"/>
          <el-option label="检测" value="2"/>
          <el-option label="换机" value="3"/>
        </el-select>
      </el-form-item>
      <el-form-item label="故障描述：">
        <el-input v-model="form.fault_info"/>
      </el-form-item>
      <h3>货品信息</h3>
      <el-form-item label="手机型号：">
        <el-select v-model="form.phone_version" placeholder="选择手机型号">
          <el-option label="m6" value="0"/>
          <el-option label="m6s" value="1"/>
          <el-option label="m8" value="2"/>
          <el-option label="m8t" value="3"/>
          <el-option label="m8s" value="4"/>
          <el-option label="t8" value="5"/>
          <el-option label="t8s" value="6"/>
          <el-option label="v6" value="7"/>
          <el-option label="t9" value="8"/>
          <el-option label="t9特别版" value="9"/>
          <el-option label="v7" value="10"/>
        </el-select>
      </el-form-item>
      <el-form-item label="手机颜色：">
          <el-input v-model="form.phone_color"/>
      </el-form-item>
      <el-form-item label="imei1：">
          <el-input v-model="form.imei1"/>
      </el-form-item>
      <el-form-item label="imei2：">
          <el-input v-model="form.imei2"/>
      </el-form-item>
      <el-form-item label="维修结果：">
        <el-select v-model="form.repair_result" placeholder="选择维修结果">
          <el-option label="已修复" value="0"/>
          <el-option label="未修复" value="1"/>
          <el-option label="拒修退回" value="2"/>
          <el-option label="无故障退回" value="3"/>
        </el-select>
      </el-form-item>
      <h3>处理信息</h3>
      <el-form-item label="检测结果：">
        <el-select v-model="form.check_result" placeholder="选择检测结果">
          <el-option label="故障属实" value="0"/>
          <el-option label="无故障" value="1"/>
        </el-select>
      </el-form-item>
      <el-form-item label="实际故障：">
          <el-input v-model="form.actual_fault"/>
      </el-form-item>
      <el-form-item label="故障代码：">
          <el-select v-model="fault_code" filterable>
          </el-select>
      </el-form-item>
      <el-form-item label="更换物料：">
          <el-select v-model="materiel" filterable>
          </el-select>
      </el-form-item>
       <el-form-item label="新imei1：">
          <el-input v-model="form.new_imei1"/>
      </el-form-item>
       <el-form-item label="新imei2：">
          <el-input v-model="form.new_imei2"/>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit">保存</el-button>
        <el-button @click="onCancel">取消</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        //客户信息
        name: "",
        phone: "",
        customer_type: "0", //客户类型，默认个人
        service_type: "0", //服务类型，默认保内
        fault_info: "", //故障描述
        //货品信息
        phone_version: "",
        phone_color: "",
        imei1: null,
        imei2: null,
        repair_result: "0",
        //处理信息
        check_result: "0",
        actual_fault: "",
        fault_code: "",
        materiel: "",
        new_imei1: "",
        new_imei2: ""
      }
    };
  },
  methods: {
    onSubmit() {
      this.$message("保存!");

      this.axios.get("/save", {
        params: {
          name: this.form.name,
          phone: this.form.phone,
          customer_type: this.form.customer_type,
          service_type: this.form.service_type,
          fault_info: this.form.fault_info,
          phone_version: this.form.phone_version,
          phone_color: this.form.phone_color,
          imei1: this.form.imei1,
          imei2: this.form.imei2,
          repair_result: this.form.repair_result,
          check_result: this.form.check_result,
          actual_fault: this.form.actual_fault,
          materiel: this.form.materiel,
          new_imei1: this.form.new_imei1,
          new_imei2: this.form.new_imei2
        }
      });
    },
    onCancel() {
      this.$message({
        message: "取消!",
        type: "warning"
      });
    }
  }
};
</script>

<style scoped>
</style>

