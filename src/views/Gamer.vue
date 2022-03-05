<template>
    <div>
        <ul>
            <li v-for="game in gamers" :key="game.id">{{ game.name }}</li>
        </ul>
        <input type="submit" value="Alterar" @click="change" />
        <input type="submit" value="Cortar" @click="cut" />
        <hr />
        <ul>
            <li v-for="(value, key) in gamer" :key="key">{{ key }}: {{ value }}</li>
        </ul>
        <input type="submit" value="Adicionar propriedade" @click="add" />
        <input type="submit" value="Alterar objeto" @click="changeo" />
    </div>
</template>

<script>
export default {
    data() {
        return {
            gamers: [
                { id: 10, name: 'Ze' },
                { id: 20, name: 'Tiago' },
                { id: 30, name: 'Marcos' },
                { id: 40, name: 'Sergio' },
                { id: 50, name: 'Franco' },
                { id: 60, name: 'Zizo' },
            ],
            gamer: {
                name: 'Marcos',
                childrens: 0,
            },
        };
    },
    mounted() {
        // delete this.gamers[0]; // Nao eh possivel, nao reativo

        this.gamers.splice(0, 1); // Alternativa 1

        this.$delete(this.gamers, 1); // Alternativa 2
    },
    methods: {
        change() {
            // this.gamers[0] = { id: 10, name: 'Francisco' }; // Nao eh possivel, nao reativo

            const gamer_a = { id: 70, name: 'Gesse' };
            const gamer_b = { id: 80, name: 'Santos' };

            this.gamers.splice(1, 1, gamer_a); // Alternativa 1

            this.$set(this.gamers, 0, gamer_b); // Alternativa 2
        },
        cut() {
            this.gamers.splice(2, 1); // Corta 1 da posicao 2 em diante
        },
        add() {
            // this.gamer['age'] = 10; // Nao eh possivel, nao reativo

            this.$set(this.gamer, 'age', 30);
        },
        changeo() {
            // Object.assign(this.gamer, { price: 100, color: 'red' }); // Altera porem nao eh reativo

            const gamer = { price: 100, color: 'red' };

            this.gamer = Object.assign({}, this.gamer, gamer); // Faz uma copia profunda do objeto

            gamer.color = 'blue';
        },
    },
};
</script>

<style></style>
