<template>
    <aside id="side-bar">
        <h3>Add a Job</h3>
        <form class="job-form">
            <label for="title">Title</label>
            <input v-model="title" type="text" name="title">
            <label for="pay">Compensation</label>
            <input v-model="pay" type="text" name="pay">
            <label for="description">Description</label>
            <textarea v-model="description" name="description" rows="8" cols="40"></textarea>
            <input  type="submit" name="submit" value="Submit" />
        </form>
    </aside>
</template>

<script>
export default {
    data(){
        return {
            title:'',
            pay:'',
            description: ''
        }
    },
}
</script>

