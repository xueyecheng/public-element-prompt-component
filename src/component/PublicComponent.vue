<template>
    <div class="PublicComponent"></div>
</template>

<script>
export default {
    name: 'PublicComponent',
    data() {
        return {

        }
    },
    props:{
        msgConfig:Object,
        confirmConfig:Object,
        promptConfig:Object
    },
    watch: {
        msgConfig: function (val, oldVal) {
            if (val != oldVal) {
                this.showMassage(val);
            }
        },
        confirmConfig: function (val, oldVal) {
            if (val != oldVal) {
                this.showConfirmModal(val);
            }
        },
        promptConfig: function (val, oldVal) {
            if (val != oldVal) {
                this.showPromptModal(val);
            }
        }
    },
    methods: {
        showMassage(config) {
            this.$message(config);
        },
        showConfirmModal(config) {
            this.$confirm(config.message, config.title, config.options ? config.options : {}).then(config.yesCallback).catch(config.cancelCallback ? config.cancelCallback : () => { });
        },
        showPromptModal(config) {
            this.$prompt(config.message, config.title, config.options ? config.options : {}).then(config.yesCallback).catch(config.cancelCallback ? config.cancelCallback : () => { });
        }
    }
}
</script>
