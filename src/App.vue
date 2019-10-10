<template>
	<div id="container">
		<app-header :item-count="items.length" :max-item="maxItem"></app-header>
		<app-new-item @itemAdded="addItem" :items="items"></app-new-item>
		<app-items-layout :items="items" @itemRemoved="removeItem"></app-items-layout>
		<div class="row mt-3">
			<div class="col-sm-12 text-center">
				<div class="alert alert-info">
					Info: click on a Item delete it!
				</div>
			</div>
		</div>
	</div>
</template>

<script>
    import ItemsLayout from "@/components/ItemsLayout";
    import NewItem from "@/components/NewItem";
    import Header from "@/components/Header";

    export default {
        name: 'app',
        components: {
            AppItemsLayout: ItemsLayout,
            AppNewItem: NewItem,
            AppHeader: Header
        },
        data: () => ({
            items: [],
            maxItem: 10
        }),
        methods: {
            addItem(item) {
                if (this.items.length >= this.maxItem) {
                    return alert('Please remove item first!')
                }
                this.items.push(item)
            },
            removeItem(index) {
                this.items.splice(index, 1)
            }
        }
    }
</script>

<style>
</style>
