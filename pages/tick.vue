<template>
  <section class="section">
    <div class="column">
      <div class="board x" id="board">
        <div class="cell x" data-cell></div>
        <div class="cell circle" data-cell></div>
        <div class="cell" data-cell></div>
        <div class="cell" data-cell></div>
        <div class="cell" data-cell></div>
        <div class="cell" data-cell></div>
        <div class="cell" data-cell></div>
        <div class="cell" data-cell></div>
        <div class="cell" data-cell></div>
      </div>

      <div class="winning-message" id="winningMessage">
        <div data-winning-message-text></div>
        <button>Restart</button>
      </div>
    </div>
  </section>
</template>
<script>
export default {
  name: "TickTacToe",
  components: {}
};
</script>

<style scoped>
.board {
  display: grid;
  justify-content: center;
  align-content: center;
  justify-items: center;
  align-items: center;
  grid-template-columns: repeat(3, auto);
}
.cell {
  width: var(--cell-size);
  height: var(--cell-size);
  background-color: #fff;
  border: 1px solid black;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  cursor: pointer;
}
.cell:first-child,
.cell:nth-child(2),
.cell:nth-child(3) {
  border-top: none;
}
.cell:nth-child(3n + 1) {
  border-left: none;
}
.cell:nth-child(3n + 3) {
  border-right: none;
}
.cell:last-child,
.cell:nth-child(8),
.cell:nth-child(7) {
  border-bottom: none;
}
.cell.x::before,
.cell.x::after,
.cell.circle::before {
  background: black;
}
.board.x .cell:not(.x):not(.circle):hover::before,
.board.x .cell:not(.x):not(.circle):hover::after,
.board.circle .cell:not(.x):not(.circle):hover::before {
  background: lightgray;
}
.cell.x::before,
.cell.x::after,
.board.x .cell:not(.x):not(.circle):hover::before,
.board.x .cell:not(.x):not(.circle):hover::after {
  content: "";
  width: calc(var(--mark-size) * 0.15);
  position: absolute;
  height: var(--mark-size);
}
.cell.x,
.cell.circle {
  cursor: not-allowed;
}
.cell.x::before,
.board.x .cell:not(.x):not(.circle):hover::before {
  transform: rotate(45deg);
}
.cell.x::after,
.board.x .cell:not(.x):not(.circle):hover::after {
  transform: rotate(-45deg);
}
.cell.circle::before,
.cell.circle::after,
.board.circle .cell:not(.x):not(.circle):hover::before,
.board.circle .cell:not(.x):not(.circle):hover::after {
  content: "";
  position: absolute;
  border-radius: 50%;
}
.cell.circle::before,
.board.circle .cell:not(.x):not(.circle):hover::before {
  width: var(--mark-size);
  height: var(--mark-size);
}
.cell.circle::after,
.board.circle .cell:not(.x):not(.circle):hover::after {
  width: calc(var(--mark-size) * 0.7);
  height: calc(var(--mark-size) * 0.7);
  background: white;
}
</style>
