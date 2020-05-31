<template>
    <div class="container">
        <a-upload-dragger
            name="file"
            :multiple="true"
            action="https://www.mocky.io/v2/5cc8019d300000980a055e76"
            @change="handleChange"
            :supportServerRender="true"
        >
            <p class="ant-upload-drag-icon">
                <a-icon type="inbox" />
            </p>
            <p class="ant-upload-text">点击或拖拽上传文件</p>
        </a-upload-dragger>
    </div>
</template>

<script>
import Vue from "vue";
import { Icon, Upload } from "ant-design-vue/lib";

Vue.use(Icon).use(Upload);

export default {
    data() {
        return {};
    },
    methods: {
        handleChange(info) {
            const status = info.file.status;
            if (status !== "uploading") {
                console.log(info.file, info.fileList);
            }
            if (status === "done") {
                this.$message.success(
                    `${info.file.name} file uploaded successfully.`
                );
            } else if (status === "error") {
                this.$message.error(`${info.file.name} file upload failed.`);
            }
        }
    }
};
</script>

<style>
.container{
  margin: 100px;
}
</style>
