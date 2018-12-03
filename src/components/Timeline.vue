<template>
  <div class="container-fluid">
    <div class="row-fluid">
      <div class="col">
        <div class="page-header">
          <h1>{{clientName.firstName + "'s "}}Journey Timeline</h1>
        </div>
        <div style="display:inline-block;width:100%;overflow-y:auto;">
          <div style="display:inline-block;width:100%;overflow-y:auto;">
            <ol class="timeline timeline-horizontal">
              <!-- List Items Iterated -->
              <li class="timeline-item" v-for="event in events" :key="event">
                <div class="timeline-badge primary">
                  <i class="glyphicon glyphicon-check"></i>
                </div>
                <div class="timeline-panel">
                  <div class="timeline-heading">
                    <h4 class="timeline-title">{{ event.title }}</h4>
                    <p>
                      <small class="text-muted">
                        <i class="glyphicon glyphicon-time"></i>
                        {{event.time}}
                      </small>
                    </p>
                  </div>
                  <div class="timeline-body">{{event.description}}</div>
                </div>
              </li>
            </ol>
          </div>
        </div>
      </div>
      <div class="row-fluid">
        <div class="col-lg-12">
          <form class="form-horizontal" v-on:submit.prevent="addEvent">
            <fieldset>
              <!-- Form Name -->
              <legend>Add Milestone</legend>

              <!-- Text input-->
              <div class="form-group">
                <label class="col-md-4 control-label" for="textinput">Event Name</label>
                <div class="col-md-4">
                  <input
                    v-model="events.title"
                    id="textinput"
                    name="textinput"
                    type="text"
                    class="form-control input-md"
                  >
                </div>
              </div>

              <!-- Text input-->
              <div class="form-group">
                <label class="col-md-4 control-label" for="textinput">Year</label>
                <div class="col-md-4">
                  <input
                    v-model="events.time"
                    id="textinput"
                    name="textinput"
                    type="text"
                    class="form-control input-md"
                  >
                </div>
              </div>

              <!-- Textarea -->
              <div class="form-group">
                <label class="col-md-4 control-label" for="textarea">Description</label>
                <div class="col-md-4">
                  <textarea
                    v-model="events.description"
                    class="form-control"
                    id="textarea"
                    name="textarea"
                  ></textarea>
                </div>
              </div>

              <!-- Button (Double) -->
              <div class="form-group">
                <div class="col-md-8">
                  <button
                    id="button1id"
                    name="button1id"
                    class="btn btn-success"
                    action="submit"
                  >Add Milestone</button>
                </div>
              </div>
            </fieldset>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Timeline",
  data() {
    return {
      clientName: {
        firstName: "Dan",
        lastName: "Malone"
      },
      events: [
        {
          title: "Became a client",
          time: "2016",
          description:
            "togen cray. Lomo 90's banjo blue bottle blog forage brunch, occupy copper mug. Normcore lyft meh single-origin coffee humblebrag craft beer, keytar flexitarian cred kinfolk."
        },
        {
          title: "Married Kate",
          time: "2018",
          description:
            "hella woke adaptogen cray. Lomo 90's banjo blue bottle blog forage brunch, occupy copper mug. Normcore lyft meh single-origin coffee humblebrag craft beer, keytar flexitarian cred kinfolk."
        },
        {
          title: "Completed Estate Plan",
          time: "2019",
          description:
            " Next level distillery freegan PBR&B, sriracha godard unicorn ethical messenger bag leggings. Brunch butcher poke retro mixtape kombucha. Synth meh lomo deep v messenger bag crucifix 8-bit tousled. "
        },
        {
          title: "Bought First Home",
          time: "2020",
          description:
            "Lyft live-edge chillwave literally ethical kitsch. Artisan sriracha fanny pack, small batch air plant prism 90's four loko iceland chillwave sustainable. Selvage hexagon synth squid pour-over scenester. Godard master cleanse vape art party normcore raw denim fingerstache offal chillwave."
        },
        {
          title: "First Life Insurance Policy",
          time: "2021",
          description:
            "Selvage hexagon synth squid pour-over scenester. Godard master cleanse vape art party normcore raw denim fingerstache offal chillwave."
        },
        {
          title: "Net Worth: $500,000",
          time: "2021",
          description:
            "Selvage hexagon synth squid pour-over scenester. Godard master cleanse vape art party normcore raw denim fingerstache offal chillwave."
        }
      ]
    };
  },
  methods: {
    addEvent: function() {
      this.events.push({
        time: this.events.time,
        title: this.events.title,
        description: this.events.description
      });
    },
    resetForm: function() {
      this.$refs.events.title = "dsadsa";
    }
  },
  computed: {}
};
</script>


