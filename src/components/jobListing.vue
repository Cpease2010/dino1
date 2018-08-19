<template>
    <li>
        <h4>{{job.title}}</h4>
        <small>{{job.pay}}</small>
        <p>{{job.description}}</p>
        <small>0 dinos are interested in this job</small>
    </li>
</template>

<script>
    export default{
        props: ['job'],
    }
</script>
