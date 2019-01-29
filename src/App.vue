<template>
	<div id="app">
		<el-button @click="showComponent" type="danger" plain>删除</el-button>
		<publicComponent :msgConfig="publicComponentObj.msgConfig" :confirmConfig="publicComponentObj.confirmConfig"></publicComponent>
	</div>
</template>

<script>
import PublicComponent from './component/PublicComponent'
export default {
	name: 'app',
	data() {
		return {
			msg: 'Welcome to Your Vue.js App',
			publicComponentObj: {
				confirmConfig: {},
				msgConfig: {},
			}
		}
	},
	methods: {
		showComponent() {
			const tempObj = {
				message: `确认移出选中成员吗？`,
				title: '提示',
				options: {
					type: 'warning'
				},
				yesCallback: () => {
					const tempMsgObj = {
						message: '删除成功',
						type: 'success',
						showClose: true,
						duration: 3000
					}
					this.publicComponentObj.msgConfig = tempMsgObj;
				}
			}
			this.publicComponentObj.confirmConfig = tempObj;
		}
	},
	components: {
		PublicComponent
	}
}
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
