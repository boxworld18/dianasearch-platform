<template>
  <el-dialog style="text-align: center" title="上传模板" :visible.sync="visible" :show-close="false"
    :before-close="cancelPost" width="60%">
    <el-form label-width="80px" @submit.native.prevent>
      <el-form-item label="Resource">{{ target }}</el-form-item>
      <el-form-item label="Pattern">
        <el-input type="text" placeholder="不同模板用&隔开" v-model="rawpattern" style="margin-left: 10px;width:60%"></el-input>
      </el-form-item>
    </el-form>
    <span slot="footer" class="dialog-footer">
      <el-button v-on:click="cancelPost()">取 消</el-button>
      <el-button type="primary" :disabled="rawpattern === ''" v-on:click="postpattern(rawpattern.split('&'))">确 定
      </el-button>
    </span>
  </el-dialog>
</template>

<script>
export default {
  name: "PostDialog",
  props: {
    dialogVisible: {
      type: Boolean,
      default: () => true,
    },
    target: {
      type: String,
      default: () => "",
    },
    cancelPost: {
      type: Function,
      default: () => { },
    },
    postpattern: {
      type: Function,
      default: () => { },
    },
  },
  data() {
    return {
      visible: false,
      rawpattern: "",
    };
  },
  watch: {
    dialogVisible(curval) {
      this.visible = curval;
      this.rawpattern = ""
    },
  },
};
</script>