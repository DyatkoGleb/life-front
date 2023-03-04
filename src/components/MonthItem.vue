<template>
    <div class="month-item__wrapper">
        <div style="display: flex">
            <div class="month-id">{{ month.id }}</div>
            -
            <div class="month-name">{{ month.name }}</div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        month: {
            type: Object,
            required: true
        }
    }
}
</script>

<style scoped>
.month-item__wrapper {
    max-width: 700px;
    width: 100%;
    margin: auto;
    margin-bottom: 10px;
    padding: 20px;
    border-radius: 12px;
    background-color: #15151d;
}
</style>