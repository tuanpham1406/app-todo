<template>
	<div class="row">
		<!--        vì sao để data và key:
ở đây truyền item vào vì khi item thay đổi nó sẽ báo lại :data, và :data sẽ báo ngược lại
:key để xác định item nằm ở phần nào trong props ?(trong mảng items [key : value])
-->
		<app-item
				v-for="(item, index) in items"
				v-bind:data="item"
				v-bind:key="item"
        @click.native="removeItem(index)"
		>
			{{item}}
		</app-item>
	</div>
</template>

<script>
    import Items from "@/components/Items";

    export default {
        props: ['items'],
        components: {
            AppItem: Items
        },
        methods: {
            removeItem(index) {
                this.$emit('itemRemoved', index)
            }
        }
    }
</script>

<style scoped>

</style>
