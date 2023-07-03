<template>
  <div class="child-container pt-5">
    <div class="row">
      <div class="col-md-6 col-12">
        <div class="card h-100">
          <div class="card-header card-header-custom">
            <div class="parameter-first-heading">Parameters</div>
            <div class="parameter-second-heading">
              Enter the required parameters for calculation
            </div>
          </div>
          <div class="card-body">
            <div class="row">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Coverage area (sq. ft) *</label
                  >
                </div>
                <div class="col-4">
                  <input
                    type="number"
                    class="form-control form-control-sm"
                    id="input1"
                  />
                </div>
              </div>
            </div>
            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label">Type of site *</label>
                </div>
                <div class="col-4">
                  <select
                    class="form-select form-select-sm"
                    aria-label=".form-select-sm example"
                  >
                    <option selected>Open this select menu</option>
                    <option value="1">One</option>
                    <option value="2">Two</option>
                    <option value="3">Three</option>
                  </select>
                </div>
              </div>
            </div>
            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Max number of user devices *</label
                  >
                </div>
                <div class="col-4">
                  <input
                    type="number"
                    class="form-control form-control-sm"
                    id="input1"
                  />
                </div>
              </div>
            </div>
            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Transmit power (dBm) *</label
                  >
                </div>
                <div class="col-4">
                  <input
                    type="number"
                    class="form-control form-control-sm"
                    id="input1"
                  />
                </div>
              </div>
            </div>
            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Carrier frequency (MHz)*</label
                  >
                </div>
                <div class="col-4">
                  <input
                    type="number"
                    class="form-control form-control-sm"
                    id="input1"
                  />
                </div>
              </div>
            </div>
          </div>
          <div class="card-footer estimate-card-footer">
            <div class="d-flex justify-content-between">
              <div class="col form-check form-switch">
                <label class="form-check-label" for="flexSwitchCheckDefault"
                  >Advance Mode</label
                >
                <input
                  class="form-check-input"
                  type="checkbox"
                  id="flexSwitchCheckDefault"
                />
              </div>
              <div class="col-6 text-end">
                <button class="btn btn-outline-primary btn-sm">Reset</button>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="col-md-6 col-12 estimate-advance-parent">
        <div class="card h-100">
          <div class="card-header card-header-custom">
            <div class="parameter-first-heading">Estimates</div>
            <div class="parameter-second-heading">
              Based on the answers provided, we estimate the following hardware
            </div>
          </div>
          <div class="card-body">
            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Estimated Hardware</label
                  >
                </div>
                <div class="col-6 text-end">
                  <span><b>7 radio units, 400 SIM cards</b></span>
                </div>
              </div>
            </div>

            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Total projected cost (monthly)</label
                  >
                </div>
                <div class="col-6 text-end">
                  <span><b>$50,400.00</b></span>
                </div>
              </div>
            </div>

            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Estimated Coverage</label
                  >
                </div>
                <div class="col-6 text-end">
                  <span><b>10000 sq. ft</b></span>
                </div>
              </div>
            </div>
          </div>
          <div class="card-footer estimate-card-footer">
            <div class="d-flex justify-content-between">
              <div class="col form-check form-switch">
                <label class="form-check-label" for="flexSwitchCheckDefault"
                  >Advance Mode</label
                >
                <input
                  class="form-check-input"
                  type="checkbox"
                  id="flexSwitchCheckDefault"
                />
              </div>
              <div class="col-6 text-end">
                <button class="btn btn-primary btn-sm download-btn">
                  Download
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!--Factory active use cases start-->
    <div class="row mt-4 py-3 border mx-1">
      <div class="col col-xs-12">
        <div>Factory active use cases</div>
        <ul class="list-group list-group-flush use-case-list">
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 first-use-case"></i
            >Autonomous Mobile Robots
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 second-use-case"></i
            >Collaborative Robots
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 third-use-case"></i>AR
            Inspection & Support
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fourth-use-case"></i>Asset
            Conditioning Monitoring
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fifth-use-case"></i>Digital
            Twin
          </li>
        </ul>
      </div>
      <div class="col col-xs-12"><img src="../assets/use-cases.jpg" /></div>
    </div>
    <!--Factory active use cases end-->

    <div class="row mt-4 py-3 border mx-1">
      <div class="col col-xs-12">
        <div>Factory active use cases</div>
        <BusinessCaseChart></BusinessCaseChart>
      </div>
      <div class="col col-xs-12"><BusinessCaseChart></BusinessCaseChart></div>
    </div>
  </div>
</template>

<script>
import BusinessCaseChart from "./BusinessCaseChart.vue";
export default {
  name: "NybSysCalculator",
  components: { BusinessCaseChart },
  data() {
    return {
      propertyName: 5,
    };
  },
};
</script>

<style>
.child-container {
  width: 1080px;
}
.card-header-custom {
  background: #edf2f5;
}
.parameter-first-heading {
  font-style: normal;
  font-weight: 500;
  font-size: 24px;
  line-height: 36px;
  color: #000000;
}
.parameter-first-heading {
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 24px;
  color: #000000;
}
.download-btn {
  background-color: #3d6cd7;
  color: #ffffff;
}
.estimate-advance-parent {
  position: relative;
}
.estimate-advance {
  position: absolute;
  bottom: 0;
}
.estimate-card-footer {
  background-color: #ffffff !important;
  border-top: none !important;
}
.use-case-list li {
  border: none;
  padding-left: 0;
  margin-left: 0;
}
.first-use-case {
  color: #6dbdbf;
}
.second-use-case {
  color: #57a0e5;
}
.third-use-case {
  color: #ed6d85;
}
.fourth-use-case {
  color: #f0953f;
}
.fifth-use-case {
  color: #f7cf6b;
}
</style>