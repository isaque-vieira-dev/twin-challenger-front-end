<template>
    <form>
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="floatingInput">
            <label for="floatingInput">Name</label>
        </div>
        <div class="form-floating mb-3">
            <textarea class="form-control" id="floatingTextarea"></textarea>
            <label for="floatingTextarea">Description</label>
        </div>
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="floatingInput">
            <label for="floatingInput">Status</label>
        </div>
    </form>
</template>

<script>
    export default{
        name:'AddTask',
        components:{
            
        }
    }
</script>