<style>
//* Timeline */
.timeline,
.timeline-horizontal {
  list-style: none;
  padding: 20px;
  position: relative;
}
.timeline:before {
  top: 40px;
  bottom: 0;
  position: absolute;
  content: " ";
  width: 3px;
  background-color: #eeeeee;
  left: 50%;
  margin-left: -1.5px;
}
.timeline .timeline-item {
  margin-bottom: 20px;
  margin-top: 20px;
  position: relative;
}
.timeline .timeline-item:before,
.timeline .timeline-item:after {
  content: "";
  display: table;
}
.timeline .timeline-item:after {
  clear: both;
}
.timeline .timeline-item .timeline-badge {
  color: #fff;
  width: 54px;
  height: 54px;
  line-height: 52px;
  font-size: 22px;
  text-align: center;
  position: absolute;
  top: 18px;
  left: 50%;
  margin-left: -25px;
  background-color: #7c7c7c;
  border: 3px solid #ffffff;
  z-index: 100;
  border-top-right-radius: 50%;
  border-top-left-radius: 50%;
  border-bottom-right-radius: 50%;
  border-bottom-left-radius: 50%;
}
.timeline .timeline-item .timeline-badge i,
.timeline .timeline-item .timeline-badge .fa,
.timeline .timeline-item .timeline-badge .glyphicon {
  top: 2px;
  left: 0px;
}
.timeline .timeline-item .timeline-badge.primary {
  background-color: #1f9eba;
}
.timeline .timeline-item .timeline-badge.info {
  background-color: #5bc0de;
}
.timeline .timeline-item .timeline-badge.success {
  background-color: #59ba1f;
}
.timeline .timeline-item .timeline-badge.warning {
  background-color: #d1bd10;
}
.timeline .timeline-item .timeline-badge.danger {
  background-color: #ba1f1f;
}
.timeline .timeline-item .timeline-panel {
  position: relative;
  margin-top: 50px;
  width: 46%;
  float: left;
  right: 16px;
  border: 1px solid #c0c0c0;
  background: #ffffff;
  border-radius: 2px;
  padding: 20px;
  -webkit-box-shadow: 0 1px 6px rgba(0, 0, 0, 0.175);
  box-shadow: 0 1px 6px rgba(0, 0, 0, 0.175);
}
.timeline .timeline-item .timeline-panel:before {
  position: absolute;
  top: 26px;
  right: -16px;
  display: inline-block;
  border-top: 16px solid transparent;
  border-left: 16px solid #c0c0c0;
  border-right: 0 solid #c0c0c0;
  border-bottom: 16px solid transparent;
  content: " ";
}
.timeline .timeline-item .timeline-panel .timeline-title {
  margin-top: 0;
  color: inherit;
}
.timeline .timeline-item .timeline-panel .timeline-body > p,
.timeline .timeline-item .timeline-panel .timeline-body > ul {
  margin-bottom: 0;
}
.timeline .timeline-item .timeline-panel .timeline-body > p + p {
  margin-top: 5px;
}
.timeline .timeline-item:last-child:nth-child(even) {
  float: right;
}
.timeline .timeline-item:nth-child(even) .timeline-panel {
  float: right;
  left: 16px;
}
.timeline .timeline-item:nth-child(even) .timeline-panel:before {
  border-left-width: 0;
  border-right-width: 14px;
  left: -14px;
  right: auto;
}
.timeline-horizontal {
  list-style: none;
  position: relative;
  padding: 20px 0px 20px 0px;
  display: inline-block;
}
.timeline-horizontal:before {
  height: 3px;
  top: auto;
  bottom: 26px;
  left: 56px;
  right: 0;
  width: 100%;
  margin-bottom: 20px;
}
.timeline-horizontal .timeline-item {
  display: table-cell;
  height: 280px;
  width: 20%;
  min-width: 320px;
  float: none !important;
  padding-left: 0px;
  padding-right: 20px;
  margin: 0 auto;
  vertical-align: bottom;
}
.timeline-horizontal .timeline-item .timeline-panel {
  top: auto;
  bottom: 64px;
  display: inline-block;
  float: none !important;
  left: 0 !important;
  right: 0 !important;
  width: 100%;
  margin-bottom: 20px;
}
.timeline-horizontal .timeline-item .timeline-panel:before {
  top: auto;
  bottom: -16px;
  left: 28px !important;
  right: auto;
  border-right: 16px solid transparent !important;
  border-top: 16px solid #c0c0c0 !important;
  border-bottom: 0 solid #c0c0c0 !important;
  border-left: 16px solid transparent !important;
}
.timeline-horizontal .timeline-item:before,
.timeline-horizontal .timeline-item:after {
  display: none;
}
.timeline-horizontal .timeline-item .timeline-badge {
  top: auto;
  bottom: 0px;
  left: 43px;
}
</style>

