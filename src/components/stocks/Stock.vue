<template>
  <div class="card">
    <div class="card-header text-primary">
      <h3 class="card-title">
        Name
        <small>(Price: Price)</small>
      </h3>
    </div>
    <div class="card-body text-primary">
      <div class="pull-left">
        <input
          type="number"
          class="form-control"
          placeholder="Quantity"
        >
      </div>
      <div class="pull-right">
        <button
          class="btn btn-primary"
          >Buy</button>
      </div>
    </div>
  </div>
</template>

<style>
  .card {
    width: 48%;
    padding: 15px;
    margin-bottom: 40px;
    margin-right: 30px;
    border: 1px solid #337ab7;
    border-radius: 5px;
  }

  .card-header {
    margin-bottom: 15px;
  }
</style>
