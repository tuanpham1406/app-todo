<template>
	<div class="row">
		<form>
			<div class="col-sm-8 offset-sm-2 col-md-6 offset-md-3 form-group">
				<label>U can saying...</label>
				<textarea class="form-group" v-model="item" cols="30" rows="10"></textarea>
			</div>
			<div class="col-sm-8 offset-sm-2 col-md-6 offset-md-3 form-group">
				<button class="btn btn-success" @click.prevent="createNew">Add</button>
			</div>
		</form>
	</div>
</template>

<script>
    export default {
        props: ['items'],
        data: () => ({
            item: ''
        }),
        methods: {
            createNew() {
                if (this.item === '') {
                    return false
                } else if (this.items.includes(this.item)) {
                    return alert('This item is existed in Card!')
                } else {
                    this.$emit('itemAdded', this.item)
                    this.item = ''
                }
            }
        }
    }
</script>

<style scoped>
	textarea {
		width: 100%;
		resize: none;
	}

	form {
		width: 100%;
	}
</style>
