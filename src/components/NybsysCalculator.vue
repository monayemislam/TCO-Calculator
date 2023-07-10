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
            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Measurement Unit *</label
                  >
                </div>
                <div class="col-4">
                  <select
                    class="form-select form-select-sm"
                    aria-label=".form-select-sm example"
                    v-model="measurementUnitType"
                  >
                    <option value="">Select</option>
                    <option value="metric">Metric</option>
                    <option value="imperial">Imperial</option>
                  </select>
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
                    v-model="typeOfSiteCategory"
                  >
                    <option selected value="">Select</option>
                    <option value="indoor">Indoor</option>
                    <option value="outdoor">Outdoor</option>
                  </select>
                </div>
              </div>
            </div>
            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Please select your site *</label
                  >
                </div>
                <div class="col-4">
                  <select
                    class="form-select form-select-sm"
                    aria-label=".form-select-sm example"
                    v-model="typeOfSite"
                  >
                    <option selected value="">Select</option>
                    <option
                      value="factory"
                      v-if="typeOfSiteCategory == 'indoor'"
                    >
                      Factory
                    </option>
                    <option value="farm" v-if="typeOfSiteCategory == 'outdoor'">
                      Farm
                    </option>
                    <option
                      value="office"
                      v-if="typeOfSiteCategory == 'indoor'"
                    >
                      Office
                    </option>
                    <option
                      value="shipyard"
                      v-if="typeOfSiteCategory == 'outdoor'"
                    >
                      Shipyard
                    </option>
                    <option
                      value="campus"
                      v-if="typeOfSiteCategory == 'outdoor'"
                    >
                      Campus
                    </option>
                    <option
                      value="indoorfarm"
                      v-if="typeOfSiteCategory == 'indoor'"
                    >
                      Indoor Farm
                    </option>
                    <option
                      value="mining-area"
                      v-if="typeOfSiteCategory == 'outdoor'"
                    >
                      Mining Area
                    </option>
                    <option
                      value="supershop"
                      v-if="typeOfSiteCategory == 'indoor'"
                    >
                      Super Shop
                    </option>
                    <option
                      value="warehouse"
                      v-if="typeOfSiteCategory == 'indoor'"
                    >
                      Warehouse
                    </option>
                    <option
                      value="airport"
                      v-if="typeOfSiteCategory == 'outdoor'"
                    >
                      Airport
                    </option>
                    <option
                      value="garments"
                      v-if="typeOfSiteCategory == 'indoor'"
                    >
                      Garments
                    </option>
                    <option
                      value="stadium"
                      v-if="typeOfSiteCategory == 'outdoor'"
                    >
                      Stadium
                    </option>
                    <option
                      value="construction-site"
                      v-if="typeOfSiteCategory == 'outdoor'"
                    >
                      Construction Site
                    </option>
                  </select>
                </div>
              </div>
            </div>
            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Client Required Coverage area
                    <span
                      v-if="
                        measurementUnitType == 'imperial' &&
                        typeOfSiteCategory == 'outdoor'
                      "
                      >(sq. mi)</span
                    >
                    <span
                      v-if="
                        typeOfSiteCategory == 'indoor' &&
                        measurementUnitType == 'imperial'
                      "
                      >(sq. ft)</span
                    >
                    <span
                      v-if="
                        measurementUnitType == 'metric' &&
                        typeOfSiteCategory == 'outdoor'
                      "
                      >(sq. km)</span
                    >
                    <span
                      v-if="
                        typeOfSiteCategory == 'indoor' &&
                        measurementUnitType == 'metric'
                      "
                      >(sq. m)</span
                    >
                    *</label
                  >
                </div>
                <!-- <div class="text-primary">
                  DL: {{ theRequiredNumberOf5GBaseStation }}
                </div> -->

                <div class="col-4">
                  <input
                    type="number"
                    class="form-control form-control-sm"
                    v-model="userDefinedCoverageArea"
                  />
                </div>
              </div>
            </div>

            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Required number of user devices *</label
                  >
                </div>
                <div class="col-4">
                  <input
                    type="number"
                    class="form-control form-control-sm"
                    id="maxNumberofDevice"
                    placeholder="eg. 100"
                    v-model="maxNumberOfUserDevices"
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
                  <select
                    class="form-select form-select-sm"
                    aria-label=".form-select-sm example"
                    v-model="transmitPower"
                  >
                    <option selected value="">Select</option>
                    <option :value="Number('24')">24 (250 mW)</option>
                    <option :value="Number('30')">30 (1 W)</option>
                    <option :value="Number('46')">46 (40 W)</option>
                  </select>
                </div>
              </div>
            </div>
            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Center frequency (MHz)*</label
                  >
                </div>
                <div class="col-4">
                  <input
                    type="number"
                    class="form-control form-control-sm"
                    v-model="carrierFrequency"
                    min="3550"
                    max="3700"
                  />
                </div>
              </div>
            </div>
            <!-- <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Base Station Antenna Height (m)*</label
                  >
                </div>
                <div class="col-4">
                  <input
                    type="number"
                    class="form-control form-control-sm"
                    v-model="baseStationAntennaHeight"
                    min="15"
                    max="100"
                  />
                </div>
              </div>
            </div> -->
            <!-- <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >UE Antenna Height (m)*</label
                  >
                </div>
                <div class="col-4">
                  <input
                    type="number"
                    class="form-control form-control-sm"
                    min="1"
                    max="10"
                    v-model="userTerminalHeight"
                  />
                </div>
              </div>
            </div> -->
            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Bandwidth (MHz) *</label
                  >
                </div>
                <div class="col-4">
                  <input
                    type="number"
                    class="form-control form-control-sm"
                    min="1"
                    v-model="bandwidth"
                  />
                </div>
              </div>
            </div>
            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Baseband Unit Antenna Gain(dBi) *</label
                  >
                </div>
                <div class="col-4">
                  <input
                    type="number"
                    class="form-control form-control-sm"
                    min="1"
                    v-model="antennaGain"
                  />
                </div>
              </div>
            </div>
            <!-- <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Noise Figure (dBm)*</label
                  >
                </div>
                <div class="col-4">
                  <select
                    class="form-select form-select-sm"
                    aria-label=".form-select-sm example"
                    v-model="noiseFigureUrban"
                  >
                    <option selected value="">Select</option>
                    <option :value="Number('9')">Dense Urban</option>
                    <option :value="Number('8')">Urban</option>
                    <option :value="Number('7')">Suburban</option>
                    <option :value="Number('6')">Rural</option>
                    <option :value="Number('5')">LOS</option>
                  </select>
                </div>
              </div>
            </div> -->
            <!-- <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label class="form-label">Modulation Scheme (QAM)*</label>
                </div>
                <div class="col-4">
                  <select
                    class="form-select form-select-sm"
                    aria-label=".form-select-sm example"
                    v-model="modulationScheme"
                  >
                    <option selected value="">Select</option>
                    <option :value="Number('64')">QAM64</option>
                    <option :value="Number('256')">QAM256</option>
                  </select>
                </div>
              </div>
            </div>
            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label class="form-label">Subcarrier Spacing (kHz)*</label>
                </div>
                <div class="col-4">
                  <select
                    class="form-select form-select-sm"
                    aria-label=".form-select-sm example"
                    v-model="subCarrierSpacing"
                  >
                    <option selected value="">Select</option>
                    <option :value="Number('15')">15 KHz</option>
                    <option :value="Number('30')">30 KHz</option>
                    <option :value="Number('60')">60 KHz</option>
                    <option :value="Number('120')">120 KHz</option>
                    <option :value="Number('240')">240 KHz</option>
                  </select>
                </div>
              </div>
            </div>
            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label class="form-label">Antenna Type*</label>
                </div>
                <div class="col-4">
                  <select
                    class="form-select form-select-sm"
                    aria-label=".form-select-sm example"
                    v-model="antennaType"
                  >
                    <option selected value="">Select</option>
                    <option :value="Number('1')">Omni</option>
                    <option :value="Number('3')">Sector</option>
                  </select>
                </div>
              </div>
            </div> -->
          </div>
          <!-- <div class="card-footer estimate-card-footer">
            <div class="d-flex justify-content-between">
              <div class="col form-check form-switch">
                <label class="form-check-label" for="flexSwitchCheckInput"
                  >Advance Mode</label
                >
                <input
                  class="form-check-input"
                  type="checkbox"
                  id="flexSwitchCheckInput"
                  @change="toggleInputAdvanceMode"
                />
              </div>
              <div class="col-6 text-end">
                <button class="btn btn-outline-primary btn-sm">Reset</button>
              </div>
            </div>
          </div> -->
        </div>
      </div>
      <div class="col-md-6 col-12 estimate-advance-parent">
        <div class="card h-100">
          <div class="card-header card-header-custom">
            <div class="parameter-first-heading">Estimation</div>
            <div class="parameter-second-heading">
              Please see your results below.
            </div>
          </div>
          <div class="card-body">
            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Estimated Baseband Unit</label
                  >
                </div>
                <div class="col-6 text-end">
                  <span
                    ><b v-if="numberOfRadio"
                      ><span
                        v-if="
                          typeOfSiteCategory == 'indoor' &&
                          measurementUnitType == 'metric'
                        "
                        >{{ Math.ceil(numberOfRadio / 1000000) }} radio
                        units</span
                      >
                      <span
                        v-if="
                          typeOfSiteCategory == 'indoor' &&
                          measurementUnitType == 'imperial'
                        "
                        >{{ Math.ceil(numberOfRadio / 10760000) }} radio
                        units</span
                      >
                      <span
                        v-if="
                          typeOfSiteCategory == 'outdoor' &&
                          measurementUnitType == 'imperial'
                        "
                        >{{ Math.ceil(numberOfRadio / 0.386102) }} radio
                        units</span
                      >
                      <span
                        v-if="
                          typeOfSiteCategory == 'outdoor' &&
                          measurementUnitType == 'metric'
                        "
                        >{{ Math.ceil(numberOfRadio) }} radio units</span
                      >
                    </b></span
                  >
                </div>
              </div>
            </div>

            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Estimated SIM Card</label
                  >
                </div>
                <div class="col-6 text-end">
                  <span
                    ><b v-if="maxNumberOfUserDevices"
                      >{{ maxNumberOfUserDevices }} SIM cards
                    </b></span
                  >
                </div>
              </div>
            </div>

            <!-- <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Total projected cost (monthly)</label
                  >
                </div>
                <div class="col-6 text-end">
                  <span><b></b></span>
                </div>
              </div>
            </div> -->

            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label for="input1" class="form-label"
                    >Estimated Coverage</label
                  >
                </div>
                <div class="col-6 text-end">
                  <span
                    ><b
                      v-if="
                        coverageArea !== null &&
                        !isNaN(coverageArea) &&
                        coverageArea !== '' &&
                        isFinite(coverageArea)
                      "
                    >
                      <span
                        v-if="
                          measurementUnitType == 'metric' &&
                          typeOfSiteCategory == 'indoor'
                        "
                        >{{ (coverageArea * 1000000).toFixed(0) }} sq. m</span
                      >
                      <span
                        v-if="
                          measurementUnitType == 'imperial' &&
                          typeOfSiteCategory == 'indoor'
                        "
                        >{{ (coverageArea * 10760000).toFixed(0) }} sq. ft</span
                      >
                      <span
                        v-if="
                          measurementUnitType == 'imperial' &&
                          typeOfSiteCategory == 'outdoor'
                        "
                        >{{ (coverageArea * 0.386102).toFixed(3) }} sq. mi</span
                      >
                      <span
                        v-if="
                          measurementUnitType == 'metric' &&
                          typeOfSiteCategory == 'outdoor'
                        "
                        >{{ (coverageArea * 1).toFixed(0) }} sq. Km</span
                      ></b
                    ></span
                  >
                </div>
              </div>
            </div>

            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label class="form-label">Base Station to UE distance</label>
                </div>
                <div class="col-6 text-end">
                  <span
                    ><b
                      v-if="
                        cellRadiusInMeter !== null &&
                        !isNaN(cellRadiusInMeter) &&
                        cellRadiusInMeter !== '' &&
                        isFinite(cellRadiusInMeter)
                      "
                    >
                      <span
                        v-if="
                          measurementUnitType == 'metric' &&
                          typeOfSiteCategory == 'indoor'
                        "
                        >{{ cellRadiusInMeter }} m</span
                      ><span
                        v-if="
                          measurementUnitType == 'imperial' &&
                          typeOfSiteCategory == 'indoor'
                        "
                        >{{ (cellRadiusInMeter * 3.28084).toFixed(2) }} ft</span
                      ><span
                        v-if="
                          measurementUnitType == 'metric' &&
                          typeOfSiteCategory == 'outdoor'
                        "
                        >{{ (cellRadiusInMeter / 1000).toFixed(2) }} Km</span
                      ><span
                        v-if="
                          measurementUnitType == 'imperial' &&
                          typeOfSiteCategory == 'outdoor'
                        "
                        >{{
                          (cellRadiusInMeter * 0.000621371).toFixed(2)
                        }}
                        mi</span
                      ></b
                    ></span
                  >
                </div>
              </div>
            </div>
            <!-- <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label class="form-label">Propagation Model Pathloss</label>
                </div>
                <div class="col-6 text-end">
                  <span
                    ><b
                      v-if="
                        maximumAllowablePathloss !== null &&
                        !isNaN(maximumAllowablePathloss) &&
                        maximumAllowablePathloss !== '' &&
                        isFinite(maximumAllowablePathloss)
                      "
                      >{{ maximumAllowablePathloss.toFixed(2) }} dBm</b
                    ></span
                  >
                </div>
              </div>
            </div>
            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label class="form-label">SNR</label>
                </div>
                <div class="col-6 text-end">
                  <span
                    ><b
                      v-if="
                        signalToNoiseRatio !== null &&
                        !isNaN(signalToNoiseRatio) &&
                        signalToNoiseRatio !== '' &&
                        isFinite(signalToNoiseRatio)
                      "
                      >{{ signalToNoiseRatio }}</b
                    ></span
                  >
                </div>
              </div>
            </div>
            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label class="form-label">Sensitivity at UE</label>
                </div>
                <div class="col-6 text-end">
                  <span
                    ><b
                      v-if="
                        sensitivityOfTheUserTerminal !== null &&
                        !isNaN(sensitivityOfTheUserTerminal) &&
                        sensitivityOfTheUserTerminal !== '' &&
                        isFinite(sensitivityOfTheUserTerminal)
                      "
                      >{{ sensitivityOfTheUserTerminal }} dB</b
                    ></span
                  >
                </div>
              </div>
            </div>
            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label class="form-label">Resource Block</label>
                </div>
                <div class="col-6 text-end">
                  <span
                    ><b
                      v-if="
                        resourceBlocks !== null &&
                        !isNaN(resourceBlocks) &&
                        resourceBlocks !== '' &&
                        isFinite(resourceBlocks)
                      "
                      >{{ resourceBlocks }}</b
                    ></span
                  >
                </div>
              </div>
            </div> -->
            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label class="form-label">5G NR DL Throughput</label>
                </div>
                <div class="col-6 text-end">
                  <span
                    ><b
                      v-if="
                        fiveGNRDL !== null &&
                        !isNaN(fiveGNRDL) &&
                        fiveGNRDL !== '' &&
                        isFinite(fiveGNRDL)
                      "
                      >{{ fiveGNRDL * 4 }} Mbps</b
                    ></span
                  >
                </div>
              </div>
            </div>
            <div class="row pt-3">
              <div class="d-flex justify-content-between">
                <div class="col">
                  <label class="form-label">Estimated Cost (monthly)</label>
                </div>
                <div class="col-6 text-end">
                  <span
                    ><b
                      v-if="
                        numberOfRadio !== null &&
                        estimatedCost !== null &&
                        !isNaN(numberOfRadio) &&
                        numberOfRadio !== '' &&
                        isFinite(numberOfRadio)
                      "
                    >
                      <span
                        v-if="
                          typeOfSiteCategory == 'indoor' &&
                          measurementUnitType == 'metric'
                        "
                        >{{
                          "$" +
                          Math.ceil(numberOfRadio / 1000000) * estimatedCost
                        }}
                      </span>

                      <span
                        v-if="
                          typeOfSiteCategory == 'indoor' &&
                          measurementUnitType == 'imperial'
                        "
                        >{{
                          "$" +
                          Math.ceil(numberOfRadio / 10760000) * estimatedCost
                        }}
                      </span>
                      <span
                        v-if="
                          typeOfSiteCategory == 'outdoor' &&
                          measurementUnitType == 'imperial'
                        "
                        >{{
                          "$" +
                          Math.ceil(numberOfRadio / 0.386102) * estimatedCost
                        }}</span
                      >
                      <span
                        v-if="
                          typeOfSiteCategory == 'outdoor' &&
                          measurementUnitType == 'metric'
                        "
                        >{{
                          "$" + Math.ceil(numberOfRadio) * estimatedCost
                        }}</span
                      >
                    </b></span
                  >
                </div>
              </div>
            </div>
          </div>
          <div class="card-footer estimate-card-footer">
            <div class="d-flex justify-content-between">
              <div class="col form-check form-switch">
                <!-- <label class="form-check-label" for="flexSwitchCheckDefault"
                  >Advance Mode</label
                >
                <input
                  class="form-check-input"
                  type="checkbox"
                  id="flexSwitchCheckDefault"
                /> -->
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
      <!--Factory active use cases start-->
      <div class="col col-xs-12" v-if="typeOfSite == 'factory'">
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
      <!--Factory active use cases end-->
      <!--poultry firm start-->
      <div class="col col-xs-12" v-if="typeOfSite == 'indoorfarm'">
        <div>Indoor Farm active use cases</div>
        <ul class="list-group list-group-flush use-case-list">
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fifth-use-case"></i
            >Temperature, Humidity, Air Quality and Harmful Gases monitoring
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 first-use-case"></i
            >Automated Lighting
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 second-use-case"></i
            >Automated Ventilation
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 third-use-case"></i>Video
            Surveillance
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fourth-use-case"></i
            >Automated Water and Feed Supply
          </li>
        </ul>
      </div>
      <!--poultry firm End-->
      <!--beef firm start-->
      <div class="col col-xs-12" v-if="typeOfSite == 'farm'">
        <div>Outdoor Farm active use cases</div>
        <ul class="list-group list-group-flush use-case-list">
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fifth-use-case"></i
            >Temperature, Humidity, Air Quality and Harmful Gases monitoring
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 first-use-case"></i
            >Automated Lighting
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 second-use-case"></i
            >Automated Ventilation
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 third-use-case"></i>Video
            Camera/Drone Surveillance
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fourth-use-case"></i>Smart
            Tags
          </li>
        </ul>
      </div>
      <!--beef firm End-->
      <!--Warehouse start-->
      <div class="col col-xs-12" v-if="typeOfSite == 'warehouse'">
        <div>Warehouse active use cases</div>
        <ul class="list-group list-group-flush use-case-list">
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fifth-use-case"></i>Asset
            Monitoring
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 first-use-case"></i>VIdeo
            Monitoring
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 second-use-case"></i
            >Automated Guided Vehicles
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 third-use-case"></i>Access
            Control
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fourth-use-case"></i
            >Environment Control
          </li>
        </ul>
      </div>
      <!--Warehouse End-->
      <!--Garments start-->
      <div class="col col-xs-12" v-if="typeOfSite == 'garments'">
        <div>Garments active use cases</div>
        <ul class="list-group list-group-flush use-case-list">
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fifth-use-case"></i>Asset
            Monitoring
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 first-use-case"></i>VIdeo
            Monitoring
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 second-use-case"></i>AI
            Inspection
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 third-use-case"></i>Access
            Control
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fourth-use-case"></i
            >Environment Control
          </li>
        </ul>
      </div>
      <!--Garments End-->
      <!--Shipyard start-->
      <div class="col col-xs-12" v-if="typeOfSite == 'shipyard'">
        <div>Shipyard active use cases</div>
        <ul class="list-group list-group-flush use-case-list">
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fifth-use-case"></i
            >Automated RTG Cranes
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 first-use-case"></i>Remote
            control of ship-to-shore cranes
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 second-use-case"></i
            >Automated Guided Vehicles
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 third-use-case"></i>Asset
            Monitoring
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fourth-use-case"></i>Video
            Surveillance
          </li>
        </ul>
      </div>
      <!--Shipyard End-->
      <!--Mining Area start-->
      <div class="col col-xs-12" v-if="typeOfSite == 'mining-area'">
        <div>Mining area active use cases</div>
        <ul class="list-group list-group-flush use-case-list">
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fifth-use-case"></i
            >Autonomous Vehicles
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 first-use-case"></i
            >Autonomous Cranes
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 second-use-case"></i
            >Real-Time Environment Monitoring
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 third-use-case"></i>Remote
            Controlled Drill Rigs
          </li>
        </ul>
      </div>
      <!--Mining Area End-->
      <!--Airport start-->
      <div class="col col-xs-12" v-if="typeOfSite == 'airport'">
        <div>Airport active use cases</div>
        <ul class="list-group list-group-flush use-case-list">
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fifth-use-case"></i>Flight
            Schedule management
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 first-use-case"></i
            >Environment Monitoring
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 second-use-case"></i
            >AIrcraft Management
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 third-use-case"></i>
            Ground Vehicle Management
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fourth-use-case"></i
            >Automated Gates
          </li>
        </ul>
      </div>
      <!--Airport End-->
      <!--Campus start-->
      <div class="col col-xs-12" v-if="typeOfSite == 'campus'">
        <div>Campus active use cases</div>
        <ul class="list-group list-group-flush use-case-list">
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fifth-use-case"></i>Class
            management
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 first-use-case"></i>Library
            management
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 second-use-case"></i>Campus
            environment monitoring
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 third-use-case"></i>
            Access control
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fourth-use-case"></i>Video
            Surveillance
          </li>
        </ul>
      </div>
      <!--Campus End-->
      <!--Stadium start-->
      <div class="col col-xs-12" v-if="typeOfSite == 'stadium'">
        <div>Stadium active use cases</div>
        <ul class="list-group list-group-flush use-case-list">
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fifth-use-case"></i
            >Automated light Control
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 first-use-case"></i>Remote
            Controlled Action Camera
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 second-use-case"></i>Drones
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 third-use-case"></i>
            Access control
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fourth-use-case"></i>Video
            Surveillance
          </li>
        </ul>
      </div>
      <!--Stadium End-->
      <!--Construction  start-->
      <div class="col col-xs-12" v-if="typeOfSite == 'construction-site'">
        <div>Cconstruction Site active use cases</div>
        <ul class="list-group list-group-flush use-case-list">
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fifth-use-case"></i>AR
            Safety helmet
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 first-use-case"></i>Site
            environment monitoring
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 second-use-case"></i>Access
            control
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 third-use-case"></i>
            Video Surveillance
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fourth-use-case"></i>Video
            Worker safety suit
          </li>
        </ul>
      </div>
      <!--Construction End-->
      <!--Office  start-->
      <div class="col col-xs-12" v-if="typeOfSite == 'office'">
        <div>Office active use cases</div>
        <ul class="list-group list-group-flush use-case-list">
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fifth-use-case"></i>Access
            Control
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 first-use-case"></i
            >Appliance Automation
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 second-use-case"></i>Meeting
            room reservation
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 third-use-case"></i>
            Video Surveillance
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fourth-use-case"></i>Video
            Worker safety suit
          </li>
        </ul>
      </div>
      <!--Office End-->
      <!--Supershop start-->
      <div class="col col-xs-12" v-if="typeOfSite == 'supershop'">
        <div>Super Shop active use cases</div>
        <ul class="list-group list-group-flush use-case-list">
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fifth-use-case"></i
            >Inventory management
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 first-use-case"></i>Cash
            management
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 second-use-case"></i>Smart
            ad. management
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 third-use-case"></i>
            Access control
          </li>
          <li class="list-group-item">
            <i class="fa-solid fa-circle fa-xs pe-2 fourth-use-case"></i>Video
            Surveillance
          </li>
        </ul>
      </div>
      <!--Construction End-->

      <div class="col col-xs-12">
        <img
          v-if="useCaseImageSource"
          :src="useCaseImageSource"
          style="width: 600px !important"
          alt="Selected Image"
        />
      </div>
    </div>

    <!-- <div class="row mt-4 py-3 border mx-1">
      <div class="col col-xs-12">
        <div>Factory active use cases</div>
        <BusinessCaseChart></BusinessCaseChart>
      </div>
      <div class="col col-xs-12"><BusinessCaseChart></BusinessCaseChart></div>
    </div> -->

    <div class="row mt-4 py-3 mx-1">
      <div class="col col-xs-12 cell-comparison py-4 border">
        <h3 class="pb-3">Cell Comparison</h3>
        <table class="table table-bordered">
          <tbody>
            <tr>
              <td>Cell Count</td>
              <td>Indoor</td>
              <td>Outdoor</td>
            </tr>
            <tr>
              <td style="background-color: #6dbdbf; color: #ffffff">Wi-Fi 6</td>
              <td>
                <span
                  v-if="
                    typeOfSiteCategory == 'indoor' &&
                    measurementUnitType == 'metric'
                  "
                  >{{
                    (
                      userDefinedCoverageArea /
                      1000000 /
                      wifi6CoverageAre
                    ).toFixed(0)
                  }}</span
                >
                <span
                  v-if="
                    typeOfSiteCategory == 'indoor' &&
                    measurementUnitType == 'imperial'
                  "
                  >{{
                    (
                      userDefinedCoverageArea /
                      10760000 /
                      wifi6CoverageAre
                    ).toFixed(0)
                  }}</span
                >
                <span v-if="typeOfSiteCategory == 'outdoor'">-</span>
              </td>
              <td>
                <span
                  v-if="
                    typeOfSiteCategory == 'outdoor' &&
                    measurementUnitType == 'metric'
                  "
                  >{{
                    (
                      (0.5 * userDefinedCoverageArea) /
                      wifi6CoverageAre
                    ).toFixed(0)
                  }}</span
                >
                <span
                  v-if="
                    typeOfSiteCategory == 'outdoor' &&
                    measurementUnitType == 'imperial'
                  "
                  >{{
                    (
                      (0.5 * userDefinedCoverageArea) /
                      0.386102 /
                      wifi6CoverageAre
                    ).toFixed(0)
                  }}</span
                >
                <span v-if="typeOfSiteCategory == 'indoor'">-</span>
              </td>
            </tr>
            <tr>
              <td style="background-color: #57a0e5; color: #ffffff">
                Private wireless CBRS
              </td>
              <td>
                <span v-if="typeOfSiteCategory == 'indoor'">{{
                  Math.ceil(numberOfRadio / 1000000)
                }}</span>
                <span v-if="typeOfSiteCategory == 'outdoor'">-</span>
              </td>
              <td>
                <span v-if="typeOfSiteCategory == 'outdoor'">{{
                  Math.ceil(numberOfRadio / 0.386102)
                }}</span>
                <span v-if="typeOfSiteCategory == 'indoor'">-</span>
              </td>
            </tr>
            <tr>
              <td style="background-color: #ed6d85; color: #ffffff">
                Private wireless LTE
              </td>
              <td></td>
              <td>
                <span v-if="typeOfSiteCategory == 'outdoor'">
                  <span
                    v-if="
                      userDefinedCoverageArea >= 7 &&
                      userDefinedCoverageArea <= 12
                    "
                    >2</span
                  >
                  <span v-if="userDefinedCoverageArea < 7">1</span>
                </span>
                <span v-if="typeOfSiteCategory == 'indoor'">-</span>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
      <div class="col col-xs-12">
        <h3>TCO Comparison</h3>
      </div>
    </div>

    <div class="row mt-4 py-3 border mx-1">
      <img src="../assets/business-case-overview.png" width="1070px" />
    </div>
    <div class="row mt-4 py-3 border mx-1">
      <img src="../assets/tco-comaprison2.png" width="1070px" />
    </div>
  </div>
