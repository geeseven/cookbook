<template>
    <li :class="{ 'header': isHeader() }" @click="toggleDone">
    	<div class="checkmark" :class="{ 'done': isDone }">✔</div>
    	{{ displayIngredient }}
	</li>
</template>

<script>
export default {
    name: 'RecipeIngredient',
    props: ['ingredient'],
    data () {
        return {
            headerPrefix: "## ",
            isDone: false,
        }
    },
    computed: {
        displayIngredient: function() {
            if (this.isHeader()) {
                return this.ingredient.substring(this.headerPrefix.length)
            }
            return this.ingredient
        },
    },
    methods: {
        isHeader: function() {
            if (this.ingredient.startsWith(this.headerPrefix)) {
                return true
            }
            return false
        },
        toggleDone: function() {
        	this.isDone = !this.isDone
        }
    }

}
</script>

<style scoped>

li {
    margin-left: 1.25em;
}
    li.header {
        position: relative;
        left: -1.25em;
        margin-top: 0.25em;
        list-style-type: none;
        font-variant: small-caps;
    }
    
    li > div.checkmark {
    	display: inline;
    	visibility: hidden;
    }
    li > div.done {
    	visibility: visible;
    }
    
    li:hover > div.checkmark {
    	visibility: visible;
    	opacity: 0.5;
    	color: var(--color-primary-element);
    }
    
</style>
