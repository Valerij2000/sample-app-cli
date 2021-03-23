<template>
  <div class="wrapper">
    <div class="wrapper-content">

      <!-- Heder setion -->
  <section class="header-section">
		<header class="bd-header bg-dark py-2	  d-flex align-items-stretch border-bottom border-dark">
			<h6 style="color: grey; margin-left: 20px;">Valeij Shumkov</h6>
		  </header>
	</section>

  <!-- Main Content -->

	<section class="main-section" style="padding-top: 20px; padding-bottom: 40px;">
		<div class="container">
			<div class="row">
				<div class="col-xl-8 offset-xl-2">
					<h1 class="text-center" style="margin-bottom: 20px; font-size: 25px">Notes Application</h1>





  <Message 
  
  v-if="message" 
  :message="message" 
  
  />

	<NewNote 
	:note="note"
	@addPost="addPost"
	/>

<!-- Search -->


	<Search :value="search" placeholder="Find you are post" @search="search = $event"/>


					<Notes 
						:notes="notesFilter"
						@remove="removePost"
					/>


					

				</div>
			</div>
		</div>
	</section>
    </div>
  </div>
</template>

<script>

// Импортируем созданный нами компонент в родителький объект:
import Message from '@/components/Message.vue'
import NewNote from '@/components/NewNote.vue'
import Notes from '@/components/Notes.vue'
import Search from '@/components/Search.vue'



export default {

  data() {
    return {
	  search: '',
      message: null,
			note: {
				title: '',
				descr: '',
				sub: '',
			},
			notes: [
				{
					title: 'Java Script',
					sub: 'Programming and Math',
					descr: 'Here we learn JavaScript, starting from scratch and go on to advanced concepts like OOP.',
					date: new Date(Date.now()).toLocaleString()
				},

				{
					title: 'Java ',
					sub: 'Algoritms',
					descr: 'Java is a class-based, object-oriented programming language that is designed to have as few implementation dependencies as possible.',
					date: new Date(Date.now()).toLocaleString()
				},

				{
					title: 'PHP',
					sub: 'Oracle and Server Dev',
					descr: 'lorem PHP is server lang.',
					date: new Date(Date.now()).toLocaleString()
				},

				{
					title: 'Python',
					sub: 'Backend development',
					descr: 'The core of extensible programming is defining functions. Python allows mandatory and optional arguments, keyword arguments, and even arbitrary argument lists...',
					date: new Date(Date.now()).toLocaleString()
				},

			],
    };
  },

  created() {},

  mounted() {},

  methods: {

	  
    addPost () {

				if(this.note.title === '' || this.note.descr === '' || this.note.sub === '') {
					this.message = 'Сan not be blank!';
					return false;
				}

				this.notes.push({
					title: this.note.title,
					descr: this.note.descr,
					sub: this.note.sub,
					date: new Date(Date.now()).toLocaleString(),
				})


				this.note.title = '';
				this.note.sub = '';
				this.note.descr = '';
				this.message = '';


			},

			removePost (index) {
				this.notes.splice(index, 1);
			},
  },

  computed: {
	  notesFilter () {
		  let arr = this.notes,
		  	search = this.search
				if (!search) return arr;
				// Small
			search = search.trim().toLowerCase();
			// Filter
			arr = arr.filter(function (item) {
				if (item.title.toLowerCase().indexOf(search) !== -1) {
					return item;
				}
			})
			// Error
			return arr;
	  },
  },

  components: {
    // Регистрируем созданный компонент TodoList:
    Message, NewNote, Notes, Search
    
  },
};
</script>

<style>
</style>
