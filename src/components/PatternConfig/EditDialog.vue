<template>
  <el-dialog style="text-align: center" title="编辑模板" :visible.sync="visible" :show-close="false"
    :before-close="cancelEdit" width="60%">
    <el-form label-width="80px" @submit.native.prevent>
      <el-form-item label="Resource">{{ target }}</el-form-item>
      <el-form-item label="pattern">
        <dynamicTags :type="'pattern'" :Taglist="rawtags" :backflag="backflag" :cancelchange="cancelEdit"
          :submitchange="editpattern" />
      </el-form-item>
    </el-form>
  </el-dialog>
</template>

<script>
import dynamicTags from "../dynamicTags";
export default {
  name: "PostDialog",
  components: { dynamicTags },
  props: {
    dialogVisible: {
      type: Boolean,
      default: () => true,
    },
    target: {
      type: String,
      default: () => "",
    },
    backflag: {
      type: Boolean,
      default: () => true
    },
    rawpattern: {
      type: String,
      default: () => "",
    },
    cancelEdit: {
      type: Function,
      default: () => {
        return () => { };
      },
    },
    editpattern: {
      type: Function,
      default: () => {
        return () => { };
      },
    },
  },
  data() {
    return {
      visible: false,
      rawtags: []
    };
  },
  watch: {
    dialogVisible(curval) {
      this.visible = curval;
    },
    rawpattern(curval) {
      this.rawtags = curval.split('+')
    }
  },
};
</script>
