<template>
    <form @submit.prevent>
        <h4>Создание поста</h4>
        <MyInput v-focus v-model="post.title" type="text" placeholder="Название"/>
        <MyInput v-model="post.body" type="text" placeholder="Описание"/>
        <MyButton @click="createPost" class="btn" style="align-self: flex-end; margin-top: 15px;">Создать</MyButton>
    </form>
</template>

<script>
import MyButton from './UI/MyButton.vue';
import MyInput from '@/components/UI/MyInput.vue';

export default {
    components: {MyButton, MyInput},
    emits: ['create'],
    data() {
        return {
            post: {
                title: '',
                body: ''
            }
        };
    },
    methods: {
        createPost() {
            this.post.id = Date.now();
            this.$emit('create', this.post);
            this.post = {
                title: '',
                body: '',
            };
        }
    }
}
</script>

<style>
form {
    display: flex;
    flex-direction: column;
}
.input {
    width: 100%;
    border: 1px solid teal;
    padding: 10px 15px;
    margin-top: 15px;
}
</style>