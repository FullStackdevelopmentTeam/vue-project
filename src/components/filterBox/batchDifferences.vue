<template>
    <div class="batch-Differences">
      <template>
        <el-dialog title="批量差异对帐" :visible.sync="dialogFromDifferences" :before-close="dialog_close">
          <el-form :model="form">

            <el-form-item label="单据类型" :label-width="formLabelWidth">
              <el-select size="small" v-model="form.documentsType" placeholder="请选择活动区域">
                <el-option label="平台订单" value="shanghai"></el-option>
                <el-option label="手工订单" value="beijing"></el-option>
              </el-select>
            </el-form-item>

            <el-form-item label="业务日期" :label-width="formLabelWidth">
              <div class="block">
                <el-date-picker
                  size="small"
                  v-model="form.time"
                  type="datetimerange"
                  start-placeholder="开始日期"
                  end-placeholder="结束日期"
                  :default-time="['12:00:00']">
                </el-date-picker>
              </div>
            </el-form-item>

            <el-form-item label="平台" :label-width="formLabelWidth">
              <el-select size="small" v-model="form.platform" placeholder="请选择活动区域">
                <el-option label="区域一" value="shanghai"></el-option>
                <el-option label="区域二" value="beijing"></el-option>
              </el-select>
            </el-form-item>

            <el-form-item label="单据状态" :label-width="formLabelWidth">
              <el-select size="small" v-model="form.documentsState" placeholder="请选择活动区域">
                <el-option label="区域一" value="shanghai"></el-option>
                <el-option label="区域二" value="beijing"></el-option>
              </el-select>
            </el-form-item>

            <el-form-item label="对账状态" :label-width="formLabelWidth">
              <el-select size="small" v-model="form.checkState" placeholder="请选择活动区域">
                <el-option label="保存" value="shanghai"></el-option>
                <el-option label="区域二" value="beijing"></el-option>
              </el-select>
            </el-form-item>

            <el-form-item label="差异对帐原因" :label-width="formLabelWidth">
              <el-input size="small" v-model="form.remarks" placeholder="请输入差异对帐原因"></el-input>
            </el-form-item>
          </el-form>
          <div slot="footer" class="dialog-footer">
            <el-button size="mini" @click="cancel">取 消</el-button>
            <el-button size="mini" type="primary" @click="dialogFormVisible = false">确 定</el-button>
          </div>
        </el-dialog>
      </template>
    </div>
</template>

<script>
  import {mapState} from 'vuex'
    export default {
        name: 'batchDifferences',
        data () {
            return {
              form: {
                documentsType: '',//单据类型
                time: '',//时间
                platform: '',//平台
                documentsState: '',//单据状态
                checkState: '', //对账状态
                remarks: '',//差异对帐原因
              },
              formLabelWidth: '120px'
            }
        },
      computed:{
          ...mapState({
            dialogFromDifferences:state=>state.dialogFromDifferences
          })
        },
      methods:{
        cancel(){
          this.$store.dispatch('dialogFromDifferences')
        },
        dialog_close(){
          this.$store.dispatch('dialogFromDifferences')
        }
      }
    }
</script>
<style scoped>

</style>
