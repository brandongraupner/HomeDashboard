<script>
export default{
    props: {
        shopping_list_items: Array,
    },
    emits: ['add', 'buy'],
    methods: {
        get_new_item() {
            let new_item = document.querySelectorAll(".item-input");
            if(new_item[0].value.length > 0 || new_item[1].value >= 0){
                return {name: new_item[0].value, amount: new_item[1].value};
            }
            return {};
        }
    }
};

</script>

<template>
    <section>
        <input type="text" class="item-input" required/>
        <input type="number" class="item-input" required/>
        <button @click="$emit('add', get_new_item())">add</button>
    </section>

    <section>
            <ul>
                <li v-for="(item, index) in shopping_list_items" :key="index">
                    <span contenteditable="false" id="id"> {{ index }}</span>
                    <span contenteditable="true" id="name">{{ item.name }}</span>
                    <span  contenteditable="true" id="amount">{{ item.amount}}</span>
                </li>
            </ul>
            <button @click="$emit('buy')">I've bought all these items</button>
        </section>
</template>