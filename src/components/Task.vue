
<template>
    <div v-for="task  in tasks" :key="task.id">
        <TaskComponent @toggle-reminder="$emit('toggle-reminder',task.id)" @delete-task = "$emit('delete-task',task.id)" :task = "task"/>
    </div>
</template>



<script>
import TaskComponent from './Tasks';
    export default{
        name:'TaskItem',
        props:{
            tasks:Array
        },
        components:{
            TaskComponent
        },
        emits:['delete-task','toggle-reminder']
    }

</script>