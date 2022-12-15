<template>
  <LayOut @eliminarLista="removerArray">
    <template #head>
      <HeaDer />
    </template>
    <template #resume>
      <Resume
        :label="'Ahorro total'"
        :fullAmount="totalAmount"
        :amount="monto"
        :date="dateLabel"
      >
        <template #graphic>
          <GraPhic :monthAmount="month" @seleccion="select" />
        </template>
        <template #action>
          <AcTion @anadir="anadido" />
        </template>
      </Resume>
    </template>
    <template #movements>
      <MoVements :movements="movementsArray" @eliminar="eliminado" />
    </template>
  </LayOut>
</template>

<script>
import HeaDer from "./HeaDer.vue";
import LayOut from "./LayOut.vue";
import Resume from "./Resume/InDex.vue";
import AcTion from "./AcTion.vue";
import MoVements from "./Movements/InDex.vue";
import GraPhic from "./Resume/GraPhic.vue";

export default {
  components: {
    HeaDer,
    LayOut,
    Resume,
    AcTion,
    MoVements,
    GraPhic,
  },
  data() {
    return {
      null: null,
      monto: null,
      movementsArray: [],
    };
  },
  computed: {
    month() {
      const lastMonth = this.movementsArray
        .filter((m) => {
          const today = new Date();
          const oldMonth = today.setDate(today.getDate() - 30);
          return m.time > oldMonth;
        })
        .map((m) => m.amount);
      return lastMonth.map((m, i) => {
        const newArray = lastMonth.slice(0, i + 1);
        console.log("Primer elemento de la lista: ", newArray);
        return newArray.reduce((elementOne, movement) => {
          return elementOne + movement;
        }, 0);
      });
    },
    totalAmount() {
      return this.movementsArray.reduce((valorInicial, valoresArray) => {
        return valorInicial + valoresArray.amount;
      }, 0);
    },
    dateLabel() {
      return "today";
    },
  },
  mounted() {
    const movimiento = JSON.parse(localStorage.getItem("movement"));
    if (Array.isArray(movimiento)) {
      this.movementsArray = movimiento.map((m) => {
        return {
          ...m,
          time: new Date(m.time),
        };
      });
    }
  },
  methods: {
    anadido(valor) {
      this.movementsArray.push(valor);
      this.save();
    },
    eliminado(value) {
      const index = this.movementsArray.findIndex((m) => m.id === value);
      this.movementsArray.splice(index, 1);
      this.save();
    },
    select(value) {
      this.monto = value;
    },
    removerArray() {
      const listValues = this.movementsArray.length;
      this.movementsArray.splice(0, listValues);
      this.save();
    },
    save() {
      localStorage.setItem("movement", JSON.stringify(this.movementsArray));
    },
  },
};
</script>