</template>

<script>
// import BusinessCaseChart from "./BusinessCaseChart.vue";
export default {
  name: "NybSysCalculator",
  // components: { BusinessCaseChart },
  data() {
    return {
      measurementUnitType: "metric",
      userDefinedCoverageArea: 5,
      typeOfSite: "",
      typeOfSiteCategory: "",
      specificHardwareCoverageAreaPerCell: 200,
      maxNumberOfUserDevices: null,
      radioPerCell: 3,
      concurrentUser: 100,
      numberOfConcurrentNBIoTDevices: 1000,
      tcoPeriod: 36,
      numberOfSite: 1,
      numberOfCore: 1,
      indoorArea: 0,
      // outdoorArea: this.userDefinedCoverageArea,
      country: "USA",
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
      transmitPower: 30,
      bandwidth: 10,
      antennaGain: 18,
      antennaType: 1,
      carrierFrequency: 3600,
      baseStationAntennaHeight: 20,
      userTerminalHeight: 2,
      shannonCapacityScalingFactorAlpha: null,
      cableLoss: 2,
      noiseFigureUrban: 8,
      interferenceMargin: 5,
      cellEdgeReliablity: 0.15,
      wallPenetarationLoss: 18,
      bodyLoss: 3,
      GUT: 0,
      RxAntennaGain: 0,
      modulationScheme: 64,
      subCarrierSpacing: 30,
      slotsPerSubframe: 2,
      useCaseImageSource: null,
      kilometerToMileConverter: 0.621371,
      mileToKilometer: 1.609,
      //cell comparison
      wifi6CoverageAre: 0.0081, //sq.km
      //cost
      estimatedCost: 500,
    };
  },
  methods: {
    toggleInputAdvanceMode() {
      this.isInputAdvanceMode = !this.isInputAdvanceMode;
    },
  },
  watch: {
    typeOfSite() {
      if (this.typeOfSite == "factory") {
        this.useCaseImageSource = require("@/assets/factory.png");
      } else if (this.typeOfSite == "farm") {
        this.useCaseImageSource = require("@/assets/farm.png");
      } else if (this.typeOfSite == "indoorfarm") {
        this.useCaseImageSource = require("@/assets/poultry-farm.jpg");
      } else if (this.typeOfSite == "garments") {
        this.useCaseImageSource = require("@/assets/Garments.jpg");
      } else if (this.typeOfSite == "warehouse") {
        this.useCaseImageSource = require("@/assets/Warehouse.jpg");
      } else if (this.typeOfSite == "shipyard") {
        this.useCaseImageSource = require("@/assets/Shipyard.jpg");
      } else if (this.typeOfSite == "stadium") {
        this.useCaseImageSource = require("@/assets/Stadium.jpg");
      } else if (this.typeOfSite == "mining-area") {
        this.useCaseImageSource = require("@/assets/Mining-area.jpg");
      } else if (this.typeOfSite == "campus") {
        this.useCaseImageSource = require("@/assets/Campus.jpg");
      } else if (this.typeOfSite == "airport") {
        this.useCaseImageSource = require("@/assets/Airport.jpg");
      } else if (this.typeOfSite == "construction-site") {
        this.useCaseImageSource = require("@/assets/Construction.jpg");
      } else if (this.typeOfSite == "office") {
        this.useCaseImageSource = require("@/assets/Office.jpg");
      } else if (this.typeOfSite == "supershop") {
        this.useCaseImageSource = require("@/assets/Supermarket.jpg");
      } else {
        this.useCaseImageSource = require("@/assets/factory.png");
      }

      if (
        this.typeOfSiteCategory == "indoor" &&
        this.measurementUnitType == "metric"
      ) {
        this.userDefinedCoverageArea = 1000000;
      } else if (
        this.typeOfSiteCategory == "indoor" &&
        this.measurementUnitType == "imperial"
      ) {
        this.userDefinedCoverageArea = 10760000;
      } else if (
        this.typeOfSiteCategory == "outdoor" &&
        this.measurementUnitType == "imperial"
      ) {
        this.userDefinedCoverageArea = 5 * 0.386102;
      } else if (
        this.typeOfSiteCategory == "outdoor" &&
        this.measurementUnitType == "metric"
      ) {
        this.userDefinedCoverageArea = 5;
      }
    },
    // measurementUnitType() {
    //   if (this.measurementUnitType == "metric") {
    //     this.userDefinedCoverageArea = 5;
    //   } else {
    //     this.userDefinedCoverageArea =
    //       this.userDefinedCoverageArea * this.mileToKilometer;
    //   }
    // },
    // typeOfSiteCategory() {
    //   if (this.typeOfSiteCategory == "indoor") {
    //     this.userDefinedCoverageArea = 1;
    //   } else {
    //     this.userDefinedCoverageArea = 5;
    //   }
    // },
    // measurementUnitType() {
    //   if (this.measurementUnitType == "metric") {
    //     this.userDefinedCoverageArea = 5;
    //   } else {
    //     this.userDefinedCoverageArea =
    //       this.userDefinedCoverageArea * this.mileToKilometer;
    //   }
    // },
    typeOfSiteCategory() {
      if (
        this.typeOfSiteCategory == "indoor" &&
        this.measurementUnitType == "metric"
      ) {
        this.userDefinedCoverageArea = 1000000;
      } else if (
        this.typeOfSiteCategory == "indoor" &&
        this.measurementUnitType == "imperial"
      ) {
        this.userDefinedCoverageArea = 10760000;
      } else if (
        this.typeOfSiteCategory == "outdoor" &&
        this.measurementUnitType == "imperial"
      ) {
        this.userDefinedCoverageArea = 5 * 0.386102;
      } else if (
        this.typeOfSiteCategory == "outdoor" &&
        this.measurementUnitType == "metric"
      ) {
        this.userDefinedCoverageArea = 5;
      }
    },
    measurementUnitType() {
      if (
        this.typeOfSiteCategory == "indoor" &&
        this.measurementUnitType == "metric"
      ) {
        this.userDefinedCoverageArea = 1000000;
      } else if (
        this.typeOfSiteCategory == "indoor" &&
        this.measurementUnitType == "imperial"
      ) {
        this.userDefinedCoverageArea = 10760000;
      } else if (
        this.typeOfSiteCategory == "outdoor" &&
        this.measurementUnitType == "imperial"
      ) {
        this.userDefinedCoverageArea = 5 * 0.386102;
      } else if (
        this.typeOfSiteCategory == "outdoor" &&
        this.measurementUnitType == "metric"
      ) {
        this.userDefinedCoverageArea = 5;
      }
    },
  },
  computed: {
    numberOfRadio() {
      return this.theRequiredNumberOf5GBaseStation * this.antennaType;
    },
    simCard() {
      return this.numberOfRadio * this.concurrentUser;
    },
    // cellNumber() {
    //   return (
    //     this.userDefinedCoverageArea / this.specificHardwareCoverageAreaPerCell
    //   );
    // },
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
      return result.toFixed(2);
    },
    sensitivityOfTheUserTerminal() {
      const sensitivityValue =
        -174 +
        10 * Math.log10(10 * Math.pow(this.bandwidth, 6)) +
        this.noiseFigureUrban -
        this.signalToNoiseRatio;
      return sensitivityValue.toFixed(2);
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
      return result.toFixed(2);
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
/*cell comparison*/
.cell-comparison {
  background-color: #edf2f5;
}
</style>