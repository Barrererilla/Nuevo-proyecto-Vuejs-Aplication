<template>
  <LayOut>
    <template #head>
      <HeaDer />
    </template>
    <template #resume>
      <Resume
        :label="'Ahorro total'"
        :amount="2000"
        :fullAmount="5600600"
        :date="dateLabel"
      >
        <template #graphic> Graphic </template>
        <template #action>
          <AcTion />
        </template>
      </Resume>
    </template>
    <template #movements>
      <MoVements :movements="movementsArray" />
    </template>
  </LayOut>
</template>

<script>
import HeaDer from "./HeaDer.vue";
import LayOut from "./LayOut.vue";
import Resume from "./Resume/InDex.vue";
import AcTion from "./AcTion.vue";
import MoVements from "./Movements/InDex.vue";

export default {
  components: {
    HeaDer,
    LayOut,
    Resume,
    AcTion,
    MoVements,
  },
  data() {
    return {
      null: null,
      dateLabel: "1/12/22",
      movementsArray: [
        {
          id: 0,
          title: "Movimientos 1",
          description: "Este puede ser un ingreso a un gasto",
          amount: -5000,
        },
        {
          id: 1,
          title: "Movimientos 2",
          description: "Este puede ser un ingreso a un gasto",
          amount: 5000,
        },
        {
          id: 2,
          title: "Movimientos 3",
          description: "Este puede ser un ingreso a un gasto",
          amount: -5000,
        },
        {
          id: 3,
          title: "Movimientos 4",
          description: "Este puede ser un ingreso a un gasto",
          amount: 5000,
        },
        {
          id: 4,
          title: "Movimientos 5",
          description: "Este puede ser un ingreso a un gasto",
          amount: -5000,
        },
        {
          id: 5,
          title: "Movimientos 6",
          description: "Este puede ser un ingreso a un gasto",
          amount: 5000,
        },
        {
          id: 6,
          title: "Movimientos 7",
          description: "Este puede ser un ingreso a un gasto",
          amount: 5000,
        },
        {
          id: 7,
          title: "Movimientos 8",
          description: "Este puede ser un ingreso a un gasto",
          amount: 5000,
        },
        {
          id: 8,
          title: "Movimientos 9",
          description: "Este puede ser un ingreso a un gasto",
          amount: 5000,
        },
      ],
    };
  },
};
</script>
