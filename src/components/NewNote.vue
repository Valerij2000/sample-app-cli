<template>
    <div class="new-post">
        <!-- Form Add Note -->

					<form action="">
						<div class="mb-3">
							<label class="form-label">Title note</label>
							<input v-model="note.title"	type="text" class="form-control" placeholder="Enter title note">
						  </div>
						  <div class="mb-3">
							<label class="form-label">Subtitle note</label>
							<input v-model="note.sub"	type="text" class="form-control" placeholder="Enter subtitle note">
						  </div>
						  <div class="mb-3">
							<label class="form-label">Description note</label>
							<textarea v-model="note.descr" class="form-control" placeholder="Enter something description note" rows="3"></textarea>
						  </div>
						  <button @click="addPost()" type="button" class="btn btnPrimary w-100 mb-4 btn btn-secondary"><b>Add Post</b></button>
					</form>
    </div>
</template>

<script>
export default {
    props: {
        note: {
            type: Object,
            required: true
        }
    },
    methods: {
        addPost () {
            this.$emit('addPost', this.note)
        },
    }
}
</script>

<style lang="scss" scoped>
    button {
        margin-top: 12px;
    }
</style>