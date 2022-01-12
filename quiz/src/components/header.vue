<template>
    <div>
        <b-navbar type="dark" variant="dark">
            <b-navbar-nav>
                <b-navbar-brand style="margin-left:40px;">Quesiton & Answer</b-navbar-brand>
                <b-nav-item disabled>Question {{index}}/10</b-nav-item>
            </b-navbar-nav>
        </b-navbar>
    </div>
</template>


<script>

export default ({
    setup() {
        
    },
    props:{
        index: Number,
    }
})
</script>
