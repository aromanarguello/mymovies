<style>
  div {
    width: 300px;
    height: 350px;
    -webkit-box-shadow: 0px 0px 10px 3px rgba(176, 176, 176, 0.72);
    -moz-box-shadow: 0px 0px 10px 3px rgba(176, 176, 176, 0.72);
    box-shadow: 0px 0px 10px 3px rgba(176, 176, 176, 0.72);
    display: grid;
    grid-template-rows: 0.5fr 1fr;
    margin-bottom: 25px;
    border-radius: 2.5px;
  }
</style>

<div class="card-item">
  <slot>Sorry!</slot>
</div>
