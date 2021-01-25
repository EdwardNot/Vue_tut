<template>
    <div class="record-item" @click="favRecord(record.id)">
        <div class="user-profile_record">
            <div class="record-item_user">
                @{{ username }}
            </div>
            <div class="reord-item_content">
                {{ record.content }}
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Record",
    props: {
        username: {
            type: String,
            required: true
        },
        record: {
            type: Object,
            required: true
        }
    },
    methods: {
        favRecord(id){
            this.$emit('favourite', id)
        }
    }
};
</script>

<style>

.record-item{
    padding: 20px;
    background-color: white;
    border-radius: 5px;
    border: 1px solid #DFE3E8;
    box-sizing: border-box;
    cursor: pointer;
    transition: all 0.25s ease;
}

.record-item:hover{
    transform: scale(1.1, 1.1);
}

.record-item_user{
    font-weight: bold;
}

</style>