<template>
	<div class="user">
		<h2>用户管理 </h2>

		<div class="btn">
			<button>添加</button>
		</div>

		<table class="table">
			<thead>
				<tr>
					<th>编号</th>
					<th>姓名</th>
					<th>性别</th>
					<th>生日</th>
					<th>入职时间</th>
					<th>身份</th>
					<th>操作</th>
				</tr>
			</thead>
			<tbody>
				<tr>
					<td>
						<input type="checkbox">
					</td>
					<td></td>
					<td></td>
					<td></td>
					<td></td>
					<td></td>
					<td>
						<a href="javascript:void(0);">删除</a>
						<a href="javascript:void(0);">修改</a>
					</td>
				</tr>
			</tbody>
		</table>
	</div>
</template>

	<script>
		import {baseUrl} from '@/config/url'
		export default {
			data(){
				return {
					msg:'hello',
				
				}
			},
			methods:{
				loadUsers(successHandler){
					$.get(baseUrl+"/user/findAll",({status,data})=>{
						if(status == 200){
							successHandler(data);
						} else {
							alert('加载失败');
						}
					})
				}
			},
			
			beforeMount(){
				this.loadUsers((data)=>{
					console.log(data);
				});
			}
			
		}
	</script>

<style>
	.btn {
		margin: 10px 0;
	}
	.table {
		width: 90%;
		border-collapse: collapse;
	}
	.table td, .table th {
		border: 1px solid #ccc;
		line-height: 1.6em;
	}
</style>