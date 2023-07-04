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
                    >Client Required Coverage area (sq. Km) *</label
                  >
                </div>
                <!-- <div class="text-primary">
                  DL: {{ theRequiredNumberOf5GBaseStation }}
                </div> -->

                <div class="col-4">
                  <input
                    type="number"
                    class="form-control form-control-sm"
                    id="input1"
                    v-model="userDefinedCoverageArea"
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
                    v-model="typeOfSite"
                  >
                    <option selected value="">Open this select menu</option>
                    <option value="factory">Factory</option>
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
                    v-model="transmitPower"
                  />
                </div>
              </div>
            </div>
            <!-- <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label class="form-label">Transmit power (dBm) *</label>
                </div>
                <div class="col-4">
                  <select
                    class="form-select form-select-sm"
                    aria-label=".form-select-sm example"
                    v-model="transmitPower"
                  >
                    <option value="" selected>Choose an option</option>
                    <option value="43">43</option>
                    <option value="44">44</option>
                    <option value="45">45</option>
                  </select>
                </div>
              </div>
            </div> -->
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
                    v-model="carrierFrequency"
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
                  <span
                    ><b v-if="numberOfRadio && simCard"
                      >{{ numberOfRadio }} radio units, {{ simCard }} SIM
                      cards</b
                    ></span
                  >
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
                  <span><b>$00000</b></span>
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
                  <span
                    ><b>{{ coverageArea }} sq. Km</b></span
                  >
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
      userDefinedCoverageArea: 7,
      typeOfSite: "",
      specificHardwareCoverageAreaPerCell: null,
      radioPerCell: null,
      concurrentUser: null,
      numberOfConcurrentNBIoTDevices: null,
      tcoPeriod: null,
      numberOfSite: null,
      numberOfCore: null,
      indoorArea: null,
      outdoorArea: null,
      country: null,
      frequencyRange: null,
      privateWirelessTechnology: null,
      estimatedPriceOfTCO: null,
      numberOfRANRequired: null,
      ranUnitPrice: null,
      proposedCoverageArea: null,
      requiredNumberOfNBIoTDevice: null,
      SiteAcquisitionAnnualCost: null,
      equipmentCost: null,
      backhaulConnectivityAnnualCost: null,
      powerSupplyAnnualCost: null,
      //Link Budget Calculator
      transmitPower: null,
      bandwidth: null,
      antennaGain: null,
      carrierFrequency: null,
      baseStationAntennaHeight: null,
      userTerminalHeight: null,
      shannonCapacityScalingFactorAlpha: null,
      cableLoss: null,
      noiseFigureUrban: null,
      interferenceMargin: null,
      cellEdgeReliablity: null,
      wallPenetarationLoss: null,
      bodyLoss: null,
      GUT: null,
      RxAntennaGain: null,
      modulationScheme: null,
      subCarrierSpacing: null,
      slotsPerSubframe: null,
    };
  },
  watch: {
    typeOfSite() {
      if (this.typeOfSite == "factory") {
        (this.specificHardwareCoverageAreaPerCell = 200),
          (this.radioPerCell = 3),
          (this.concurrentUser = 100),
          (this.outdoorArea = this.userDefinedCoverageArea),
          (this.indoorArea = 0),
          (this.numberOfConcurrentNBIoTDevices = 1000),
          (this.tcoPeriod = 36),
          (this.numberOfSite = 1),
          (this.numberOfCore = 1),
          (this.estimatedPriceOfTCO = 1000),
          (this.numberOfRANRequired = 20),
          (this.ranUnitPrice = 10000),
          (this.proposedCoverageArea =
            this.specificHardwareCoverageAreaPerCell),
          (this.country = "USA"),
          (this.requiredNumberOfNBIoTDevice =
            this.numberOfConcurrentNBIoTDevices),
          (this.SiteAcquisitionAnnualCost = 1000),
          (this.equipmentCost = 10000),
          (this.powerSupplyAnnualCost = 500),
          (this.interferenceMargin = 5),
          //Link Budget Calculator
          (this.bandwidth = 10),
          (this.antennaGain = 18),
          (this.baseStationAntennaHeight = 20);
        (this.userTerminalHeight = 1),
          (this.shannonCapacityScalingFactorAlpha = 0.65),
          (this.cableLoss = 2),
          (this.noiseFigureUrban = 5),
          (this.cellEdgeReliablity = 0.15),
          (this.wallPenetarationLoss = 18),
          (this.bodyLoss = 3),
          (this.GUT = 0),
          (this.RxAntennaGain = 0);
        (this.modulationScheme = 256),
          (this.subCarrierSpacing = 60),
          (this.slotsPerSubframe = 2);
      } else if (this.typeOfSite == 2) {
        return "Nothing";
      }
    },
  },
  computed: {
    numberOfRadio() {
      return this.theRequiredNumberOf5GBaseStation;
    },
    simCard() {
      return this.numberOfRadio * this.concurrentUser;
    },
    cellNumber() {
      return (
        this.userDefinedCoverageArea / this.specificHardwareCoverageAreaPerCell
      );
    },
    totalArea() {
      return this.indoorArea + this.outdoorArea;
    },
    requiredNumberOfCPEDevice() {
      return this.simCard - this.numberOfConcurrentNBIoTDevices;
    },
    siteAcquisitionCostTCOPeriod() {
      return this.SiteAcquisitionAnnualCost * this.tcoPeriod;
    },
    backhaulConnectivityCostTCOPeriod() {
      return this.backhaulConnectivityAnnualCost * this.tcoPeriod;
    },
    //link budget calculator
    equivalentIsotropicallyRadiatedPower() {
      return this.transmitPower + this.antennaGain - this.cableLoss;
    },
    signalToNoiseRatio() {
      const exponent = 1 / (0.65 * this.bandwidth);
      const power = Math.pow(2, exponent);
      const result = 10 * Math.log10(power - 1);
      return result.toFixed(3);
    },
    sensitivityOfTheUserTerminal() {
      const sensitivityValue =
        -174 +
        10 * Math.log10(10 * Math.pow(this.bandwidth, 6)) +
        this.noiseFigureUrban -
        this.signalToNoiseRatio;
      return sensitivityValue.toFixed(3);
    },
    shadowingMargin() {
      // const value =
      //   Math.sqrt(2) *
      //   this.shannonCapacityScalingFactorAlpha *
      //   (2 * this.cellEdgeReliablity);
      // return value.toFixed(3);
      return 6.22;
    },
    convertCarrierFrequencyInGHz() {
      return this.carrierFrequency / 1000;
    },
    maximumAllowablePathloss() {
      return (
        this.equivalentIsotropicallyRadiatedPower +
        this.GUT -
        this.sensitivityOfTheUserTerminal -
        this.interferenceMargin -
        this.shadowingMargin -
        this.wallPenetarationLoss -
        this.bodyLoss
      );
    },
    lineOfSight() {
      const lineOfSightValue = Math.pow(
        10,
        (this.maximumAllowablePathloss +
          0.6 * (this.userTerminalHeight - 1.5) +
          13.54 -
          20 * Math.log10(this.convertCarrierFrequencyInGHz)) /
          39.08
      );
      return lineOfSightValue.toFixed(3);
    },
    cellRadiusInMeter() {
      const squareRootValue = Math.sqrt(
        Math.pow(this.lineOfSight, 2) -
          Math.pow(this.baseStationAntennaHeight - this.userTerminalHeight, 2)
      );
      return squareRootValue.toFixed(3);
    },
    minimalUTSignalLevel() {
      return "Need data from sajol";
    },
    resourceBlocks() {
      const result =
        (this.bandwidth * 1000) /
        (this.subCarrierSpacing * this.slotsPerSubframe);
      return Math.ceil(result);
    },
    resourceBlockBandwidth() {
      return this.subCarrierSpacing / 1000;
    },
    theNoiseBandwidth() {
      const result = this.resourceBlocks * this.resourceBlockBandwidth;
      return result.toFixed(3);
    },
    numberOfBitsPerSymbol() {
      const result = Math.log2(this.modulationScheme);
      return result.toFixed(3);
    },
    symbolRate() {
      const result = this.bandwidth / this.numberOfBitsPerSymbol;
      return result.toFixed(3);
    },
    theReceiverNoiseFloor() {
      const result =
        -174 + 10 * Math.log10(this.theNoiseBandwidth) + this.noiseFigureUrban;
      return result.toFixed(2);
    },
    fiveGNRDL() {
      const result =
        Math.pow(10, -3) *
        4 *
        this.resourceBlocks *
        this.numberOfBitsPerSymbol *
        (948 / 1024) *
        12;
      return result.toFixed(3);
    },
    coverageArea() {
      const pi = Math.PI;
      const result = (pi * Math.pow(this.cellRadiusInMeter, 2)) / 1000000;
      return result.toFixed(3);
    },
    theRequiredNumberOf5GBaseStation() {
      const result = this.userDefinedCoverageArea / this.coverageArea;
      return Math.ceil(result);
    },
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