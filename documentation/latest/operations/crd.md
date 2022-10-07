---
title: "CRD reference"
layout: documentation
weight: 1
---




### management.project-flotta.io/v1alpha1 {#managementproject-flottaiov1alpha1}


Resource Types:

- [EdgeConfig](#edgeconfig)

- [EdgeDevice](#edgedevice)

- [EdgeDeviceSet](#edgedeviceset)

- [EdgeDeviceSignedRequest](#edgedevicesignedrequest)

- [EdgeWorkload](#edgeworkload)

- [PlaybookExecution](#playbookexecution)




### EdgeConfig {#edgeconfig}
<sup><sup>[↩ Parent](#managementproject-flottaiov1alpha1 )</sup></sup>






EdgeConfig is the Schema for the edgeconfigs API
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr>
        <td><b>apiVersion</b></td>
        <td>string</td>
        <td>management.project-flotta.io/v1alpha1</td>
        <td>true</td>
        </tr>
        <tr>
        <td><b>kind</b></td>
        <td>string</td>
        <td>EdgeConfig</td>
        <td>true</td>
        </tr>
        <tr>
        <td><b><a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#objectmeta-v1-meta">metadata</a></b></td>
        <td>object</td>
        <td>Refer to the Kubernetes API documentation for the fields of the `metadata` field.</td>
        <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeconfigspec">spec</a></b></td>
          <td>object</td>
          <td>
            EdgeConfigSpec defines the desired state of EdgeConfig<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeconfigstatus">status</a></b></td>
          <td>object</td>
          <td>
            EdgeConfigStatus defines the observed state of EdgeConfig<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeConfig.spec {#edgeconfigspec}
<sup><sup>[↩ Parent](#edgeconfig)</sup></sup>



EdgeConfigSpec defines the desired state of EdgeConfig
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeconfigspecedgeplaybook">edgePlaybook</a></b></td>
          <td>object</td>
          <td>
            Definition of the custom playbook workload to execute<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeConfig.spec.edgePlaybook {#edgeconfigspecedgeplaybook}
<sup><sup>[↩ Parent](#edgeconfigspec)</sup></sup>



Definition of the custom playbook workload to execute
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeconfigspecedgeplaybookplaybooksindex">playbooks</a></b></td>
          <td>[]object</td>
          <td>
            The ansible&#39;s playbooks list. The first element is the playbook with the highest priority.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>user</b></td>
          <td>string</td>
          <td>
            username who execute the playbook<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeConfig.spec.edgePlaybook.playbooks[index] {#edgeconfigspecedgeplaybookplaybooksindex}
<sup><sup>[↩ Parent](#edgeconfigspecedgeplaybook)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>content</b></td>
          <td>string</td>
          <td>
            Playbook content<br/>
            <br/>
              <i>Format</i>: byte<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeconfigspecedgeplaybookplaybooksindexansibleoptions">ansibleOptions</a></b></td>
          <td>object</td>
          <td>
            the ansible&#39;s playbook options for the playbook<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>executionStrategy</b></td>
          <td>string</td>
          <td>
            Execution strategy for the playbook<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeconfigspecedgeplaybookplaybooksindexprivilegeescalationoptions">privilegeEscalationOptions</a></b></td>
          <td>object</td>
          <td>
            the ansible&#39;s playbook privilege escalation options for the playbook<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeconfigspecedgeplaybookplaybooksindexrequiredprivilegelevel">requiredPrivilegeLevel</a></b></td>
          <td>object</td>
          <td>
            The required privelege level necessary to execute the playbook<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>timeoutSeconds</b></td>
          <td>integer</td>
          <td>
            The connection timeout on ansible-playbook<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeConfig.spec.edgePlaybook.playbooks[index].ansibleOptions {#edgeconfigspecedgeplaybookplaybooksindexansibleoptions}
<sup><sup>[↩ Parent](#edgeconfigspecedgeplaybookplaybooksindex)</sup></sup>



the ansible&#39;s playbook options for the playbook
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>check</b></td>
          <td>boolean</td>
          <td>
            don&#39;t make any changes; instead, try to predict some of the changes that may occur<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeConfig.spec.edgePlaybook.playbooks[index].privilegeEscalationOptions {#edgeconfigspecedgeplaybookplaybooksindexprivilegeescalationoptions}
<sup><sup>[↩ Parent](#edgeconfigspecedgeplaybookplaybooksindex)</sup></sup>



the ansible&#39;s playbook privilege escalation options for the playbook
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>become</b></td>
          <td>boolean</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>becomeMethod</b></td>
          <td>enum</td>
          <td>
            <br/>
            <br/>
              <i>Enum</i>: sudo, su<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>becomeUser</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeConfig.spec.edgePlaybook.playbooks[index].requiredPrivilegeLevel {#edgeconfigspecedgeplaybookplaybooksindexrequiredprivilegelevel}
<sup><sup>[↩ Parent](#edgeconfigspecedgeplaybookplaybooksindex)</sup></sup>



The required privelege level necessary to execute the playbook
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>capAdd</b></td>
          <td>[]integer</td>
          <td>
            See https://man7.org/linux/man-pages/man7/capabilities.7.html<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>capDrop</b></td>
          <td>[]integer</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeConfig.status {#edgeconfigstatus}
<sup><sup>[↩ Parent](#edgeconfig)</sup></sup>



EdgeConfigStatus defines the observed state of EdgeConfig
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeconfigstatusedgeplaybookstatus">edgePlaybookStatus</a></b></td>
          <td>object</td>
          <td>
            EdgePlaybookStatus defines the observed state of EdgePlaybook<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeConfig.status.edgePlaybookStatus {#edgeconfigstatusedgeplaybookstatus}
<sup><sup>[↩ Parent](#edgeconfigstatus)</sup></sup>



EdgePlaybookStatus defines the observed state of EdgePlaybook
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeconfigstatusedgeplaybookstatusconditionsindex">conditions</a></b></td>
          <td>[]object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeConfig.status.edgePlaybookStatus.conditions[index] {#edgeconfigstatusedgeplaybookstatusconditionsindex}
<sup><sup>[↩ Parent](#edgeconfigstatusedgeplaybookstatus)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>status</b></td>
          <td>string</td>
          <td>
            Indicates whether that condition is applicable, with possible values &#34;True&#34;, &#34;False&#34;, or &#34;Unknown&#34; The absence of a condition should be interpreted the same as Unknown<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>type</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>lastTransitionTime</b></td>
          <td>string</td>
          <td>
            <br/>
            <br/>
              <i>Format</i>: date-time<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>message</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>reason</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>

### EdgeDevice {#edgedevice}
<sup><sup>[↩ Parent](#managementproject-flottaiov1alpha1 )</sup></sup>






EdgeDevice is the Schema for the edgedevices API
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr>
        <td><b>apiVersion</b></td>
        <td>string</td>
        <td>management.project-flotta.io/v1alpha1</td>
        <td>true</td>
        </tr>
        <tr>
        <td><b>kind</b></td>
        <td>string</td>
        <td>EdgeDevice</td>
        <td>true</td>
        </tr>
        <tr>
        <td><b><a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#objectmeta-v1-meta">metadata</a></b></td>
        <td>object</td>
        <td>Refer to the Kubernetes API documentation for the fields of the `metadata` field.</td>
        <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicespec">spec</a></b></td>
          <td>object</td>
          <td>
            EdgeDeviceSpec defines the desired state of EdgeDevice<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicestatus">status</a></b></td>
          <td>object</td>
          <td>
            EdgeDeviceStatus defines the observed state of EdgeDevice<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.spec {#edgedevicespec}
<sup><sup>[↩ Parent](#edgedevice)</sup></sup>



EdgeDeviceSpec defines the desired state of EdgeDevice
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgedevicespecheartbeat">heartbeat</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicespeclogcollectionkey">logCollection</a></b></td>
          <td>map[string]object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicespecmetrics">metrics</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicespecmountsindex">mounts</a></b></td>
          <td>[]object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicespecosinformation">osInformation</a></b></td>
          <td>object</td>
          <td>
            OsInformation carries information about commit ID of the OS Image deployed to the device<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>requestTime</b></td>
          <td>string</td>
          <td>
            RequestTime is the time of device registration request<br/>
            <br/>
              <i>Format</i>: date-time<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicespecstorage">storage</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.spec.heartbeat {#edgedevicespecheartbeat}
<sup><sup>[↩ Parent](#edgedevicespec)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgedevicespecheartbeathardwareprofile">hardwareProfile</a></b></td>
          <td>object</td>
          <td>
            hardware profile<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>periodSeconds</b></td>
          <td>integer</td>
          <td>
            period seconds<br/>
            <br/>
              <i>Format</i>: int64<br/>
              <i>Minimum</i>: 1<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.spec.heartbeat.hardwareProfile {#edgedevicespecheartbeathardwareprofile}
<sup><sup>[↩ Parent](#edgedevicespecheartbeat)</sup></sup>



hardware profile
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>include</b></td>
          <td>boolean</td>
          <td>
            include<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>scope</b></td>
          <td>string</td>
          <td>
            scope Enum: [full delta]<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.spec.logCollection[key] {#edgedevicespeclogcollectionkey}
<sup><sup>[↩ Parent](#edgedevicespec)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>bufferSize</b></td>
          <td>integer</td>
          <td>
            <br/>
            <br/>
              <i>Format</i>: int32<br/>
              <i>Default</i>: 12<br/>
              <i>Minimum</i>: 1<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>kind</b></td>
          <td>enum</td>
          <td>
            Kind is the type of log collection to be used<br/>
            <br/>
              <i>Enum</i>: syslog<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicespeclogcollectionkeysyslogconfig">syslogConfig</a></b></td>
          <td>object</td>
          <td>
            SyslogConfig is the pointer to the configMap to be used to load the config<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.spec.logCollection[key].syslogConfig {#edgedevicespeclogcollectionkeysyslogconfig}
<sup><sup>[↩ Parent](#edgedevicespeclogcollectionkey)</sup></sup>



SyslogConfig is the pointer to the configMap to be used to load the config
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.spec.metrics {#edgedevicespecmetrics}
<sup><sup>[↩ Parent](#edgedevicespec)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgedevicespecmetricsdatatransfer">dataTransfer</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicespecmetricsreceiverconfiguration">receiverConfiguration</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicespecmetricsretention">retention</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicespecmetricssystem">system</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.spec.metrics.dataTransfer {#edgedevicespecmetricsdatatransfer}
<sup><sup>[↩ Parent](#edgedevicespecmetrics)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgedevicespecmetricsdatatransferallowlist">allowList</a></b></td>
          <td>object</td>
          <td>
            AllowList defines name of a ConfigMap containing list of system metrics that should be scraped<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>disabled</b></td>
          <td>boolean</td>
          <td>
            Disabled when set to true instructs the device to turn off system metrics collection<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>interval</b></td>
          <td>integer</td>
          <td>
            Interval(in seconds) to scrape system metrics.<br/>
            <br/>
              <i>Format</i>: int32<br/>
              <i>Default</i>: 60<br/>
              <i>Minimum</i>: 0<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.spec.metrics.dataTransfer.allowList {#edgedevicespecmetricsdatatransferallowlist}
<sup><sup>[↩ Parent](#edgedevicespecmetricsdatatransfer)</sup></sup>



AllowList defines name of a ConfigMap containing list of system metrics that should be scraped
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.spec.metrics.receiverConfiguration {#edgedevicespecmetricsreceiverconfiguration}
<sup><sup>[↩ Parent](#edgedevicespecmetrics)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>caSecretName</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>requestNumSamples</b></td>
          <td>integer</td>
          <td>
            <br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>timeoutSeconds</b></td>
          <td>integer</td>
          <td>
            <br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>url</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.spec.metrics.retention {#edgedevicespecmetricsretention}
<sup><sup>[↩ Parent](#edgedevicespecmetrics)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>maxHours</b></td>
          <td>integer</td>
          <td>
            MaxHours specifies how long should persisted metrics be stored on the device disk<br/>
            <br/>
              <i>Format</i>: int32<br/>
              <i>Minimum</i>: 0<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>maxMiB</b></td>
          <td>integer</td>
          <td>
            MaxMiB specifies how much disk space should be used for storing persisted metrics on the device<br/>
            <br/>
              <i>Format</i>: int32<br/>
              <i>Minimum</i>: 0<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.spec.metrics.system {#edgedevicespecmetricssystem}
<sup><sup>[↩ Parent](#edgedevicespecmetrics)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgedevicespecmetricssystemallowlist">allowList</a></b></td>
          <td>object</td>
          <td>
            AllowList defines name of a ConfigMap containing list of system metrics that should be scraped<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>disabled</b></td>
          <td>boolean</td>
          <td>
            Disabled when set to true instructs the device to turn off system metrics collection<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>interval</b></td>
          <td>integer</td>
          <td>
            Interval(in seconds) to scrape system metrics.<br/>
            <br/>
              <i>Format</i>: int32<br/>
              <i>Default</i>: 60<br/>
              <i>Minimum</i>: 0<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.spec.metrics.system.allowList {#edgedevicespecmetricssystemallowlist}
<sup><sup>[↩ Parent](#edgedevicespecmetricssystem)</sup></sup>



AllowList defines name of a ConfigMap containing list of system metrics that should be scraped
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.spec.mounts[index] {#edgedevicespecmountsindex}
<sup><sup>[↩ Parent](#edgedevicespec)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>device</b></td>
          <td>string</td>
          <td>
            Device path to be mounted<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>folder</b></td>
          <td>string</td>
          <td>
            Destination directory path<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>options</b></td>
          <td>string</td>
          <td>
            Mount options (i.e. rw, suid, dev)<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>type</b></td>
          <td>string</td>
          <td>
            Mount type: (i.e ext4)<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.spec.osInformation {#edgedevicespecosinformation}
<sup><sup>[↩ Parent](#edgedevicespec)</sup></sup>



OsInformation carries information about commit ID of the OS Image deployed to the device
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>automaticallyUpgrade</b></td>
          <td>boolean</td>
          <td>
            Automatically upgrade the OS image<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>commitID</b></td>
          <td>string</td>
          <td>
            CommitID carries information about commit of the OS Image<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>hostedObjectsURL</b></td>
          <td>string</td>
          <td>
            HostedObjectsURL carries the URL of the hosted commits web server<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.spec.storage {#edgedevicespecstorage}
<sup><sup>[↩ Parent](#edgedevicespec)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgedevicespecstorages3">s3</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.spec.storage.s3 {#edgedevicespecstorages3}
<sup><sup>[↩ Parent](#edgedevicespecstorage)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>configMapName</b></td>
          <td>string</td>
          <td>
            configMap name<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>createOBC</b></td>
          <td>boolean</td>
          <td>
            createOBC. if the configuration above is empty and this bool is true then create OBC<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>secretName</b></td>
          <td>string</td>
          <td>
            secret name<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.status {#edgedevicestatus}
<sup><sup>[↩ Parent](#edgedevice)</sup></sup>



EdgeDeviceStatus defines the observed state of EdgeDevice
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgedevicestatusplaybookexecindex">PlaybookExec</a></b></td>
          <td>[]object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>dataObc</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicestatushardware">hardware</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>lastSyncedResourceVersion</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>phase</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicestatusupgradeinformation">upgradeInformation</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicestatusworkloadsindex">workloads</a></b></td>
          <td>[]object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.status.PlaybookExec[index] {#edgedevicestatusplaybookexecindex}
<sup><sup>[↩ Parent](#edgedevicestatus)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicestatusplaybookexecindexplaybookexecutionstatus">PlaybookExecutionStatus</a></b></td>
          <td>object</td>
          <td>
            PlaybookExecutionStatus defines the observed state of PlaybookExecution<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.status.PlaybookExec[index].PlaybookExecutionStatus {#edgedevicestatusplaybookexecindexplaybookexecutionstatus}
<sup><sup>[↩ Parent](#edgedevicestatusplaybookexecindex)</sup></sup>



PlaybookExecutionStatus defines the observed state of PlaybookExecution
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgedevicestatusplaybookexecindexplaybookexecutionstatusconditionsindex">conditions</a></b></td>
          <td>[]object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.status.PlaybookExec[index].PlaybookExecutionStatus.conditions[index] {#edgedevicestatusplaybookexecindexplaybookexecutionstatusconditionsindex}
<sup><sup>[↩ Parent](#edgedevicestatusplaybookexecindexplaybookexecutionstatus)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>status</b></td>
          <td>string</td>
          <td>
            Indicates whether that condition is applicable, with possible values &#34;True&#34;, &#34;False&#34;, or &#34;Unknown&#34; The absence of a condition should be interpreted the same as Unknown<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>type</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>lastTransitionTime</b></td>
          <td>string</td>
          <td>
            <br/>
            <br/>
              <i>Format</i>: date-time<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>message</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>reason</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.status.hardware {#edgedevicestatushardware}
<sup><sup>[↩ Parent](#edgedevicestatus)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgedevicestatushardwaredisksindex">disks</a></b></td>
          <td>[]object</td>
          <td>
            disks<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicestatushardwaregpusindex">gpus</a></b></td>
          <td>[]object</td>
          <td>
            gpus<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicestatushardwareinterfacesindex">interfaces</a></b></td>
          <td>[]object</td>
          <td>
            interfaces<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicestatushardwareboot">boot</a></b></td>
          <td>object</td>
          <td>
            boot<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicestatushardwarecpu">cpu</a></b></td>
          <td>object</td>
          <td>
            cpu<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicestatushardwarehostdevicesindex">hostDevices</a></b></td>
          <td>[]object</td>
          <td>
            list of devices present on the edgedevice<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>hostname</b></td>
          <td>string</td>
          <td>
            hostname<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicestatushardwarememory">memory</a></b></td>
          <td>object</td>
          <td>
            memory<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicestatushardwaremountsindex">mounts</a></b></td>
          <td>[]object</td>
          <td>
            list of all mounts found on edgedevice<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicestatushardwaresystemvendor">systemVendor</a></b></td>
          <td>object</td>
          <td>
            system vendor<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.status.hardware.disks[index] {#edgedevicestatushardwaredisksindex}
<sup><sup>[↩ Parent](#edgedevicestatushardware)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>bootable</b></td>
          <td>boolean</td>
          <td>
            bootable<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>byId</b></td>
          <td>string</td>
          <td>
            by-id is the World Wide Number of the device which guaranteed to be unique for every storage device<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>byPath</b></td>
          <td>string</td>
          <td>
            by-path is the shortest physical path to the device<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>driveType</b></td>
          <td>string</td>
          <td>
            drive type<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>hctl</b></td>
          <td>string</td>
          <td>
            hctl<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>id</b></td>
          <td>string</td>
          <td>
            Determine the disk&#39;s unique identifier which is the by-id field if it exists and fallback to the by-path field otherwise<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicestatushardwaredisksindexioperf">ioPerf</a></b></td>
          <td>object</td>
          <td>
            io perf<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>isInstallationMedia</b></td>
          <td>boolean</td>
          <td>
            Whether the disk appears to be an installation media or not<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>model</b></td>
          <td>string</td>
          <td>
            model<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            name<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            path<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>serial</b></td>
          <td>string</td>
          <td>
            serial<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>sizeBytes</b></td>
          <td>integer</td>
          <td>
            size bytes<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>smart</b></td>
          <td>string</td>
          <td>
            smart<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>vendor</b></td>
          <td>string</td>
          <td>
            vendor<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>wwn</b></td>
          <td>string</td>
          <td>
            wwn<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.status.hardware.disks[index].ioPerf {#edgedevicestatushardwaredisksindexioperf}
<sup><sup>[↩ Parent](#edgedevicestatushardwaredisksindex)</sup></sup>



io perf
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>syncDuration</b></td>
          <td>integer</td>
          <td>
            99th percentile of fsync duration in milliseconds<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.status.hardware.gpus[index] {#edgedevicestatushardwaregpusindex}
<sup><sup>[↩ Parent](#edgedevicestatushardware)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>address</b></td>
          <td>string</td>
          <td>
            Device address (for example &#34;0000:00:02.0&#34;)<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>deviceId</b></td>
          <td>string</td>
          <td>
            ID of the device (for example &#34;3ea0&#34;)<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Product name of the device (for example &#34;UHD Graphics 620 (Whiskey Lake)&#34;)<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>vendor</b></td>
          <td>string</td>
          <td>
            The name of the device vendor (for example &#34;Intel Corporation&#34;)<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>vendorId</b></td>
          <td>string</td>
          <td>
            ID of the vendor (for example &#34;8086&#34;)<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.status.hardware.interfaces[index] {#edgedevicestatushardwareinterfacesindex}
<sup><sup>[↩ Parent](#edgedevicestatushardware)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>flags</b></td>
          <td>[]string</td>
          <td>
            flags<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>biosdevname</b></td>
          <td>string</td>
          <td>
            biosdevname<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>clientId</b></td>
          <td>string</td>
          <td>
            client id<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>hasCarrier</b></td>
          <td>boolean</td>
          <td>
            has carrier<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>ipv4Addresses</b></td>
          <td>[]string</td>
          <td>
            ipv4 addresses<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>ipv6Addresses</b></td>
          <td>[]string</td>
          <td>
            ipv6 addresses<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>macAddress</b></td>
          <td>string</td>
          <td>
            mac address<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>mtu</b></td>
          <td>integer</td>
          <td>
            mtu<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            name<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>product</b></td>
          <td>string</td>
          <td>
            product<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>speedMbps</b></td>
          <td>integer</td>
          <td>
            speed mbps<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>vendor</b></td>
          <td>string</td>
          <td>
            vendor<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.status.hardware.boot {#edgedevicestatushardwareboot}
<sup><sup>[↩ Parent](#edgedevicestatushardware)</sup></sup>



boot
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>currentBootMode</b></td>
          <td>string</td>
          <td>
            current boot mode<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>pxeInterface</b></td>
          <td>string</td>
          <td>
            pxe interface<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.status.hardware.cpu {#edgedevicestatushardwarecpu}
<sup><sup>[↩ Parent](#edgedevicestatushardware)</sup></sup>



cpu
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>flags</b></td>
          <td>[]string</td>
          <td>
            flags<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>architecture</b></td>
          <td>string</td>
          <td>
            architecture<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>count</b></td>
          <td>integer</td>
          <td>
            count<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>frequency</b></td>
          <td>string</td>
          <td>
            frequency<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>modelName</b></td>
          <td>string</td>
          <td>
            model name<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.status.hardware.hostDevices[index] {#edgedevicestatushardwarehostdevicesindex}
<sup><sup>[↩ Parent](#edgedevicestatushardware)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>deviceType</b></td>
          <td>string</td>
          <td>
            Device type block or character<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>group</b></td>
          <td>integer</td>
          <td>
            group id<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>major</b></td>
          <td>integer</td>
          <td>
            Major ID identifying the class of the device<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>minor</b></td>
          <td>integer</td>
          <td>
            Minor ID identifying the instance of the device in the class<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>owner</b></td>
          <td>integer</td>
          <td>
            owner id<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            path of the device (i.e. /dev/loop)<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.status.hardware.memory {#edgedevicestatushardwarememory}
<sup><sup>[↩ Parent](#edgedevicestatushardware)</sup></sup>



memory
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>physicalBytes</b></td>
          <td>integer</td>
          <td>
            physical bytes<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>usableBytes</b></td>
          <td>integer</td>
          <td>
            usable bytes<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.status.hardware.mounts[index] {#edgedevicestatushardwaremountsindex}
<sup><sup>[↩ Parent](#edgedevicestatushardware)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>device</b></td>
          <td>string</td>
          <td>
            Device path to be mounted<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>folder</b></td>
          <td>string</td>
          <td>
            Destination directory path<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>options</b></td>
          <td>string</td>
          <td>
            Mount options (i.e. rw, suid, dev)<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>type</b></td>
          <td>string</td>
          <td>
            Mount type: (i.e ext4)<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.status.hardware.systemVendor {#edgedevicestatushardwaresystemvendor}
<sup><sup>[↩ Parent](#edgedevicestatushardware)</sup></sup>



system vendor
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>manufacturer</b></td>
          <td>string</td>
          <td>
            manufacturer<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>productName</b></td>
          <td>string</td>
          <td>
            product name<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>serialNumber</b></td>
          <td>string</td>
          <td>
            serial number<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>virtual</b></td>
          <td>boolean</td>
          <td>
            Whether the machine appears to be a virtual machine or not<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.status.upgradeInformation {#edgedevicestatusupgradeinformation}
<sup><sup>[↩ Parent](#edgedevicestatus)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>currentCommitID</b></td>
          <td>string</td>
          <td>
            Current commit<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>lastUpgradeStatus</b></td>
          <td>string</td>
          <td>
            last upgrade status<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>lastUpgradeTime</b></td>
          <td>string</td>
          <td>
            last upgrade time<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDevice.status.workloads[index] {#edgedevicestatusworkloadsindex}
<sup><sup>[↩ Parent](#edgedevicestatus)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>lastDataUpload</b></td>
          <td>string</td>
          <td>
            <br/>
            <br/>
              <i>Format</i>: date-time<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>lastTransitionTime</b></td>
          <td>string</td>
          <td>
            <br/>
            <br/>
              <i>Format</i>: date-time<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>phase</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>

### EdgeDeviceSet {#edgedeviceset}
<sup><sup>[↩ Parent](#managementproject-flottaiov1alpha1 )</sup></sup>






EdgeDeviceSet is the Schema for the edgedevicesets API
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr>
        <td><b>apiVersion</b></td>
        <td>string</td>
        <td>management.project-flotta.io/v1alpha1</td>
        <td>true</td>
        </tr>
        <tr>
        <td><b>kind</b></td>
        <td>string</td>
        <td>EdgeDeviceSet</td>
        <td>true</td>
        </tr>
        <tr>
        <td><b><a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#objectmeta-v1-meta">metadata</a></b></td>
        <td>object</td>
        <td>Refer to the Kubernetes API documentation for the fields of the `metadata` field.</td>
        <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesetspec">spec</a></b></td>
          <td>object</td>
          <td>
            EdgeDeviceSetSpec defines the desired state of EdgeDeviceSet<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>status</b></td>
          <td>object</td>
          <td>
            EdgeDeviceSetStatus defines the observed state of EdgeDeviceSet<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSet.spec {#edgedevicesetspec}
<sup><sup>[↩ Parent](#edgedeviceset)</sup></sup>



EdgeDeviceSetSpec defines the desired state of EdgeDeviceSet
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgedevicesetspecheartbeat">heartbeat</a></b></td>
          <td>object</td>
          <td>
            Heartbeat contains heartbeat messages configuration<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesetspeclogcollectionkey">logCollection</a></b></td>
          <td>map[string]object</td>
          <td>
            LogCollection contains configuration for device log collection<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesetspecmetrics">metrics</a></b></td>
          <td>object</td>
          <td>
            Metrics contain metric collection and upload configuration<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesetspecmountsindex">mounts</a></b></td>
          <td>[]object</td>
          <td>
            Mounts contains mount configuration<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesetspecosinformation">osInformation</a></b></td>
          <td>object</td>
          <td>
            OsInformation carries information about commit ID of the OS Image deployed to the device<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesetspecstorage">storage</a></b></td>
          <td>object</td>
          <td>
            Storage contains data upload configuration<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSet.spec.heartbeat {#edgedevicesetspecheartbeat}
<sup><sup>[↩ Parent](#edgedevicesetspec)</sup></sup>



Heartbeat contains heartbeat messages configuration
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgedevicesetspecheartbeathardwareprofile">hardwareProfile</a></b></td>
          <td>object</td>
          <td>
            hardware profile<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>periodSeconds</b></td>
          <td>integer</td>
          <td>
            period seconds<br/>
            <br/>
              <i>Format</i>: int64<br/>
              <i>Minimum</i>: 1<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSet.spec.heartbeat.hardwareProfile {#edgedevicesetspecheartbeathardwareprofile}
<sup><sup>[↩ Parent](#edgedevicesetspecheartbeat)</sup></sup>



hardware profile
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>include</b></td>
          <td>boolean</td>
          <td>
            include<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>scope</b></td>
          <td>string</td>
          <td>
            scope Enum: [full delta]<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSet.spec.logCollection[key] {#edgedevicesetspeclogcollectionkey}
<sup><sup>[↩ Parent](#edgedevicesetspec)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>bufferSize</b></td>
          <td>integer</td>
          <td>
            <br/>
            <br/>
              <i>Format</i>: int32<br/>
              <i>Default</i>: 12<br/>
              <i>Minimum</i>: 1<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>kind</b></td>
          <td>enum</td>
          <td>
            Kind is the type of log collection to be used<br/>
            <br/>
              <i>Enum</i>: syslog<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesetspeclogcollectionkeysyslogconfig">syslogConfig</a></b></td>
          <td>object</td>
          <td>
            SyslogConfig is the pointer to the configMap to be used to load the config<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSet.spec.logCollection[key].syslogConfig {#edgedevicesetspeclogcollectionkeysyslogconfig}
<sup><sup>[↩ Parent](#edgedevicesetspeclogcollectionkey)</sup></sup>



SyslogConfig is the pointer to the configMap to be used to load the config
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSet.spec.metrics {#edgedevicesetspecmetrics}
<sup><sup>[↩ Parent](#edgedevicesetspec)</sup></sup>



Metrics contain metric collection and upload configuration
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgedevicesetspecmetricsdatatransfer">dataTransfer</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesetspecmetricsreceiverconfiguration">receiverConfiguration</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesetspecmetricsretention">retention</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesetspecmetricssystem">system</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSet.spec.metrics.dataTransfer {#edgedevicesetspecmetricsdatatransfer}
<sup><sup>[↩ Parent](#edgedevicesetspecmetrics)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgedevicesetspecmetricsdatatransferallowlist">allowList</a></b></td>
          <td>object</td>
          <td>
            AllowList defines name of a ConfigMap containing list of system metrics that should be scraped<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>disabled</b></td>
          <td>boolean</td>
          <td>
            Disabled when set to true instructs the device to turn off system metrics collection<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>interval</b></td>
          <td>integer</td>
          <td>
            Interval(in seconds) to scrape system metrics.<br/>
            <br/>
              <i>Format</i>: int32<br/>
              <i>Default</i>: 60<br/>
              <i>Minimum</i>: 0<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSet.spec.metrics.dataTransfer.allowList {#edgedevicesetspecmetricsdatatransferallowlist}
<sup><sup>[↩ Parent](#edgedevicesetspecmetricsdatatransfer)</sup></sup>



AllowList defines name of a ConfigMap containing list of system metrics that should be scraped
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSet.spec.metrics.receiverConfiguration {#edgedevicesetspecmetricsreceiverconfiguration}
<sup><sup>[↩ Parent](#edgedevicesetspecmetrics)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>caSecretName</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>requestNumSamples</b></td>
          <td>integer</td>
          <td>
            <br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>timeoutSeconds</b></td>
          <td>integer</td>
          <td>
            <br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>url</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSet.spec.metrics.retention {#edgedevicesetspecmetricsretention}
<sup><sup>[↩ Parent](#edgedevicesetspecmetrics)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>maxHours</b></td>
          <td>integer</td>
          <td>
            MaxHours specifies how long should persisted metrics be stored on the device disk<br/>
            <br/>
              <i>Format</i>: int32<br/>
              <i>Minimum</i>: 0<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>maxMiB</b></td>
          <td>integer</td>
          <td>
            MaxMiB specifies how much disk space should be used for storing persisted metrics on the device<br/>
            <br/>
              <i>Format</i>: int32<br/>
              <i>Minimum</i>: 0<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSet.spec.metrics.system {#edgedevicesetspecmetricssystem}
<sup><sup>[↩ Parent](#edgedevicesetspecmetrics)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgedevicesetspecmetricssystemallowlist">allowList</a></b></td>
          <td>object</td>
          <td>
            AllowList defines name of a ConfigMap containing list of system metrics that should be scraped<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>disabled</b></td>
          <td>boolean</td>
          <td>
            Disabled when set to true instructs the device to turn off system metrics collection<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>interval</b></td>
          <td>integer</td>
          <td>
            Interval(in seconds) to scrape system metrics.<br/>
            <br/>
              <i>Format</i>: int32<br/>
              <i>Default</i>: 60<br/>
              <i>Minimum</i>: 0<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSet.spec.metrics.system.allowList {#edgedevicesetspecmetricssystemallowlist}
<sup><sup>[↩ Parent](#edgedevicesetspecmetricssystem)</sup></sup>



AllowList defines name of a ConfigMap containing list of system metrics that should be scraped
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSet.spec.mounts[index] {#edgedevicesetspecmountsindex}
<sup><sup>[↩ Parent](#edgedevicesetspec)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>device</b></td>
          <td>string</td>
          <td>
            Device path to be mounted<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>folder</b></td>
          <td>string</td>
          <td>
            Destination directory path<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>options</b></td>
          <td>string</td>
          <td>
            Mount options (i.e. rw, suid, dev)<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>type</b></td>
          <td>string</td>
          <td>
            Mount type: (i.e ext4)<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSet.spec.osInformation {#edgedevicesetspecosinformation}
<sup><sup>[↩ Parent](#edgedevicesetspec)</sup></sup>



OsInformation carries information about commit ID of the OS Image deployed to the device
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>automaticallyUpgrade</b></td>
          <td>boolean</td>
          <td>
            Automatically upgrade the OS image<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>commitID</b></td>
          <td>string</td>
          <td>
            CommitID carries information about commit of the OS Image<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>hostedObjectsURL</b></td>
          <td>string</td>
          <td>
            HostedObjectsURL carries the URL of the hosted commits web server<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSet.spec.storage {#edgedevicesetspecstorage}
<sup><sup>[↩ Parent](#edgedevicesetspec)</sup></sup>



Storage contains data upload configuration
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgedevicesetspecstorages3">s3</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSet.spec.storage.s3 {#edgedevicesetspecstorages3}
<sup><sup>[↩ Parent](#edgedevicesetspecstorage)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>configMapName</b></td>
          <td>string</td>
          <td>
            configMap name<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>createOBC</b></td>
          <td>boolean</td>
          <td>
            createOBC. if the configuration above is empty and this bool is true then create OBC<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>secretName</b></td>
          <td>string</td>
          <td>
            secret name<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>

### EdgeDeviceSignedRequest {#edgedevicesignedrequest}
<sup><sup>[↩ Parent](#managementproject-flottaiov1alpha1 )</sup></sup>






EdgeDeviceSignedRequest is the Schema for the edgedevice enrolment options
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr>
        <td><b>apiVersion</b></td>
        <td>string</td>
        <td>management.project-flotta.io/v1alpha1</td>
        <td>true</td>
        </tr>
        <tr>
        <td><b>kind</b></td>
        <td>string</td>
        <td>EdgeDeviceSignedRequest</td>
        <td>true</td>
        </tr>
        <tr>
        <td><b><a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#objectmeta-v1-meta">metadata</a></b></td>
        <td>object</td>
        <td>Refer to the Kubernetes API documentation for the fields of the `metadata` field.</td>
        <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesignedrequestspec">spec</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesignedrequeststatus">status</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSignedRequest.spec {#edgedevicesignedrequestspec}
<sup><sup>[↩ Parent](#edgedevicesignedrequest)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>targetNamespace</b></td>
          <td>string</td>
          <td>
            TargetNamespace is the namespace where device will land<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>approved</b></td>
          <td>boolean</td>
          <td>
            Approved is set to true if the device should be approved to register<br/>
            <br/>
              <i>Default</i>: false<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesignedrequestspecfeatures">features</a></b></td>
          <td>object</td>
          <td>
            Features lists features that the registering edge device has<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>targetSet</b></td>
          <td>string</td>
          <td>
            TargetSet is set that edgedevice will use.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSignedRequest.spec.features {#edgedevicesignedrequestspecfeatures}
<sup><sup>[↩ Parent](#edgedevicesignedrequestspec)</sup></sup>



Features lists features that the registering edge device has
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgedevicesignedrequestspecfeatureshardware">hardware</a></b></td>
          <td>object</td>
          <td>
            Hardware defines the hardware that devices has<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>modelName</b></td>
          <td>string</td>
          <td>
            ModelName is the model name from the OS. The output of: cat /sys/firmware/devicetree/base/model<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSignedRequest.spec.features.hardware {#edgedevicesignedrequestspecfeatureshardware}
<sup><sup>[↩ Parent](#edgedevicesignedrequestspecfeatures)</sup></sup>



Hardware defines the hardware that devices has
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgedevicesignedrequestspecfeatureshardwaredisksindex">disks</a></b></td>
          <td>[]object</td>
          <td>
            disks<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesignedrequestspecfeatureshardwaregpusindex">gpus</a></b></td>
          <td>[]object</td>
          <td>
            gpus<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesignedrequestspecfeatureshardwareinterfacesindex">interfaces</a></b></td>
          <td>[]object</td>
          <td>
            interfaces<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesignedrequestspecfeatureshardwareboot">boot</a></b></td>
          <td>object</td>
          <td>
            boot<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesignedrequestspecfeatureshardwarecpu">cpu</a></b></td>
          <td>object</td>
          <td>
            cpu<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesignedrequestspecfeatureshardwarehostdevicesindex">hostDevices</a></b></td>
          <td>[]object</td>
          <td>
            list of devices present on the edgedevice<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>hostname</b></td>
          <td>string</td>
          <td>
            hostname<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesignedrequestspecfeatureshardwarememory">memory</a></b></td>
          <td>object</td>
          <td>
            memory<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesignedrequestspecfeatureshardwaremountsindex">mounts</a></b></td>
          <td>[]object</td>
          <td>
            list of all mounts found on edgedevice<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesignedrequestspecfeatureshardwaresystemvendor">systemVendor</a></b></td>
          <td>object</td>
          <td>
            system vendor<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSignedRequest.spec.features.hardware.disks[index] {#edgedevicesignedrequestspecfeatureshardwaredisksindex}
<sup><sup>[↩ Parent](#edgedevicesignedrequestspecfeatureshardware)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>bootable</b></td>
          <td>boolean</td>
          <td>
            bootable<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>byId</b></td>
          <td>string</td>
          <td>
            by-id is the World Wide Number of the device which guaranteed to be unique for every storage device<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>byPath</b></td>
          <td>string</td>
          <td>
            by-path is the shortest physical path to the device<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>driveType</b></td>
          <td>string</td>
          <td>
            drive type<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>hctl</b></td>
          <td>string</td>
          <td>
            hctl<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>id</b></td>
          <td>string</td>
          <td>
            Determine the disk&#39;s unique identifier which is the by-id field if it exists and fallback to the by-path field otherwise<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgedevicesignedrequestspecfeatureshardwaredisksindexioperf">ioPerf</a></b></td>
          <td>object</td>
          <td>
            io perf<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>isInstallationMedia</b></td>
          <td>boolean</td>
          <td>
            Whether the disk appears to be an installation media or not<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>model</b></td>
          <td>string</td>
          <td>
            model<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            name<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            path<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>serial</b></td>
          <td>string</td>
          <td>
            serial<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>sizeBytes</b></td>
          <td>integer</td>
          <td>
            size bytes<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>smart</b></td>
          <td>string</td>
          <td>
            smart<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>vendor</b></td>
          <td>string</td>
          <td>
            vendor<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>wwn</b></td>
          <td>string</td>
          <td>
            wwn<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSignedRequest.spec.features.hardware.disks[index].ioPerf {#edgedevicesignedrequestspecfeatureshardwaredisksindexioperf}
<sup><sup>[↩ Parent](#edgedevicesignedrequestspecfeatureshardwaredisksindex)</sup></sup>



io perf
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>syncDuration</b></td>
          <td>integer</td>
          <td>
            99th percentile of fsync duration in milliseconds<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSignedRequest.spec.features.hardware.gpus[index] {#edgedevicesignedrequestspecfeatureshardwaregpusindex}
<sup><sup>[↩ Parent](#edgedevicesignedrequestspecfeatureshardware)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>address</b></td>
          <td>string</td>
          <td>
            Device address (for example &#34;0000:00:02.0&#34;)<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>deviceId</b></td>
          <td>string</td>
          <td>
            ID of the device (for example &#34;3ea0&#34;)<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Product name of the device (for example &#34;UHD Graphics 620 (Whiskey Lake)&#34;)<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>vendor</b></td>
          <td>string</td>
          <td>
            The name of the device vendor (for example &#34;Intel Corporation&#34;)<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>vendorId</b></td>
          <td>string</td>
          <td>
            ID of the vendor (for example &#34;8086&#34;)<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSignedRequest.spec.features.hardware.interfaces[index] {#edgedevicesignedrequestspecfeatureshardwareinterfacesindex}
<sup><sup>[↩ Parent](#edgedevicesignedrequestspecfeatureshardware)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>flags</b></td>
          <td>[]string</td>
          <td>
            flags<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>biosdevname</b></td>
          <td>string</td>
          <td>
            biosdevname<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>clientId</b></td>
          <td>string</td>
          <td>
            client id<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>hasCarrier</b></td>
          <td>boolean</td>
          <td>
            has carrier<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>ipv4Addresses</b></td>
          <td>[]string</td>
          <td>
            ipv4 addresses<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>ipv6Addresses</b></td>
          <td>[]string</td>
          <td>
            ipv6 addresses<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>macAddress</b></td>
          <td>string</td>
          <td>
            mac address<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>mtu</b></td>
          <td>integer</td>
          <td>
            mtu<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            name<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>product</b></td>
          <td>string</td>
          <td>
            product<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>speedMbps</b></td>
          <td>integer</td>
          <td>
            speed mbps<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>vendor</b></td>
          <td>string</td>
          <td>
            vendor<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSignedRequest.spec.features.hardware.boot {#edgedevicesignedrequestspecfeatureshardwareboot}
<sup><sup>[↩ Parent](#edgedevicesignedrequestspecfeatureshardware)</sup></sup>



boot
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>currentBootMode</b></td>
          <td>string</td>
          <td>
            current boot mode<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>pxeInterface</b></td>
          <td>string</td>
          <td>
            pxe interface<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSignedRequest.spec.features.hardware.cpu {#edgedevicesignedrequestspecfeatureshardwarecpu}
<sup><sup>[↩ Parent](#edgedevicesignedrequestspecfeatureshardware)</sup></sup>



cpu
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>flags</b></td>
          <td>[]string</td>
          <td>
            flags<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>architecture</b></td>
          <td>string</td>
          <td>
            architecture<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>count</b></td>
          <td>integer</td>
          <td>
            count<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>frequency</b></td>
          <td>string</td>
          <td>
            frequency<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>modelName</b></td>
          <td>string</td>
          <td>
            model name<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSignedRequest.spec.features.hardware.hostDevices[index] {#edgedevicesignedrequestspecfeatureshardwarehostdevicesindex}
<sup><sup>[↩ Parent](#edgedevicesignedrequestspecfeatureshardware)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>deviceType</b></td>
          <td>string</td>
          <td>
            Device type block or character<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>group</b></td>
          <td>integer</td>
          <td>
            group id<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>major</b></td>
          <td>integer</td>
          <td>
            Major ID identifying the class of the device<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>minor</b></td>
          <td>integer</td>
          <td>
            Minor ID identifying the instance of the device in the class<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>owner</b></td>
          <td>integer</td>
          <td>
            owner id<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            path of the device (i.e. /dev/loop)<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSignedRequest.spec.features.hardware.memory {#edgedevicesignedrequestspecfeatureshardwarememory}
<sup><sup>[↩ Parent](#edgedevicesignedrequestspecfeatureshardware)</sup></sup>



memory
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>physicalBytes</b></td>
          <td>integer</td>
          <td>
            physical bytes<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>usableBytes</b></td>
          <td>integer</td>
          <td>
            usable bytes<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSignedRequest.spec.features.hardware.mounts[index] {#edgedevicesignedrequestspecfeatureshardwaremountsindex}
<sup><sup>[↩ Parent](#edgedevicesignedrequestspecfeatureshardware)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>device</b></td>
          <td>string</td>
          <td>
            Device path to be mounted<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>folder</b></td>
          <td>string</td>
          <td>
            Destination directory path<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>options</b></td>
          <td>string</td>
          <td>
            Mount options (i.e. rw, suid, dev)<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>type</b></td>
          <td>string</td>
          <td>
            Mount type: (i.e ext4)<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSignedRequest.spec.features.hardware.systemVendor {#edgedevicesignedrequestspecfeatureshardwaresystemvendor}
<sup><sup>[↩ Parent](#edgedevicesignedrequestspecfeatureshardware)</sup></sup>



system vendor
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>manufacturer</b></td>
          <td>string</td>
          <td>
            manufacturer<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>productName</b></td>
          <td>string</td>
          <td>
            product name<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>serialNumber</b></td>
          <td>string</td>
          <td>
            serial number<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>virtual</b></td>
          <td>boolean</td>
          <td>
            Whether the machine appears to be a virtual machine or not<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSignedRequest.status {#edgedevicesignedrequeststatus}
<sup><sup>[↩ Parent](#edgedevicesignedrequest)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgedevicesignedrequeststatusconditionsindex">conditions</a></b></td>
          <td>[]object</td>
          <td>
            <br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeDeviceSignedRequest.status.conditions[index] {#edgedevicesignedrequeststatusconditionsindex}
<sup><sup>[↩ Parent](#edgedevicesignedrequeststatus)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>status</b></td>
          <td>string</td>
          <td>
            Status of the condition, one of True, False, Unknown<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>type</b></td>
          <td>enum</td>
          <td>
            Type of status<br/>
            <br/>
              <i>Enum</i>: declined, approved, pending<br/>
              <i>Default</i>: pending<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>lastTransitionTime</b></td>
          <td>string</td>
          <td>
            The last time the condition transit from one status to another<br/>
            <br/>
              <i>Format</i>: date-time<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>message</b></td>
          <td>string</td>
          <td>
            A human-readable message indicating details about last transition<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>

### EdgeWorkload {#edgeworkload}
<sup><sup>[↩ Parent](#managementproject-flottaiov1alpha1 )</sup></sup>






EdgeWorkload is the Schema for the EdgeWorkloads API
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr>
        <td><b>apiVersion</b></td>
        <td>string</td>
        <td>management.project-flotta.io/v1alpha1</td>
        <td>true</td>
        </tr>
        <tr>
        <td><b>kind</b></td>
        <td>string</td>
        <td>EdgeWorkload</td>
        <td>true</td>
        </tr>
        <tr>
        <td><b><a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#objectmeta-v1-meta">metadata</a></b></td>
        <td>object</td>
        <td>Refer to the Kubernetes API documentation for the fields of the `metadata` field.</td>
        <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspec">spec</a></b></td>
          <td>object</td>
          <td>
            EdgeWorkloadSpec defines the desired state of EdgeWorkload<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>status</b></td>
          <td>object</td>
          <td>
            EdgeWorkloadStatus defines the observed state of EdgeWorkload<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec {#edgeworkloadspec}
<sup><sup>[↩ Parent](#edgeworkload)</sup></sup>



EdgeWorkloadSpec defines the desired state of EdgeWorkload
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>type</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecdata">data</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>device</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecdeviceselector">deviceSelector</a></b></td>
          <td>object</td>
          <td>
            A label selector is a label query over a set of resources. The result of matchLabels and matchExpressions are ANDed. An empty label selector matches all objects. A null label selector matches no objects.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecimageregistries">imageRegistries</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>logCollection</b></td>
          <td>string</td>
          <td>
            LogCollection is the logCollection property to be used to collect logs from this endpoint. This key is what is defined on the edgedevice logCollection property<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecmetrics">metrics</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpod">pod</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.data {#edgeworkloadspecdata}
<sup><sup>[↩ Parent](#edgeworkloadspec)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecdataegressindex">egress</a></b></td>
          <td>[]object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecdataingressindex">ingress</a></b></td>
          <td>[]object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.data.egress[index] {#edgeworkloadspecdataegressindex}
<sup><sup>[↩ Parent](#edgeworkloadspecdata)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>source</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>target</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.data.ingress[index] {#edgeworkloadspecdataingressindex}
<sup><sup>[↩ Parent](#edgeworkloadspecdata)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>source</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>target</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.deviceSelector {#edgeworkloadspecdeviceselector}
<sup><sup>[↩ Parent](#edgeworkloadspec)</sup></sup>



A label selector is a label query over a set of resources. The result of matchLabels and matchExpressions are ANDed. An empty label selector matches all objects. A null label selector matches no objects.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecdeviceselectormatchexpressionsindex">matchExpressions</a></b></td>
          <td>[]object</td>
          <td>
            matchExpressions is a list of label selector requirements. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>matchLabels</b></td>
          <td>map[string]string</td>
          <td>
            matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is &#34;key&#34;, the operator is &#34;In&#34;, and the values array contains only &#34;value&#34;. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.deviceSelector.matchExpressions[index] {#edgeworkloadspecdeviceselectormatchexpressionsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecdeviceselector)</sup></sup>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            key is the label key that the selector applies to.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>operator</b></td>
          <td>string</td>
          <td>
            operator represents a key&#39;s relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>values</b></td>
          <td>[]string</td>
          <td>
            values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.imageRegistries {#edgeworkloadspecimageregistries}
<sup><sup>[↩ Parent](#edgeworkloadspec)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecimageregistriessecretref">secretRef</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.imageRegistries.secretRef {#edgeworkloadspecimageregistriessecretref}
<sup><sup>[↩ Parent](#edgeworkloadspecimageregistries)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.metrics {#edgeworkloadspecmetrics}
<sup><sup>[↩ Parent](#edgeworkloadspec)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecmetricsallowlist">allowList</a></b></td>
          <td>object</td>
          <td>
            Specification of workload metrics to be collected<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecmetricscontainerskey">containers</a></b></td>
          <td>map[string]object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>interval</b></td>
          <td>integer</td>
          <td>
            Interval(in seconds) to scrape metrics endpoint.<br/>
            <br/>
              <i>Format</i>: int32<br/>
              <i>Default</i>: 60<br/>
              <i>Minimum</i>: 0<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path to use when retrieving metrics<br/>
            <br/>
              <i>Default</i>: /<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>port</b></td>
          <td>integer</td>
          <td>
            Port to use when retrieve the metrics<br/>
            <br/>
              <i>Format</i>: int32<br/>
              <i>Minimum</i>: 0<br/>
              <i>Maximum</i>: 65535<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.metrics.allowList {#edgeworkloadspecmetricsallowlist}
<sup><sup>[↩ Parent](#edgeworkloadspecmetrics)</sup></sup>



Specification of workload metrics to be collected
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.metrics.containers[key] {#edgeworkloadspecmetricscontainerskey}
<sup><sup>[↩ Parent](#edgeworkloadspecmetrics)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>disabled</b></td>
          <td>boolean</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path to use when retrieving metrics<br/>
            <br/>
              <i>Default</i>: /<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>port</b></td>
          <td>integer</td>
          <td>
            Port to use when retrieve the metrics<br/>
            <br/>
              <i>Format</i>: int32<br/>
              <i>Minimum</i>: 0<br/>
              <i>Maximum</i>: 65535<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod {#edgeworkloadspecpod}
<sup><sup>[↩ Parent](#edgeworkloadspec)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspec">spec</a></b></td>
          <td>object</td>
          <td>
            PodSpec is a description of a pod.<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec {#edgeworkloadspecpodspec}
<sup><sup>[↩ Parent](#edgeworkloadspecpod)</sup></sup>



PodSpec is a description of a pod.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindex">containers</a></b></td>
          <td>[]object</td>
          <td>
            List of containers belonging to the pod. Containers cannot currently be added or removed. There must be at least one container in a Pod. Cannot be updated.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>activeDeadlineSeconds</b></td>
          <td>integer</td>
          <td>
            Optional duration in seconds the pod may be active on the node relative to StartTime before the system will actively try to mark it failed and kill associated containers. Value must be a positive integer.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinity">affinity</a></b></td>
          <td>object</td>
          <td>
            If specified, the pod&#39;s scheduling constraints<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>automountServiceAccountToken</b></td>
          <td>boolean</td>
          <td>
            AutomountServiceAccountToken indicates whether a service account token should be automatically mounted.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecdnsconfig">dnsConfig</a></b></td>
          <td>object</td>
          <td>
            Specifies the DNS parameters of a pod. Parameters specified here will be merged to the generated DNS configuration based on DNSPolicy.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>dnsPolicy</b></td>
          <td>string</td>
          <td>
            Set DNS policy for the pod. Defaults to &#34;ClusterFirst&#34;. Valid values are &#39;ClusterFirstWithHostNet&#39;, &#39;ClusterFirst&#39;, &#39;Default&#39; or &#39;None&#39;. DNS parameters given in DNSConfig will be merged with the policy selected with DNSPolicy. To have DNS options set along with hostNetwork, you have to specify DNS policy explicitly to &#39;ClusterFirstWithHostNet&#39;.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>enableServiceLinks</b></td>
          <td>boolean</td>
          <td>
            EnableServiceLinks indicates whether information about services should be injected into pod&#39;s environment variables, matching the syntax of Docker links. Optional: Defaults to true.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindex">ephemeralContainers</a></b></td>
          <td>[]object</td>
          <td>
            List of ephemeral containers run in this pod. Ephemeral containers may be run in an existing pod to perform user-initiated actions such as debugging. This list cannot be specified when creating a pod, and it cannot be modified by updating the pod spec. In order to add an ephemeral container to an existing pod, use the pod&#39;s ephemeralcontainers subresource. This field is beta-level and available on clusters that haven&#39;t disabled the EphemeralContainers feature gate.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspechostaliasesindex">hostAliases</a></b></td>
          <td>[]object</td>
          <td>
            HostAliases is an optional list of hosts and IPs that will be injected into the pod&#39;s hosts file if specified. This is only valid for non-hostNetwork pods.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>hostIPC</b></td>
          <td>boolean</td>
          <td>
            Use the host&#39;s ipc namespace. Optional: Default to false.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>hostNetwork</b></td>
          <td>boolean</td>
          <td>
            Host networking requested for this pod. Use the host&#39;s network namespace. If this option is set, the ports that will be used must be specified. Default to false.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>hostPID</b></td>
          <td>boolean</td>
          <td>
            Use the host&#39;s pid namespace. Optional: Default to false.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>hostname</b></td>
          <td>string</td>
          <td>
            Specifies the hostname of the Pod If not specified, the pod&#39;s hostname will be set to a system-defined value.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecimagepullsecretsindex">imagePullSecrets</a></b></td>
          <td>[]object</td>
          <td>
            ImagePullSecrets is an optional list of references to secrets in the same namespace to use for pulling any of the images used by this PodSpec. If specified, these secrets will be passed to individual puller implementations for them to use. For example, in the case of docker, only DockerConfig type secrets are honored. More info: https://kubernetes.io/docs/concepts/containers/images#specifying-imagepullsecrets-on-a-pod<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindex">initContainers</a></b></td>
          <td>[]object</td>
          <td>
            List of initialization containers belonging to the pod. Init containers are executed in order prior to containers being started. If any init container fails, the pod is considered to have failed and is handled according to its restartPolicy. The name for an init container or normal container must be unique among all containers. Init containers may not have Lifecycle actions, Readiness probes, Liveness probes, or Startup probes. The resourceRequirements of an init container are taken into account during scheduling by finding the highest request/limit for each resource type, and then using the max of of that value or the sum of the normal containers. Limits are applied to init containers in a similar fashion. Init containers cannot currently be added or removed. Cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/init-containers/<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>nodeName</b></td>
          <td>string</td>
          <td>
            NodeName is a request to schedule this pod onto a specific node. If it is non-empty, the scheduler simply schedules this pod onto that node, assuming that it fits resource requirements.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>nodeSelector</b></td>
          <td>map[string]string</td>
          <td>
            NodeSelector is a selector which must be true for the pod to fit on a node. Selector which must match a node&#39;s labels for the pod to be scheduled on that node. More info: https://kubernetes.io/docs/concepts/configuration/assign-pod-node/<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecos">os</a></b></td>
          <td>object</td>
          <td>
            Specifies the OS of the containers in the pod. Some pod and container fields are restricted if this is set. 
 If the OS field is set to linux, the following fields must be unset: -securityContext.windowsOptions 
 If the OS field is set to windows, following fields must be unset: - spec.hostPID - spec.hostIPC - spec.securityContext.seLinuxOptions - spec.securityContext.seccompProfile - spec.securityContext.fsGroup - spec.securityContext.fsGroupChangePolicy - spec.securityContext.sysctls - spec.shareProcessNamespace - spec.securityContext.runAsUser - spec.securityContext.runAsGroup - spec.securityContext.supplementalGroups - spec.containers[*].securityContext.seLinuxOptions - spec.containers[*].securityContext.seccompProfile - spec.containers[*].securityContext.capabilities - spec.containers[*].securityContext.readOnlyRootFilesystem - spec.containers[*].securityContext.privileged - spec.containers[*].securityContext.allowPrivilegeEscalation - spec.containers[*].securityContext.procMount - spec.containers[*].securityContext.runAsUser - spec.containers[*].securityContext.runAsGroup This is an alpha field and requires the IdentifyPodOS feature<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>overhead</b></td>
          <td>map[string]int or string</td>
          <td>
            Overhead represents the resource overhead associated with running a pod for a given RuntimeClass. This field will be autopopulated at admission time by the RuntimeClass admission controller. If the RuntimeClass admission controller is enabled, overhead must not be set in Pod create requests. The RuntimeClass admission controller will reject Pod create requests which have the overhead already set. If RuntimeClass is configured and selected in the PodSpec, Overhead will be set to the value defined in the corresponding RuntimeClass, otherwise it will remain unset and treated as zero. More info: https://git.k8s.io/enhancements/keps/sig-node/688-pod-overhead/README.md This field is beta-level as of Kubernetes v1.18, and is only honored by servers that enable the PodOverhead feature.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>preemptionPolicy</b></td>
          <td>string</td>
          <td>
            PreemptionPolicy is the Policy for preempting pods with lower priority. One of Never, PreemptLowerPriority. Defaults to PreemptLowerPriority if unset. This field is beta-level, gated by the NonPreemptingPriority feature-gate.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>priority</b></td>
          <td>integer</td>
          <td>
            The priority value. Various system components use this field to find the priority of the pod. When Priority Admission Controller is enabled, it prevents users from setting this field. The admission controller populates this field from PriorityClassName. The higher the value, the higher the priority.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>priorityClassName</b></td>
          <td>string</td>
          <td>
            If specified, indicates the pod&#39;s priority. &#34;system-node-critical&#34; and &#34;system-cluster-critical&#34; are two special keywords which indicate the highest priorities with the former being the highest priority. Any other name must be defined by creating a PriorityClass object with that name. If not specified, the pod priority will be default or zero if there is no default.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecreadinessgatesindex">readinessGates</a></b></td>
          <td>[]object</td>
          <td>
            If specified, all readiness gates will be evaluated for pod readiness. A pod is ready when all its containers are ready AND all conditions specified in the readiness gates have status equal to &#34;True&#34; More info: https://git.k8s.io/enhancements/keps/sig-network/580-pod-readiness-gates<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>restartPolicy</b></td>
          <td>string</td>
          <td>
            Restart policy for all containers within the pod. One of Always, OnFailure, Never. Default to Always. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/#restart-policy<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>runtimeClassName</b></td>
          <td>string</td>
          <td>
            RuntimeClassName refers to a RuntimeClass object in the node.k8s.io group, which should be used to run this pod.  If no RuntimeClass resource matches the named class, the pod will not be run. If unset or empty, the &#34;legacy&#34; RuntimeClass will be used, which is an implicit class with an empty definition that uses the default runtime handler. More info: https://git.k8s.io/enhancements/keps/sig-node/585-runtime-class This is a beta feature as of Kubernetes v1.14.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>schedulerName</b></td>
          <td>string</td>
          <td>
            If specified, the pod will be dispatched by specified scheduler. If not specified, the pod will be dispatched by default scheduler.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecsecuritycontext">securityContext</a></b></td>
          <td>object</td>
          <td>
            SecurityContext holds pod-level security attributes and common container settings. Optional: Defaults to empty.  See type description for default values of each field.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>serviceAccount</b></td>
          <td>string</td>
          <td>
            DeprecatedServiceAccount is a depreciated alias for ServiceAccountName. Deprecated: Use serviceAccountName instead.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>serviceAccountName</b></td>
          <td>string</td>
          <td>
            ServiceAccountName is the name of the ServiceAccount to use to run this pod. More info: https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>setHostnameAsFQDN</b></td>
          <td>boolean</td>
          <td>
            If true the pod&#39;s hostname will be configured as the pod&#39;s FQDN, rather than the leaf name (the default). In Linux containers, this means setting the FQDN in the hostname field of the kernel (the nodename field of struct utsname). In Windows containers, this means setting the registry value of hostname for the registry key HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\Tcpip\\Parameters to FQDN. If a pod does not have FQDN, this has no effect. Default to false.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>shareProcessNamespace</b></td>
          <td>boolean</td>
          <td>
            Share a single process namespace between all of the containers in a pod. When this is set containers will be able to view and signal processes from other containers in the same pod, and the first process in each container will not be assigned PID 1. HostPID and ShareProcessNamespace cannot both be set. Optional: Default to false.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>subdomain</b></td>
          <td>string</td>
          <td>
            If specified, the fully qualified Pod hostname will be &#34;&lt;hostname&gt;.&lt;subdomain&gt;.&lt;pod namespace&gt;.svc.&lt;cluster domain&gt;&#34;. If not specified, the pod will not have a domainname at all.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>terminationGracePeriodSeconds</b></td>
          <td>integer</td>
          <td>
            Optional duration in seconds the pod needs to terminate gracefully. May be decreased in delete request. Value must be non-negative integer. The value zero indicates stop immediately via the kill signal (no opportunity to shut down). If this value is nil, the default grace period will be used instead. The grace period is the duration in seconds after the processes running in the pod are sent a termination signal and the time when the processes are forcibly halted with a kill signal. Set this value longer than the expected cleanup time for your process. Defaults to 30 seconds.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspectolerationsindex">tolerations</a></b></td>
          <td>[]object</td>
          <td>
            If specified, the pod&#39;s tolerations.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspectopologyspreadconstraintsindex">topologySpreadConstraints</a></b></td>
          <td>[]object</td>
          <td>
            TopologySpreadConstraints describes how a group of pods ought to spread across topology domains. Scheduler will schedule pods in a way which abides by the constraints. All topologySpreadConstraints are ANDed.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindex">volumes</a></b></td>
          <td>[]object</td>
          <td>
            List of volumes that can be mounted by containers belonging to the pod. More info: https://kubernetes.io/docs/concepts/storage/volumes<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index] {#edgeworkloadspecpodspeccontainersindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspec)</sup></sup>



A single application container that you want to run within a pod.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the container specified as a DNS_LABEL. Each container in a pod must have a unique name (DNS_LABEL). Cannot be updated.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>args</b></td>
          <td>[]string</td>
          <td>
            Arguments to the entrypoint. The docker image&#39;s CMD is used if this is not provided. Variable references $(VAR_NAME) are expanded using the container&#39;s environment. If a variable cannot be resolved, the reference in the input string will be unchanged. Double $$ are reduced to a single $, which allows for escaping the $(VAR_NAME) syntax: i.e. &#34;$$(VAR_NAME)&#34; will produce the string literal &#34;$(VAR_NAME)&#34;. Escaped references will never be expanded, regardless of whether the variable exists or not. Cannot be updated. More info: https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/#running-a-command-in-a-shell<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>command</b></td>
          <td>[]string</td>
          <td>
            Entrypoint array. Not executed within a shell. The docker image&#39;s ENTRYPOINT is used if this is not provided. Variable references $(VAR_NAME) are expanded using the container&#39;s environment. If a variable cannot be resolved, the reference in the input string will be unchanged. Double $$ are reduced to a single $, which allows for escaping the $(VAR_NAME) syntax: i.e. &#34;$$(VAR_NAME)&#34; will produce the string literal &#34;$(VAR_NAME)&#34;. Escaped references will never be expanded, regardless of whether the variable exists or not. Cannot be updated. More info: https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/#running-a-command-in-a-shell<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexenvindex">env</a></b></td>
          <td>[]object</td>
          <td>
            List of environment variables to set in the container. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexenvfromindex">envFrom</a></b></td>
          <td>[]object</td>
          <td>
            List of sources to populate environment variables in the container. The keys defined within a source must be a C_IDENTIFIER. All invalid keys will be reported as an event when the container is starting. When a key exists in multiple sources, the value associated with the last source will take precedence. Values defined by an Env with a duplicate key will take precedence. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>image</b></td>
          <td>string</td>
          <td>
            Docker image name. More info: https://kubernetes.io/docs/concepts/containers/images This field is optional to allow higher level config management to default or override container images in workload controllers like Deployments and StatefulSets.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>imagePullPolicy</b></td>
          <td>string</td>
          <td>
            Image pull policy. One of Always, Never, IfNotPresent. Defaults to Always if :latest tag is specified, or IfNotPresent otherwise. Cannot be updated. More info: https://kubernetes.io/docs/concepts/containers/images#updating-images<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexlifecycle">lifecycle</a></b></td>
          <td>object</td>
          <td>
            Actions that the management system should take in response to container lifecycle events. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexlivenessprobe">livenessProbe</a></b></td>
          <td>object</td>
          <td>
            Periodic probe of container liveness. Container will be restarted if the probe fails. Cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexportsindex">ports</a></b></td>
          <td>[]object</td>
          <td>
            List of ports to expose from the container. Exposing a port here gives the system additional information about the network connections a container uses, but is primarily informational. Not specifying a port here DOES NOT prevent that port from being exposed. Any port which is listening on the default &#34;0.0.0.0&#34; address inside a container will be accessible from the network. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexreadinessprobe">readinessProbe</a></b></td>
          <td>object</td>
          <td>
            Periodic probe of container service readiness. Container will be removed from service endpoints if the probe fails. Cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexresources">resources</a></b></td>
          <td>object</td>
          <td>
            Compute Resources required by this container. Cannot be updated. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexsecuritycontext">securityContext</a></b></td>
          <td>object</td>
          <td>
            SecurityContext defines the security options the container should be run with. If set, the fields of SecurityContext override the equivalent fields of PodSecurityContext. More info: https://kubernetes.io/docs/tasks/configure-pod-container/security-context/<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexstartupprobe">startupProbe</a></b></td>
          <td>object</td>
          <td>
            StartupProbe indicates that the Pod has successfully initialized. If specified, no other probes are executed until this completes successfully. If this probe fails, the Pod will be restarted, just as if the livenessProbe failed. This can be used to provide different probe parameters at the beginning of a Pod&#39;s lifecycle, when it might take a long time to load data or warm a cache, than during steady-state operation. This cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>stdin</b></td>
          <td>boolean</td>
          <td>
            Whether this container should allocate a buffer for stdin in the container runtime. If this is not set, reads from stdin in the container will always result in EOF. Default is false.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>stdinOnce</b></td>
          <td>boolean</td>
          <td>
            Whether the container runtime should close the stdin channel after it has been opened by a single attach. When stdin is true the stdin stream will remain open across multiple attach sessions. If stdinOnce is set to true, stdin is opened on container start, is empty until the first client attaches to stdin, and then remains open and accepts data until the client disconnects, at which time stdin is closed and remains closed until the container is restarted. If this flag is false, a container processes that reads from stdin will never receive an EOF. Default is false<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>terminationMessagePath</b></td>
          <td>string</td>
          <td>
            Optional: Path at which the file to which the container&#39;s termination message will be written is mounted into the container&#39;s filesystem. Message written is intended to be brief final status, such as an assertion failure message. Will be truncated by the node if greater than 4096 bytes. The total message length across all containers will be limited to 12kb. Defaults to /dev/termination-log. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>terminationMessagePolicy</b></td>
          <td>string</td>
          <td>
            Indicate how the termination message should be populated. File will use the contents of terminationMessagePath to populate the container status message on both success and failure. FallbackToLogsOnError will use the last chunk of container log output if the termination message file is empty and the container exited with an error. The log output is limited to 2048 bytes or 80 lines, whichever is smaller. Defaults to File. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>tty</b></td>
          <td>boolean</td>
          <td>
            Whether this container should allocate a TTY for itself, also requires &#39;stdin&#39; to be true. Default is false.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexvolumedevicesindex">volumeDevices</a></b></td>
          <td>[]object</td>
          <td>
            volumeDevices is the list of block devices to be used by the container.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexvolumemountsindex">volumeMounts</a></b></td>
          <td>[]object</td>
          <td>
            Pod volumes to mount into the container&#39;s filesystem. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>workingDir</b></td>
          <td>string</td>
          <td>
            Container&#39;s working directory. If not specified, the container runtime&#39;s default will be used, which might be configured in the container image. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].env[index] {#edgeworkloadspecpodspeccontainersindexenvindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindex)</sup></sup>



EnvVar represents an environment variable present in a Container.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the environment variable. Must be a C_IDENTIFIER.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            Variable references $(VAR_NAME) are expanded using the previously defined environment variables in the container and any service environment variables. If a variable cannot be resolved, the reference in the input string will be unchanged. Double $$ are reduced to a single $, which allows for escaping the $(VAR_NAME) syntax: i.e. &#34;$$(VAR_NAME)&#34; will produce the string literal &#34;$(VAR_NAME)&#34;. Escaped references will never be expanded, regardless of whether the variable exists or not. Defaults to &#34;&#34;.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexenvindexvaluefrom">valueFrom</a></b></td>
          <td>object</td>
          <td>
            Source for the environment variable&#39;s value. Cannot be used if value is not empty.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].env[index].valueFrom {#edgeworkloadspecpodspeccontainersindexenvindexvaluefrom}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexenvindex)</sup></sup>



Source for the environment variable&#39;s value. Cannot be used if value is not empty.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexenvindexvaluefromconfigmapkeyref">configMapKeyRef</a></b></td>
          <td>object</td>
          <td>
            Selects a key of a ConfigMap.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexenvindexvaluefromfieldref">fieldRef</a></b></td>
          <td>object</td>
          <td>
            Selects a field of the pod: supports metadata.name, metadata.namespace, `metadata.labels[&#39;&lt;KEY&gt;&#39;]`, `metadata.annotations[&#39;&lt;KEY&gt;&#39;]`, spec.nodeName, spec.serviceAccountName, status.hostIP, status.podIP, status.podIPs.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexenvindexvaluefromresourcefieldref">resourceFieldRef</a></b></td>
          <td>object</td>
          <td>
            Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, limits.ephemeral-storage, requests.cpu, requests.memory and requests.ephemeral-storage) are currently supported.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexenvindexvaluefromsecretkeyref">secretKeyRef</a></b></td>
          <td>object</td>
          <td>
            Selects a key of a secret in the pod&#39;s namespace<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].env[index].valueFrom.configMapKeyRef {#edgeworkloadspecpodspeccontainersindexenvindexvaluefromconfigmapkeyref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexenvindexvaluefrom)</sup></sup>



Selects a key of a ConfigMap.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            The key to select.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>optional</b></td>
          <td>boolean</td>
          <td>
            Specify whether the ConfigMap or its key must be defined<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].env[index].valueFrom.fieldRef {#edgeworkloadspecpodspeccontainersindexenvindexvaluefromfieldref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexenvindexvaluefrom)</sup></sup>



Selects a field of the pod: supports metadata.name, metadata.namespace, `metadata.labels[&#39;&lt;KEY&gt;&#39;]`, `metadata.annotations[&#39;&lt;KEY&gt;&#39;]`, spec.nodeName, spec.serviceAccountName, status.hostIP, status.podIP, status.podIPs.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>fieldPath</b></td>
          <td>string</td>
          <td>
            Path of the field to select in the specified API version.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>apiVersion</b></td>
          <td>string</td>
          <td>
            Version of the schema the FieldPath is written in terms of, defaults to &#34;v1&#34;.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].env[index].valueFrom.resourceFieldRef {#edgeworkloadspecpodspeccontainersindexenvindexvaluefromresourcefieldref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexenvindexvaluefrom)</sup></sup>



Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, limits.ephemeral-storage, requests.cpu, requests.memory and requests.ephemeral-storage) are currently supported.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>resource</b></td>
          <td>string</td>
          <td>
            Required: resource to select<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>containerName</b></td>
          <td>string</td>
          <td>
            Container name: required for volumes, optional for env vars<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>divisor</b></td>
          <td>int or string</td>
          <td>
            Specifies the output format of the exposed resources, defaults to &#34;1&#34;<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].env[index].valueFrom.secretKeyRef {#edgeworkloadspecpodspeccontainersindexenvindexvaluefromsecretkeyref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexenvindexvaluefrom)</sup></sup>



Selects a key of a secret in the pod&#39;s namespace
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            The key of the secret to select from.  Must be a valid secret key.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>optional</b></td>
          <td>boolean</td>
          <td>
            Specify whether the Secret or its key must be defined<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].envFrom[index] {#edgeworkloadspecpodspeccontainersindexenvfromindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindex)</sup></sup>



EnvFromSource represents the source of a set of ConfigMaps
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexenvfromindexconfigmapref">configMapRef</a></b></td>
          <td>object</td>
          <td>
            The ConfigMap to select from<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>prefix</b></td>
          <td>string</td>
          <td>
            An optional identifier to prepend to each key in the ConfigMap. Must be a C_IDENTIFIER.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexenvfromindexsecretref">secretRef</a></b></td>
          <td>object</td>
          <td>
            The Secret to select from<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].envFrom[index].configMapRef {#edgeworkloadspecpodspeccontainersindexenvfromindexconfigmapref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexenvfromindex)</sup></sup>



The ConfigMap to select from
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>optional</b></td>
          <td>boolean</td>
          <td>
            Specify whether the ConfigMap must be defined<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].envFrom[index].secretRef {#edgeworkloadspecpodspeccontainersindexenvfromindexsecretref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexenvfromindex)</sup></sup>



The Secret to select from
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>optional</b></td>
          <td>boolean</td>
          <td>
            Specify whether the Secret must be defined<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].lifecycle {#edgeworkloadspecpodspeccontainersindexlifecycle}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindex)</sup></sup>



Actions that the management system should take in response to container lifecycle events. Cannot be updated.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexlifecyclepoststart">postStart</a></b></td>
          <td>object</td>
          <td>
            PostStart is called immediately after a container is created. If the handler fails, the container is terminated and restarted according to its restart policy. Other management of the container blocks until the hook completes. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexlifecycleprestop">preStop</a></b></td>
          <td>object</td>
          <td>
            PreStop is called immediately before a container is terminated due to an API request or management event such as liveness/startup probe failure, preemption, resource contention, etc. The handler is not called if the container crashes or exits. The Pod&#39;s termination grace period countdown begins before the PreStop hook is executed. Regardless of the outcome of the handler, the container will eventually terminate within the Pod&#39;s termination grace period (unless delayed by finalizers). Other management of the container blocks until the hook completes or until the termination grace period is reached. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].lifecycle.postStart {#edgeworkloadspecpodspeccontainersindexlifecyclepoststart}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexlifecycle)</sup></sup>



PostStart is called immediately after a container is created. If the handler fails, the container is terminated and restarted according to its restart policy. Other management of the container blocks until the hook completes. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexlifecyclepoststartexec">exec</a></b></td>
          <td>object</td>
          <td>
            Exec specifies the action to take.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexlifecyclepoststarthttpget">httpGet</a></b></td>
          <td>object</td>
          <td>
            HTTPGet specifies the http request to perform.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexlifecyclepoststarttcpsocket">tcpSocket</a></b></td>
          <td>object</td>
          <td>
            Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].lifecycle.postStart.exec {#edgeworkloadspecpodspeccontainersindexlifecyclepoststartexec}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexlifecyclepoststart)</sup></sup>



Exec specifies the action to take.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>command</b></td>
          <td>[]string</td>
          <td>
            Command is the command line to execute inside the container, the working directory for the command  is root (&#39;/&#39;) in the container&#39;s filesystem. The command is simply exec&#39;d, it is not run inside a shell, so traditional shell instructions (&#39;|&#39;, etc) won&#39;t work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].lifecycle.postStart.httpGet {#edgeworkloadspecpodspeccontainersindexlifecyclepoststarthttpget}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexlifecyclepoststart)</sup></sup>



HTTPGet specifies the http request to perform.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Host name to connect to, defaults to the pod IP. You probably want to set &#34;Host&#34; in httpHeaders instead.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexlifecyclepoststarthttpgethttpheadersindex">httpHeaders</a></b></td>
          <td>[]object</td>
          <td>
            Custom headers to set in the request. HTTP allows repeated headers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path to access on the HTTP server.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>scheme</b></td>
          <td>string</td>
          <td>
            Scheme to use for connecting to the host. Defaults to HTTP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].lifecycle.postStart.httpGet.httpHeaders[index] {#edgeworkloadspecpodspeccontainersindexlifecyclepoststarthttpgethttpheadersindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexlifecyclepoststarthttpget)</sup></sup>



HTTPHeader describes a custom header to be used in HTTP probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            The header field name<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            The header field value<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].lifecycle.postStart.tcpSocket {#edgeworkloadspecpodspeccontainersindexlifecyclepoststarttcpsocket}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexlifecyclepoststart)</sup></sup>



Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Optional: Host name to connect to, defaults to the pod IP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].lifecycle.preStop {#edgeworkloadspecpodspeccontainersindexlifecycleprestop}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexlifecycle)</sup></sup>



PreStop is called immediately before a container is terminated due to an API request or management event such as liveness/startup probe failure, preemption, resource contention, etc. The handler is not called if the container crashes or exits. The Pod&#39;s termination grace period countdown begins before the PreStop hook is executed. Regardless of the outcome of the handler, the container will eventually terminate within the Pod&#39;s termination grace period (unless delayed by finalizers). Other management of the container blocks until the hook completes or until the termination grace period is reached. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexlifecycleprestopexec">exec</a></b></td>
          <td>object</td>
          <td>
            Exec specifies the action to take.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexlifecycleprestophttpget">httpGet</a></b></td>
          <td>object</td>
          <td>
            HTTPGet specifies the http request to perform.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexlifecycleprestoptcpsocket">tcpSocket</a></b></td>
          <td>object</td>
          <td>
            Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].lifecycle.preStop.exec {#edgeworkloadspecpodspeccontainersindexlifecycleprestopexec}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexlifecycleprestop)</sup></sup>



Exec specifies the action to take.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>command</b></td>
          <td>[]string</td>
          <td>
            Command is the command line to execute inside the container, the working directory for the command  is root (&#39;/&#39;) in the container&#39;s filesystem. The command is simply exec&#39;d, it is not run inside a shell, so traditional shell instructions (&#39;|&#39;, etc) won&#39;t work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].lifecycle.preStop.httpGet {#edgeworkloadspecpodspeccontainersindexlifecycleprestophttpget}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexlifecycleprestop)</sup></sup>



HTTPGet specifies the http request to perform.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Host name to connect to, defaults to the pod IP. You probably want to set &#34;Host&#34; in httpHeaders instead.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexlifecycleprestophttpgethttpheadersindex">httpHeaders</a></b></td>
          <td>[]object</td>
          <td>
            Custom headers to set in the request. HTTP allows repeated headers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path to access on the HTTP server.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>scheme</b></td>
          <td>string</td>
          <td>
            Scheme to use for connecting to the host. Defaults to HTTP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].lifecycle.preStop.httpGet.httpHeaders[index] {#edgeworkloadspecpodspeccontainersindexlifecycleprestophttpgethttpheadersindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexlifecycleprestophttpget)</sup></sup>



HTTPHeader describes a custom header to be used in HTTP probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            The header field name<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            The header field value<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].lifecycle.preStop.tcpSocket {#edgeworkloadspecpodspeccontainersindexlifecycleprestoptcpsocket}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexlifecycleprestop)</sup></sup>



Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Optional: Host name to connect to, defaults to the pod IP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].livenessProbe {#edgeworkloadspecpodspeccontainersindexlivenessprobe}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindex)</sup></sup>



Periodic probe of container liveness. Container will be restarted if the probe fails. Cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexlivenessprobeexec">exec</a></b></td>
          <td>object</td>
          <td>
            Exec specifies the action to take.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>failureThreshold</b></td>
          <td>integer</td>
          <td>
            Minimum consecutive failures for the probe to be considered failed after having succeeded. Defaults to 3. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexlivenessprobegrpc">grpc</a></b></td>
          <td>object</td>
          <td>
            GRPC specifies an action involving a GRPC port. This is an alpha field and requires enabling GRPCContainerProbe feature gate.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexlivenessprobehttpget">httpGet</a></b></td>
          <td>object</td>
          <td>
            HTTPGet specifies the http request to perform.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>initialDelaySeconds</b></td>
          <td>integer</td>
          <td>
            Number of seconds after the container has started before liveness probes are initiated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>periodSeconds</b></td>
          <td>integer</td>
          <td>
            How often (in seconds) to perform the probe. Default to 10 seconds. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>successThreshold</b></td>
          <td>integer</td>
          <td>
            Minimum consecutive successes for the probe to be considered successful after having failed. Defaults to 1. Must be 1 for liveness and startup. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexlivenessprobetcpsocket">tcpSocket</a></b></td>
          <td>object</td>
          <td>
            TCPSocket specifies an action involving a TCP port.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>terminationGracePeriodSeconds</b></td>
          <td>integer</td>
          <td>
            Optional duration in seconds the pod needs to terminate gracefully upon probe failure. The grace period is the duration in seconds after the processes running in the pod are sent a termination signal and the time when the processes are forcibly halted with a kill signal. Set this value longer than the expected cleanup time for your process. If this value is nil, the pod&#39;s terminationGracePeriodSeconds will be used. Otherwise, this value overrides the value provided by the pod spec. Value must be non-negative integer. The value zero indicates stop immediately via the kill signal (no opportunity to shut down). This is a beta field and requires enabling ProbeTerminationGracePeriod feature gate. Minimum value is 1. spec.terminationGracePeriodSeconds is used if unset.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>timeoutSeconds</b></td>
          <td>integer</td>
          <td>
            Number of seconds after which the probe times out. Defaults to 1 second. Minimum value is 1. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].livenessProbe.exec {#edgeworkloadspecpodspeccontainersindexlivenessprobeexec}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexlivenessprobe)</sup></sup>



Exec specifies the action to take.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>command</b></td>
          <td>[]string</td>
          <td>
            Command is the command line to execute inside the container, the working directory for the command  is root (&#39;/&#39;) in the container&#39;s filesystem. The command is simply exec&#39;d, it is not run inside a shell, so traditional shell instructions (&#39;|&#39;, etc) won&#39;t work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].livenessProbe.grpc {#edgeworkloadspecpodspeccontainersindexlivenessprobegrpc}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexlivenessprobe)</sup></sup>



GRPC specifies an action involving a GRPC port. This is an alpha field and requires enabling GRPCContainerProbe feature gate.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>integer</td>
          <td>
            Port number of the gRPC service. Number must be in the range 1 to 65535.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>service</b></td>
          <td>string</td>
          <td>
            Service is the name of the service to place in the gRPC HealthCheckRequest (see https://github.com/grpc/grpc/blob/master/doc/health-checking.md). 
 If this is not specified, the default behavior is defined by gRPC.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].livenessProbe.httpGet {#edgeworkloadspecpodspeccontainersindexlivenessprobehttpget}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexlivenessprobe)</sup></sup>



HTTPGet specifies the http request to perform.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Host name to connect to, defaults to the pod IP. You probably want to set &#34;Host&#34; in httpHeaders instead.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexlivenessprobehttpgethttpheadersindex">httpHeaders</a></b></td>
          <td>[]object</td>
          <td>
            Custom headers to set in the request. HTTP allows repeated headers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path to access on the HTTP server.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>scheme</b></td>
          <td>string</td>
          <td>
            Scheme to use for connecting to the host. Defaults to HTTP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].livenessProbe.httpGet.httpHeaders[index] {#edgeworkloadspecpodspeccontainersindexlivenessprobehttpgethttpheadersindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexlivenessprobehttpget)</sup></sup>



HTTPHeader describes a custom header to be used in HTTP probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            The header field name<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            The header field value<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].livenessProbe.tcpSocket {#edgeworkloadspecpodspeccontainersindexlivenessprobetcpsocket}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexlivenessprobe)</sup></sup>



TCPSocket specifies an action involving a TCP port.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Optional: Host name to connect to, defaults to the pod IP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].ports[index] {#edgeworkloadspecpodspeccontainersindexportsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindex)</sup></sup>



ContainerPort represents a network port in a single container.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>containerPort</b></td>
          <td>integer</td>
          <td>
            Number of port to expose on the pod&#39;s IP address. This must be a valid port number, 0 &lt; x &lt; 65536.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>hostIP</b></td>
          <td>string</td>
          <td>
            What host IP to bind the external port to.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>hostPort</b></td>
          <td>integer</td>
          <td>
            Number of port to expose on the host. If specified, this must be a valid port number, 0 &lt; x &lt; 65536. If HostNetwork is specified, this must match ContainerPort. Most containers do not need this.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            If specified, this must be an IANA_SVC_NAME and unique within the pod. Each named port in a pod must have a unique name. Name for the port that can be referred to by services.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>protocol</b></td>
          <td>string</td>
          <td>
            Protocol for port. Must be UDP, TCP, or SCTP. Defaults to &#34;TCP&#34;.<br/>
            <br/>
              <i>Default</i>: TCP<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].readinessProbe {#edgeworkloadspecpodspeccontainersindexreadinessprobe}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindex)</sup></sup>



Periodic probe of container service readiness. Container will be removed from service endpoints if the probe fails. Cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexreadinessprobeexec">exec</a></b></td>
          <td>object</td>
          <td>
            Exec specifies the action to take.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>failureThreshold</b></td>
          <td>integer</td>
          <td>
            Minimum consecutive failures for the probe to be considered failed after having succeeded. Defaults to 3. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexreadinessprobegrpc">grpc</a></b></td>
          <td>object</td>
          <td>
            GRPC specifies an action involving a GRPC port. This is an alpha field and requires enabling GRPCContainerProbe feature gate.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexreadinessprobehttpget">httpGet</a></b></td>
          <td>object</td>
          <td>
            HTTPGet specifies the http request to perform.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>initialDelaySeconds</b></td>
          <td>integer</td>
          <td>
            Number of seconds after the container has started before liveness probes are initiated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>periodSeconds</b></td>
          <td>integer</td>
          <td>
            How often (in seconds) to perform the probe. Default to 10 seconds. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>successThreshold</b></td>
          <td>integer</td>
          <td>
            Minimum consecutive successes for the probe to be considered successful after having failed. Defaults to 1. Must be 1 for liveness and startup. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexreadinessprobetcpsocket">tcpSocket</a></b></td>
          <td>object</td>
          <td>
            TCPSocket specifies an action involving a TCP port.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>terminationGracePeriodSeconds</b></td>
          <td>integer</td>
          <td>
            Optional duration in seconds the pod needs to terminate gracefully upon probe failure. The grace period is the duration in seconds after the processes running in the pod are sent a termination signal and the time when the processes are forcibly halted with a kill signal. Set this value longer than the expected cleanup time for your process. If this value is nil, the pod&#39;s terminationGracePeriodSeconds will be used. Otherwise, this value overrides the value provided by the pod spec. Value must be non-negative integer. The value zero indicates stop immediately via the kill signal (no opportunity to shut down). This is a beta field and requires enabling ProbeTerminationGracePeriod feature gate. Minimum value is 1. spec.terminationGracePeriodSeconds is used if unset.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>timeoutSeconds</b></td>
          <td>integer</td>
          <td>
            Number of seconds after which the probe times out. Defaults to 1 second. Minimum value is 1. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].readinessProbe.exec {#edgeworkloadspecpodspeccontainersindexreadinessprobeexec}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexreadinessprobe)</sup></sup>



Exec specifies the action to take.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>command</b></td>
          <td>[]string</td>
          <td>
            Command is the command line to execute inside the container, the working directory for the command  is root (&#39;/&#39;) in the container&#39;s filesystem. The command is simply exec&#39;d, it is not run inside a shell, so traditional shell instructions (&#39;|&#39;, etc) won&#39;t work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].readinessProbe.grpc {#edgeworkloadspecpodspeccontainersindexreadinessprobegrpc}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexreadinessprobe)</sup></sup>



GRPC specifies an action involving a GRPC port. This is an alpha field and requires enabling GRPCContainerProbe feature gate.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>integer</td>
          <td>
            Port number of the gRPC service. Number must be in the range 1 to 65535.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>service</b></td>
          <td>string</td>
          <td>
            Service is the name of the service to place in the gRPC HealthCheckRequest (see https://github.com/grpc/grpc/blob/master/doc/health-checking.md). 
 If this is not specified, the default behavior is defined by gRPC.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].readinessProbe.httpGet {#edgeworkloadspecpodspeccontainersindexreadinessprobehttpget}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexreadinessprobe)</sup></sup>



HTTPGet specifies the http request to perform.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Host name to connect to, defaults to the pod IP. You probably want to set &#34;Host&#34; in httpHeaders instead.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexreadinessprobehttpgethttpheadersindex">httpHeaders</a></b></td>
          <td>[]object</td>
          <td>
            Custom headers to set in the request. HTTP allows repeated headers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path to access on the HTTP server.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>scheme</b></td>
          <td>string</td>
          <td>
            Scheme to use for connecting to the host. Defaults to HTTP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].readinessProbe.httpGet.httpHeaders[index] {#edgeworkloadspecpodspeccontainersindexreadinessprobehttpgethttpheadersindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexreadinessprobehttpget)</sup></sup>



HTTPHeader describes a custom header to be used in HTTP probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            The header field name<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            The header field value<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].readinessProbe.tcpSocket {#edgeworkloadspecpodspeccontainersindexreadinessprobetcpsocket}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexreadinessprobe)</sup></sup>



TCPSocket specifies an action involving a TCP port.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Optional: Host name to connect to, defaults to the pod IP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].resources {#edgeworkloadspecpodspeccontainersindexresources}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindex)</sup></sup>



Compute Resources required by this container. Cannot be updated. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>limits</b></td>
          <td>map[string]int or string</td>
          <td>
            Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>requests</b></td>
          <td>map[string]int or string</td>
          <td>
            Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].securityContext {#edgeworkloadspecpodspeccontainersindexsecuritycontext}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindex)</sup></sup>



SecurityContext defines the security options the container should be run with. If set, the fields of SecurityContext override the equivalent fields of PodSecurityContext. More info: https://kubernetes.io/docs/tasks/configure-pod-container/security-context/
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>allowPrivilegeEscalation</b></td>
          <td>boolean</td>
          <td>
            AllowPrivilegeEscalation controls whether a process can gain more privileges than its parent process. This bool directly controls if the no_new_privs flag will be set on the container process. AllowPrivilegeEscalation is true always when the container is: 1) run as Privileged 2) has CAP_SYS_ADMIN Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexsecuritycontextcapabilities">capabilities</a></b></td>
          <td>object</td>
          <td>
            The capabilities to add/drop when running containers. Defaults to the default set of capabilities granted by the container runtime. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>privileged</b></td>
          <td>boolean</td>
          <td>
            Run container in privileged mode. Processes in privileged containers are essentially equivalent to root on the host. Defaults to false. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>procMount</b></td>
          <td>string</td>
          <td>
            procMount denotes the type of proc mount to use for the containers. The default is DefaultProcMount which uses the container runtime defaults for readonly paths and masked paths. This requires the ProcMountType feature flag to be enabled. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnlyRootFilesystem</b></td>
          <td>boolean</td>
          <td>
            Whether this container has a read-only root filesystem. Default is false. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>runAsGroup</b></td>
          <td>integer</td>
          <td>
            The GID to run the entrypoint of the container process. Uses runtime default if unset. May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>runAsNonRoot</b></td>
          <td>boolean</td>
          <td>
            Indicates that the container must run as a non-root user. If true, the Kubelet will validate the image at runtime to ensure that it does not run as UID 0 (root) and fail to start the container if it does. If unset or false, no such validation will be performed. May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>runAsUser</b></td>
          <td>integer</td>
          <td>
            The UID to run the entrypoint of the container process. Defaults to user specified in image metadata if unspecified. May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexsecuritycontextselinuxoptions">seLinuxOptions</a></b></td>
          <td>object</td>
          <td>
            The SELinux context to be applied to the container. If unspecified, the container runtime will allocate a random SELinux context for each container.  May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexsecuritycontextseccompprofile">seccompProfile</a></b></td>
          <td>object</td>
          <td>
            The seccomp options to use by this container. If seccomp options are provided at both the pod &amp; container level, the container options override the pod options. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexsecuritycontextwindowsoptions">windowsOptions</a></b></td>
          <td>object</td>
          <td>
            The Windows specific settings applied to all containers. If unspecified, the options from the PodSecurityContext will be used. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is linux.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].securityContext.capabilities {#edgeworkloadspecpodspeccontainersindexsecuritycontextcapabilities}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexsecuritycontext)</sup></sup>



The capabilities to add/drop when running containers. Defaults to the default set of capabilities granted by the container runtime. Note that this field cannot be set when spec.os.name is windows.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>add</b></td>
          <td>[]string</td>
          <td>
            Added capabilities<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>drop</b></td>
          <td>[]string</td>
          <td>
            Removed capabilities<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].securityContext.seLinuxOptions {#edgeworkloadspecpodspeccontainersindexsecuritycontextselinuxoptions}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexsecuritycontext)</sup></sup>



The SELinux context to be applied to the container. If unspecified, the container runtime will allocate a random SELinux context for each container.  May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>level</b></td>
          <td>string</td>
          <td>
            Level is SELinux level label that applies to the container.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>role</b></td>
          <td>string</td>
          <td>
            Role is a SELinux role label that applies to the container.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>type</b></td>
          <td>string</td>
          <td>
            Type is a SELinux type label that applies to the container.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>user</b></td>
          <td>string</td>
          <td>
            User is a SELinux user label that applies to the container.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].securityContext.seccompProfile {#edgeworkloadspecpodspeccontainersindexsecuritycontextseccompprofile}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexsecuritycontext)</sup></sup>



The seccomp options to use by this container. If seccomp options are provided at both the pod &amp; container level, the container options override the pod options. Note that this field cannot be set when spec.os.name is windows.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>type</b></td>
          <td>string</td>
          <td>
            type indicates which kind of seccomp profile will be applied. Valid options are: 
 Localhost - a profile defined in a file on the node should be used. RuntimeDefault - the container runtime default profile should be used. Unconfined - no profile should be applied.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>localhostProfile</b></td>
          <td>string</td>
          <td>
            localhostProfile indicates a profile defined in a file on the node should be used. The profile must be preconfigured on the node to work. Must be a descending path, relative to the kubelet&#39;s configured seccomp profile location. Must only be set if type is &#34;Localhost&#34;.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].securityContext.windowsOptions {#edgeworkloadspecpodspeccontainersindexsecuritycontextwindowsoptions}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexsecuritycontext)</sup></sup>



The Windows specific settings applied to all containers. If unspecified, the options from the PodSecurityContext will be used. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is linux.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>gmsaCredentialSpec</b></td>
          <td>string</td>
          <td>
            GMSACredentialSpec is where the GMSA admission webhook (https://github.com/kubernetes-sigs/windows-gmsa) inlines the contents of the GMSA credential spec named by the GMSACredentialSpecName field.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>gmsaCredentialSpecName</b></td>
          <td>string</td>
          <td>
            GMSACredentialSpecName is the name of the GMSA credential spec to use.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>hostProcess</b></td>
          <td>boolean</td>
          <td>
            HostProcess determines if a container should be run as a &#39;Host Process&#39; container. This field is alpha-level and will only be honored by components that enable the WindowsHostProcessContainers feature flag. Setting this field without the feature flag will result in errors when validating the Pod. All of a Pod&#39;s containers must have the same effective HostProcess value (it is not allowed to have a mix of HostProcess containers and non-HostProcess containers).  In addition, if HostProcess is true then HostNetwork must also be set to true.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>runAsUserName</b></td>
          <td>string</td>
          <td>
            The UserName in Windows to run the entrypoint of the container process. Defaults to the user specified in image metadata if unspecified. May also be set in PodSecurityContext. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].startupProbe {#edgeworkloadspecpodspeccontainersindexstartupprobe}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindex)</sup></sup>



StartupProbe indicates that the Pod has successfully initialized. If specified, no other probes are executed until this completes successfully. If this probe fails, the Pod will be restarted, just as if the livenessProbe failed. This can be used to provide different probe parameters at the beginning of a Pod&#39;s lifecycle, when it might take a long time to load data or warm a cache, than during steady-state operation. This cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexstartupprobeexec">exec</a></b></td>
          <td>object</td>
          <td>
            Exec specifies the action to take.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>failureThreshold</b></td>
          <td>integer</td>
          <td>
            Minimum consecutive failures for the probe to be considered failed after having succeeded. Defaults to 3. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexstartupprobegrpc">grpc</a></b></td>
          <td>object</td>
          <td>
            GRPC specifies an action involving a GRPC port. This is an alpha field and requires enabling GRPCContainerProbe feature gate.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexstartupprobehttpget">httpGet</a></b></td>
          <td>object</td>
          <td>
            HTTPGet specifies the http request to perform.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>initialDelaySeconds</b></td>
          <td>integer</td>
          <td>
            Number of seconds after the container has started before liveness probes are initiated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>periodSeconds</b></td>
          <td>integer</td>
          <td>
            How often (in seconds) to perform the probe. Default to 10 seconds. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>successThreshold</b></td>
          <td>integer</td>
          <td>
            Minimum consecutive successes for the probe to be considered successful after having failed. Defaults to 1. Must be 1 for liveness and startup. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexstartupprobetcpsocket">tcpSocket</a></b></td>
          <td>object</td>
          <td>
            TCPSocket specifies an action involving a TCP port.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>terminationGracePeriodSeconds</b></td>
          <td>integer</td>
          <td>
            Optional duration in seconds the pod needs to terminate gracefully upon probe failure. The grace period is the duration in seconds after the processes running in the pod are sent a termination signal and the time when the processes are forcibly halted with a kill signal. Set this value longer than the expected cleanup time for your process. If this value is nil, the pod&#39;s terminationGracePeriodSeconds will be used. Otherwise, this value overrides the value provided by the pod spec. Value must be non-negative integer. The value zero indicates stop immediately via the kill signal (no opportunity to shut down). This is a beta field and requires enabling ProbeTerminationGracePeriod feature gate. Minimum value is 1. spec.terminationGracePeriodSeconds is used if unset.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>timeoutSeconds</b></td>
          <td>integer</td>
          <td>
            Number of seconds after which the probe times out. Defaults to 1 second. Minimum value is 1. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].startupProbe.exec {#edgeworkloadspecpodspeccontainersindexstartupprobeexec}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexstartupprobe)</sup></sup>



Exec specifies the action to take.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>command</b></td>
          <td>[]string</td>
          <td>
            Command is the command line to execute inside the container, the working directory for the command  is root (&#39;/&#39;) in the container&#39;s filesystem. The command is simply exec&#39;d, it is not run inside a shell, so traditional shell instructions (&#39;|&#39;, etc) won&#39;t work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].startupProbe.grpc {#edgeworkloadspecpodspeccontainersindexstartupprobegrpc}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexstartupprobe)</sup></sup>



GRPC specifies an action involving a GRPC port. This is an alpha field and requires enabling GRPCContainerProbe feature gate.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>integer</td>
          <td>
            Port number of the gRPC service. Number must be in the range 1 to 65535.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>service</b></td>
          <td>string</td>
          <td>
            Service is the name of the service to place in the gRPC HealthCheckRequest (see https://github.com/grpc/grpc/blob/master/doc/health-checking.md). 
 If this is not specified, the default behavior is defined by gRPC.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].startupProbe.httpGet {#edgeworkloadspecpodspeccontainersindexstartupprobehttpget}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexstartupprobe)</sup></sup>



HTTPGet specifies the http request to perform.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Host name to connect to, defaults to the pod IP. You probably want to set &#34;Host&#34; in httpHeaders instead.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspeccontainersindexstartupprobehttpgethttpheadersindex">httpHeaders</a></b></td>
          <td>[]object</td>
          <td>
            Custom headers to set in the request. HTTP allows repeated headers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path to access on the HTTP server.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>scheme</b></td>
          <td>string</td>
          <td>
            Scheme to use for connecting to the host. Defaults to HTTP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].startupProbe.httpGet.httpHeaders[index] {#edgeworkloadspecpodspeccontainersindexstartupprobehttpgethttpheadersindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexstartupprobehttpget)</sup></sup>



HTTPHeader describes a custom header to be used in HTTP probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            The header field name<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            The header field value<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].startupProbe.tcpSocket {#edgeworkloadspecpodspeccontainersindexstartupprobetcpsocket}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindexstartupprobe)</sup></sup>



TCPSocket specifies an action involving a TCP port.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Optional: Host name to connect to, defaults to the pod IP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].volumeDevices[index] {#edgeworkloadspecpodspeccontainersindexvolumedevicesindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindex)</sup></sup>



volumeDevice describes a mapping of a raw block device within a container.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>devicePath</b></td>
          <td>string</td>
          <td>
            devicePath is the path inside of the container that the device will be mapped to.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            name must match the name of a persistentVolumeClaim in the pod<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.containers[index].volumeMounts[index] {#edgeworkloadspecpodspeccontainersindexvolumemountsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspeccontainersindex)</sup></sup>



VolumeMount describes a mounting of a Volume within a container.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>mountPath</b></td>
          <td>string</td>
          <td>
            Path within the container at which the volume should be mounted.  Must not contain &#39;:&#39;.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            This must match the Name of a Volume.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>mountPropagation</b></td>
          <td>string</td>
          <td>
            mountPropagation determines how mounts are propagated from the host to container and the other way around. When not set, MountPropagationNone is used. This field is beta in 1.10.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            Mounted read-only if true, read-write otherwise (false or unspecified). Defaults to false.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>subPath</b></td>
          <td>string</td>
          <td>
            Path within the volume from which the container&#39;s volume should be mounted. Defaults to &#34;&#34; (volume&#39;s root).<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>subPathExpr</b></td>
          <td>string</td>
          <td>
            Expanded path within the volume from which the container&#39;s volume should be mounted. Behaves similarly to SubPath but environment variable references $(VAR_NAME) are expanded using the container&#39;s environment. Defaults to &#34;&#34; (volume&#39;s root). SubPathExpr and SubPath are mutually exclusive.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity {#edgeworkloadspecpodspecaffinity}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspec)</sup></sup>



If specified, the pod&#39;s scheduling constraints
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitynodeaffinity">nodeAffinity</a></b></td>
          <td>object</td>
          <td>
            Describes node affinity scheduling rules for the pod.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodaffinity">podAffinity</a></b></td>
          <td>object</td>
          <td>
            Describes pod affinity scheduling rules (e.g. co-locate this pod in the same node, zone, etc. as some other pod(s)).<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodantiaffinity">podAntiAffinity</a></b></td>
          <td>object</td>
          <td>
            Describes pod anti-affinity scheduling rules (e.g. avoid putting this pod in the same node, zone, etc. as some other pod(s)).<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.nodeAffinity {#edgeworkloadspecpodspecaffinitynodeaffinity}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinity)</sup></sup>



Describes node affinity scheduling rules for the pod.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindex">preferredDuringSchedulingIgnoredDuringExecution</a></b></td>
          <td>[]object</td>
          <td>
            The scheduler will prefer to schedule pods to nodes that satisfy the affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding &#34;weight&#34; to the sum if the node matches the corresponding matchExpressions; the node(s) with the highest sum are the most preferred.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitynodeaffinityrequiredduringschedulingignoredduringexecution">requiredDuringSchedulingIgnoredDuringExecution</a></b></td>
          <td>object</td>
          <td>
            If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to an update), the system may or may not try to eventually evict the pod from its node.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index] {#edgeworkloadspecpodspecaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitynodeaffinity)</sup></sup>



An empty preferred scheduling term matches all objects with implicit weight 0 (i.e. it&#39;s a no-op). A null preferred scheduling term matches no objects (i.e. is also a no-op).
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">preference</a></b></td>
          <td>object</td>
          <td>
            A node selector term, associated with the corresponding weight.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>weight</b></td>
          <td>integer</td>
          <td>
            Weight associated with matching the corresponding nodeSelectorTerm, in the range 1-100.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference {#edgeworkloadspecpodspecaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindex)</sup></sup>



A node selector term, associated with the corresponding weight.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreferencematchexpressionsindex">matchExpressions</a></b></td>
          <td>[]object</td>
          <td>
            A list of node selector requirements by node&#39;s labels.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreferencematchfieldsindex">matchFields</a></b></td>
          <td>[]object</td>
          <td>
            A list of node selector requirements by node&#39;s fields.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference.matchExpressions[index] {#edgeworkloadspecpodspecaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreferencematchexpressionsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference)</sup></sup>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            The label key that the selector applies to.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>operator</b></td>
          <td>string</td>
          <td>
            Represents a key&#39;s relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>values</b></td>
          <td>[]string</td>
          <td>
            An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference.matchFields[index] {#edgeworkloadspecpodspecaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreferencematchfieldsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference)</sup></sup>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            The label key that the selector applies to.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>operator</b></td>
          <td>string</td>
          <td>
            Represents a key&#39;s relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>values</b></td>
          <td>[]string</td>
          <td>
            An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution {#edgeworkloadspecpodspecaffinitynodeaffinityrequiredduringschedulingignoredduringexecution}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitynodeaffinity)</sup></sup>



If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to an update), the system may or may not try to eventually evict the pod from its node.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">nodeSelectorTerms</a></b></td>
          <td>[]object</td>
          <td>
            Required. A list of node selector terms. The terms are ORed.<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index] {#edgeworkloadspecpodspecaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitynodeaffinityrequiredduringschedulingignoredduringexecution)</sup></sup>



A null or empty node selector term matches no objects. The requirements of them are ANDed. The TopologySelectorTerm type implements a subset of the NodeSelectorTerm.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindexmatchexpressionsindex">matchExpressions</a></b></td>
          <td>[]object</td>
          <td>
            A list of node selector requirements by node&#39;s labels.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindexmatchfieldsindex">matchFields</a></b></td>
          <td>[]object</td>
          <td>
            A list of node selector requirements by node&#39;s fields.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index].matchExpressions[index] {#edgeworkloadspecpodspecaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindexmatchexpressionsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex)</sup></sup>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            The label key that the selector applies to.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>operator</b></td>
          <td>string</td>
          <td>
            Represents a key&#39;s relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>values</b></td>
          <td>[]string</td>
          <td>
            An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index].matchFields[index] {#edgeworkloadspecpodspecaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindexmatchfieldsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex)</sup></sup>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            The label key that the selector applies to.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>operator</b></td>
          <td>string</td>
          <td>
            Represents a key&#39;s relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>values</b></td>
          <td>[]string</td>
          <td>
            An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAffinity {#edgeworkloadspecpodspecaffinitypodaffinity}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinity)</sup></sup>



Describes pod affinity scheduling rules (e.g. co-locate this pod in the same node, zone, etc. as some other pod(s)).
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindex">preferredDuringSchedulingIgnoredDuringExecution</a></b></td>
          <td>[]object</td>
          <td>
            The scheduler will prefer to schedule pods to nodes that satisfy the affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding &#34;weight&#34; to the sum if the node has pods which matches the corresponding podAffinityTerm; the node(s) with the highest sum are the most preferred.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">requiredDuringSchedulingIgnoredDuringExecution</a></b></td>
          <td>[]object</td>
          <td>
            If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to a pod label update), the system may or may not try to eventually evict the pod from its node. When there are multiple elements, the lists of nodes corresponding to each podAffinityTerm are intersected, i.e. all terms must be satisfied.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index] {#edgeworkloadspecpodspecaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodaffinity)</sup></sup>



The weights of all of the matched WeightedPodAffinityTerm fields are added per-node to find the most preferred node(s)
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">podAffinityTerm</a></b></td>
          <td>object</td>
          <td>
            Required. A pod affinity term, associated with the corresponding weight.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>weight</b></td>
          <td>integer</td>
          <td>
            weight associated with matching the corresponding podAffinityTerm, in the range 1-100.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm {#edgeworkloadspecpodspecaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindex)</sup></sup>



Required. A pod affinity term, associated with the corresponding weight.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>topologyKey</b></td>
          <td>string</td>
          <td>
            This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">labelSelector</a></b></td>
          <td>object</td>
          <td>
            A label query over a set of resources, in this case pods.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">namespaceSelector</a></b></td>
          <td>object</td>
          <td>
            A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means &#34;this pod&#39;s namespace&#34;. An empty selector ({}) matches all namespaces. This field is beta-level and is only honored when PodAffinityNamespaceSelector feature is enabled.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>namespaces</b></td>
          <td>[]string</td>
          <td>
            namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means &#34;this pod&#39;s namespace&#34;<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector {#edgeworkloadspecpodspecaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm)</sup></sup>



A label query over a set of resources, in this case pods.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselectormatchexpressionsindex">matchExpressions</a></b></td>
          <td>[]object</td>
          <td>
            matchExpressions is a list of label selector requirements. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>matchLabels</b></td>
          <td>map[string]string</td>
          <td>
            matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is &#34;key&#34;, the operator is &#34;In&#34;, and the values array contains only &#34;value&#34;. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector.matchExpressions[index] {#edgeworkloadspecpodspecaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselectormatchexpressionsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector)</sup></sup>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            key is the label key that the selector applies to.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>operator</b></td>
          <td>string</td>
          <td>
            operator represents a key&#39;s relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>values</b></td>
          <td>[]string</td>
          <td>
            values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector {#edgeworkloadspecpodspecaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm)</sup></sup>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means &#34;this pod&#39;s namespace&#34;. An empty selector ({}) matches all namespaces. This field is beta-level and is only honored when PodAffinityNamespaceSelector feature is enabled.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselectormatchexpressionsindex">matchExpressions</a></b></td>
          <td>[]object</td>
          <td>
            matchExpressions is a list of label selector requirements. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>matchLabels</b></td>
          <td>map[string]string</td>
          <td>
            matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is &#34;key&#34;, the operator is &#34;In&#34;, and the values array contains only &#34;value&#34;. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector.matchExpressions[index] {#edgeworkloadspecpodspecaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselectormatchexpressionsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector)</sup></sup>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            key is the label key that the selector applies to.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>operator</b></td>
          <td>string</td>
          <td>
            operator represents a key&#39;s relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>values</b></td>
          <td>[]string</td>
          <td>
            values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index] {#edgeworkloadspecpodspecaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodaffinity)</sup></sup>



Defines a set of pods (namely those matching the labelSelector relative to the given namespace(s)) that this pod should be co-located (affinity) or not co-located (anti-affinity) with, where co-located is defined as running on a node whose value of the label with key &lt;topologyKey&gt; matches that of any node on which a pod of the set of pods is running
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>topologyKey</b></td>
          <td>string</td>
          <td>
            This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">labelSelector</a></b></td>
          <td>object</td>
          <td>
            A label query over a set of resources, in this case pods.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">namespaceSelector</a></b></td>
          <td>object</td>
          <td>
            A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means &#34;this pod&#39;s namespace&#34;. An empty selector ({}) matches all namespaces. This field is beta-level and is only honored when PodAffinityNamespaceSelector feature is enabled.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>namespaces</b></td>
          <td>[]string</td>
          <td>
            namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means &#34;this pod&#39;s namespace&#34;<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector {#edgeworkloadspecpodspecaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex)</sup></sup>



A label query over a set of resources, in this case pods.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselectormatchexpressionsindex">matchExpressions</a></b></td>
          <td>[]object</td>
          <td>
            matchExpressions is a list of label selector requirements. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>matchLabels</b></td>
          <td>map[string]string</td>
          <td>
            matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is &#34;key&#34;, the operator is &#34;In&#34;, and the values array contains only &#34;value&#34;. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector.matchExpressions[index] {#edgeworkloadspecpodspecaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselectormatchexpressionsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector)</sup></sup>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            key is the label key that the selector applies to.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>operator</b></td>
          <td>string</td>
          <td>
            operator represents a key&#39;s relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>values</b></td>
          <td>[]string</td>
          <td>
            values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector {#edgeworkloadspecpodspecaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex)</sup></sup>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means &#34;this pod&#39;s namespace&#34;. An empty selector ({}) matches all namespaces. This field is beta-level and is only honored when PodAffinityNamespaceSelector feature is enabled.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselectormatchexpressionsindex">matchExpressions</a></b></td>
          <td>[]object</td>
          <td>
            matchExpressions is a list of label selector requirements. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>matchLabels</b></td>
          <td>map[string]string</td>
          <td>
            matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is &#34;key&#34;, the operator is &#34;In&#34;, and the values array contains only &#34;value&#34;. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector.matchExpressions[index] {#edgeworkloadspecpodspecaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselectormatchexpressionsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector)</sup></sup>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            key is the label key that the selector applies to.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>operator</b></td>
          <td>string</td>
          <td>
            operator represents a key&#39;s relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>values</b></td>
          <td>[]string</td>
          <td>
            values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAntiAffinity {#edgeworkloadspecpodspecaffinitypodantiaffinity}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinity)</sup></sup>



Describes pod anti-affinity scheduling rules (e.g. avoid putting this pod in the same node, zone, etc. as some other pod(s)).
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindex">preferredDuringSchedulingIgnoredDuringExecution</a></b></td>
          <td>[]object</td>
          <td>
            The scheduler will prefer to schedule pods to nodes that satisfy the anti-affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling anti-affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding &#34;weight&#34; to the sum if the node has pods which matches the corresponding podAffinityTerm; the node(s) with the highest sum are the most preferred.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">requiredDuringSchedulingIgnoredDuringExecution</a></b></td>
          <td>[]object</td>
          <td>
            If the anti-affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the anti-affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to a pod label update), the system may or may not try to eventually evict the pod from its node. When there are multiple elements, the lists of nodes corresponding to each podAffinityTerm are intersected, i.e. all terms must be satisfied.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index] {#edgeworkloadspecpodspecaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodantiaffinity)</sup></sup>



The weights of all of the matched WeightedPodAffinityTerm fields are added per-node to find the most preferred node(s)
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">podAffinityTerm</a></b></td>
          <td>object</td>
          <td>
            Required. A pod affinity term, associated with the corresponding weight.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>weight</b></td>
          <td>integer</td>
          <td>
            weight associated with matching the corresponding podAffinityTerm, in the range 1-100.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm {#edgeworkloadspecpodspecaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindex)</sup></sup>



Required. A pod affinity term, associated with the corresponding weight.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>topologyKey</b></td>
          <td>string</td>
          <td>
            This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">labelSelector</a></b></td>
          <td>object</td>
          <td>
            A label query over a set of resources, in this case pods.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">namespaceSelector</a></b></td>
          <td>object</td>
          <td>
            A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means &#34;this pod&#39;s namespace&#34;. An empty selector ({}) matches all namespaces. This field is beta-level and is only honored when PodAffinityNamespaceSelector feature is enabled.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>namespaces</b></td>
          <td>[]string</td>
          <td>
            namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means &#34;this pod&#39;s namespace&#34;<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector {#edgeworkloadspecpodspecaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm)</sup></sup>



A label query over a set of resources, in this case pods.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselectormatchexpressionsindex">matchExpressions</a></b></td>
          <td>[]object</td>
          <td>
            matchExpressions is a list of label selector requirements. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>matchLabels</b></td>
          <td>map[string]string</td>
          <td>
            matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is &#34;key&#34;, the operator is &#34;In&#34;, and the values array contains only &#34;value&#34;. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector.matchExpressions[index] {#edgeworkloadspecpodspecaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselectormatchexpressionsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector)</sup></sup>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            key is the label key that the selector applies to.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>operator</b></td>
          <td>string</td>
          <td>
            operator represents a key&#39;s relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>values</b></td>
          <td>[]string</td>
          <td>
            values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector {#edgeworkloadspecpodspecaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm)</sup></sup>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means &#34;this pod&#39;s namespace&#34;. An empty selector ({}) matches all namespaces. This field is beta-level and is only honored when PodAffinityNamespaceSelector feature is enabled.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselectormatchexpressionsindex">matchExpressions</a></b></td>
          <td>[]object</td>
          <td>
            matchExpressions is a list of label selector requirements. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>matchLabels</b></td>
          <td>map[string]string</td>
          <td>
            matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is &#34;key&#34;, the operator is &#34;In&#34;, and the values array contains only &#34;value&#34;. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector.matchExpressions[index] {#edgeworkloadspecpodspecaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselectormatchexpressionsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector)</sup></sup>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            key is the label key that the selector applies to.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>operator</b></td>
          <td>string</td>
          <td>
            operator represents a key&#39;s relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>values</b></td>
          <td>[]string</td>
          <td>
            values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index] {#edgeworkloadspecpodspecaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodantiaffinity)</sup></sup>



Defines a set of pods (namely those matching the labelSelector relative to the given namespace(s)) that this pod should be co-located (affinity) or not co-located (anti-affinity) with, where co-located is defined as running on a node whose value of the label with key &lt;topologyKey&gt; matches that of any node on which a pod of the set of pods is running
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>topologyKey</b></td>
          <td>string</td>
          <td>
            This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">labelSelector</a></b></td>
          <td>object</td>
          <td>
            A label query over a set of resources, in this case pods.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">namespaceSelector</a></b></td>
          <td>object</td>
          <td>
            A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means &#34;this pod&#39;s namespace&#34;. An empty selector ({}) matches all namespaces. This field is beta-level and is only honored when PodAffinityNamespaceSelector feature is enabled.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>namespaces</b></td>
          <td>[]string</td>
          <td>
            namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means &#34;this pod&#39;s namespace&#34;<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector {#edgeworkloadspecpodspecaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex)</sup></sup>



A label query over a set of resources, in this case pods.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselectormatchexpressionsindex">matchExpressions</a></b></td>
          <td>[]object</td>
          <td>
            matchExpressions is a list of label selector requirements. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>matchLabels</b></td>
          <td>map[string]string</td>
          <td>
            matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is &#34;key&#34;, the operator is &#34;In&#34;, and the values array contains only &#34;value&#34;. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector.matchExpressions[index] {#edgeworkloadspecpodspecaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselectormatchexpressionsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector)</sup></sup>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            key is the label key that the selector applies to.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>operator</b></td>
          <td>string</td>
          <td>
            operator represents a key&#39;s relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>values</b></td>
          <td>[]string</td>
          <td>
            values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector {#edgeworkloadspecpodspecaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex)</sup></sup>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means &#34;this pod&#39;s namespace&#34;. An empty selector ({}) matches all namespaces. This field is beta-level and is only honored when PodAffinityNamespaceSelector feature is enabled.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselectormatchexpressionsindex">matchExpressions</a></b></td>
          <td>[]object</td>
          <td>
            matchExpressions is a list of label selector requirements. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>matchLabels</b></td>
          <td>map[string]string</td>
          <td>
            matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is &#34;key&#34;, the operator is &#34;In&#34;, and the values array contains only &#34;value&#34;. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector.matchExpressions[index] {#edgeworkloadspecpodspecaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselectormatchexpressionsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector)</sup></sup>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            key is the label key that the selector applies to.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>operator</b></td>
          <td>string</td>
          <td>
            operator represents a key&#39;s relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>values</b></td>
          <td>[]string</td>
          <td>
            values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.dnsConfig {#edgeworkloadspecpodspecdnsconfig}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspec)</sup></sup>



Specifies the DNS parameters of a pod. Parameters specified here will be merged to the generated DNS configuration based on DNSPolicy.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>nameservers</b></td>
          <td>[]string</td>
          <td>
            A list of DNS name server IP addresses. This will be appended to the base nameservers generated from DNSPolicy. Duplicated nameservers will be removed.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecdnsconfigoptionsindex">options</a></b></td>
          <td>[]object</td>
          <td>
            A list of DNS resolver options. This will be merged with the base options generated from DNSPolicy. Duplicated entries will be removed. Resolution options given in Options will override those that appear in the base DNSPolicy.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>searches</b></td>
          <td>[]string</td>
          <td>
            A list of DNS search domains for host-name lookup. This will be appended to the base search paths generated from DNSPolicy. Duplicated search paths will be removed.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.dnsConfig.options[index] {#edgeworkloadspecpodspecdnsconfigoptionsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecdnsconfig)</sup></sup>



PodDNSConfigOption defines DNS resolver options of a pod.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Required.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index] {#edgeworkloadspecpodspecephemeralcontainersindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspec)</sup></sup>



An EphemeralContainer is a temporary container that you may add to an existing Pod for user-initiated activities such as debugging. Ephemeral containers have no resource or scheduling guarantees, and they will not be restarted when they exit or when a Pod is removed or restarted. The kubelet may evict a Pod if an ephemeral container causes the Pod to exceed its resource allocation. 
 To add an ephemeral container, use the ephemeralcontainers subresource of an existing Pod. Ephemeral containers may not be removed or restarted. 
 This is a beta feature available on clusters that haven&#39;t disabled the EphemeralContainers feature gate.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the ephemeral container specified as a DNS_LABEL. This name must be unique among all containers, init containers and ephemeral containers.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>args</b></td>
          <td>[]string</td>
          <td>
            Arguments to the entrypoint. The docker image&#39;s CMD is used if this is not provided. Variable references $(VAR_NAME) are expanded using the container&#39;s environment. If a variable cannot be resolved, the reference in the input string will be unchanged. Double $$ are reduced to a single $, which allows for escaping the $(VAR_NAME) syntax: i.e. &#34;$$(VAR_NAME)&#34; will produce the string literal &#34;$(VAR_NAME)&#34;. Escaped references will never be expanded, regardless of whether the variable exists or not. Cannot be updated. More info: https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/#running-a-command-in-a-shell<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>command</b></td>
          <td>[]string</td>
          <td>
            Entrypoint array. Not executed within a shell. The docker image&#39;s ENTRYPOINT is used if this is not provided. Variable references $(VAR_NAME) are expanded using the container&#39;s environment. If a variable cannot be resolved, the reference in the input string will be unchanged. Double $$ are reduced to a single $, which allows for escaping the $(VAR_NAME) syntax: i.e. &#34;$$(VAR_NAME)&#34; will produce the string literal &#34;$(VAR_NAME)&#34;. Escaped references will never be expanded, regardless of whether the variable exists or not. Cannot be updated. More info: https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/#running-a-command-in-a-shell<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexenvindex">env</a></b></td>
          <td>[]object</td>
          <td>
            List of environment variables to set in the container. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexenvfromindex">envFrom</a></b></td>
          <td>[]object</td>
          <td>
            List of sources to populate environment variables in the container. The keys defined within a source must be a C_IDENTIFIER. All invalid keys will be reported as an event when the container is starting. When a key exists in multiple sources, the value associated with the last source will take precedence. Values defined by an Env with a duplicate key will take precedence. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>image</b></td>
          <td>string</td>
          <td>
            Docker image name. More info: https://kubernetes.io/docs/concepts/containers/images<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>imagePullPolicy</b></td>
          <td>string</td>
          <td>
            Image pull policy. One of Always, Never, IfNotPresent. Defaults to Always if :latest tag is specified, or IfNotPresent otherwise. Cannot be updated. More info: https://kubernetes.io/docs/concepts/containers/images#updating-images<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexlifecycle">lifecycle</a></b></td>
          <td>object</td>
          <td>
            Lifecycle is not allowed for ephemeral containers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexlivenessprobe">livenessProbe</a></b></td>
          <td>object</td>
          <td>
            Probes are not allowed for ephemeral containers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexportsindex">ports</a></b></td>
          <td>[]object</td>
          <td>
            Ports are not allowed for ephemeral containers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexreadinessprobe">readinessProbe</a></b></td>
          <td>object</td>
          <td>
            Probes are not allowed for ephemeral containers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexresources">resources</a></b></td>
          <td>object</td>
          <td>
            Resources are not allowed for ephemeral containers. Ephemeral containers use spare resources already allocated to the pod.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexsecuritycontext">securityContext</a></b></td>
          <td>object</td>
          <td>
            Optional: SecurityContext defines the security options the ephemeral container should be run with. If set, the fields of SecurityContext override the equivalent fields of PodSecurityContext.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexstartupprobe">startupProbe</a></b></td>
          <td>object</td>
          <td>
            Probes are not allowed for ephemeral containers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>stdin</b></td>
          <td>boolean</td>
          <td>
            Whether this container should allocate a buffer for stdin in the container runtime. If this is not set, reads from stdin in the container will always result in EOF. Default is false.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>stdinOnce</b></td>
          <td>boolean</td>
          <td>
            Whether the container runtime should close the stdin channel after it has been opened by a single attach. When stdin is true the stdin stream will remain open across multiple attach sessions. If stdinOnce is set to true, stdin is opened on container start, is empty until the first client attaches to stdin, and then remains open and accepts data until the client disconnects, at which time stdin is closed and remains closed until the container is restarted. If this flag is false, a container processes that reads from stdin will never receive an EOF. Default is false<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>targetContainerName</b></td>
          <td>string</td>
          <td>
            If set, the name of the container from PodSpec that this ephemeral container targets. The ephemeral container will be run in the namespaces (IPC, PID, etc) of this container. If not set then the ephemeral container uses the namespaces configured in the Pod spec. 
 The container runtime must implement support for this feature. If the runtime does not support namespace targeting then the result of setting this field is undefined.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>terminationMessagePath</b></td>
          <td>string</td>
          <td>
            Optional: Path at which the file to which the container&#39;s termination message will be written is mounted into the container&#39;s filesystem. Message written is intended to be brief final status, such as an assertion failure message. Will be truncated by the node if greater than 4096 bytes. The total message length across all containers will be limited to 12kb. Defaults to /dev/termination-log. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>terminationMessagePolicy</b></td>
          <td>string</td>
          <td>
            Indicate how the termination message should be populated. File will use the contents of terminationMessagePath to populate the container status message on both success and failure. FallbackToLogsOnError will use the last chunk of container log output if the termination message file is empty and the container exited with an error. The log output is limited to 2048 bytes or 80 lines, whichever is smaller. Defaults to File. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>tty</b></td>
          <td>boolean</td>
          <td>
            Whether this container should allocate a TTY for itself, also requires &#39;stdin&#39; to be true. Default is false.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexvolumedevicesindex">volumeDevices</a></b></td>
          <td>[]object</td>
          <td>
            volumeDevices is the list of block devices to be used by the container.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexvolumemountsindex">volumeMounts</a></b></td>
          <td>[]object</td>
          <td>
            Pod volumes to mount into the container&#39;s filesystem. Subpath mounts are not allowed for ephemeral containers. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>workingDir</b></td>
          <td>string</td>
          <td>
            Container&#39;s working directory. If not specified, the container runtime&#39;s default will be used, which might be configured in the container image. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].env[index] {#edgeworkloadspecpodspecephemeralcontainersindexenvindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindex)</sup></sup>



EnvVar represents an environment variable present in a Container.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the environment variable. Must be a C_IDENTIFIER.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            Variable references $(VAR_NAME) are expanded using the previously defined environment variables in the container and any service environment variables. If a variable cannot be resolved, the reference in the input string will be unchanged. Double $$ are reduced to a single $, which allows for escaping the $(VAR_NAME) syntax: i.e. &#34;$$(VAR_NAME)&#34; will produce the string literal &#34;$(VAR_NAME)&#34;. Escaped references will never be expanded, regardless of whether the variable exists or not. Defaults to &#34;&#34;.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexenvindexvaluefrom">valueFrom</a></b></td>
          <td>object</td>
          <td>
            Source for the environment variable&#39;s value. Cannot be used if value is not empty.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].env[index].valueFrom {#edgeworkloadspecpodspecephemeralcontainersindexenvindexvaluefrom}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexenvindex)</sup></sup>



Source for the environment variable&#39;s value. Cannot be used if value is not empty.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexenvindexvaluefromconfigmapkeyref">configMapKeyRef</a></b></td>
          <td>object</td>
          <td>
            Selects a key of a ConfigMap.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexenvindexvaluefromfieldref">fieldRef</a></b></td>
          <td>object</td>
          <td>
            Selects a field of the pod: supports metadata.name, metadata.namespace, `metadata.labels[&#39;&lt;KEY&gt;&#39;]`, `metadata.annotations[&#39;&lt;KEY&gt;&#39;]`, spec.nodeName, spec.serviceAccountName, status.hostIP, status.podIP, status.podIPs.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexenvindexvaluefromresourcefieldref">resourceFieldRef</a></b></td>
          <td>object</td>
          <td>
            Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, limits.ephemeral-storage, requests.cpu, requests.memory and requests.ephemeral-storage) are currently supported.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexenvindexvaluefromsecretkeyref">secretKeyRef</a></b></td>
          <td>object</td>
          <td>
            Selects a key of a secret in the pod&#39;s namespace<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].env[index].valueFrom.configMapKeyRef {#edgeworkloadspecpodspecephemeralcontainersindexenvindexvaluefromconfigmapkeyref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexenvindexvaluefrom)</sup></sup>



Selects a key of a ConfigMap.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            The key to select.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>optional</b></td>
          <td>boolean</td>
          <td>
            Specify whether the ConfigMap or its key must be defined<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].env[index].valueFrom.fieldRef {#edgeworkloadspecpodspecephemeralcontainersindexenvindexvaluefromfieldref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexenvindexvaluefrom)</sup></sup>



Selects a field of the pod: supports metadata.name, metadata.namespace, `metadata.labels[&#39;&lt;KEY&gt;&#39;]`, `metadata.annotations[&#39;&lt;KEY&gt;&#39;]`, spec.nodeName, spec.serviceAccountName, status.hostIP, status.podIP, status.podIPs.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>fieldPath</b></td>
          <td>string</td>
          <td>
            Path of the field to select in the specified API version.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>apiVersion</b></td>
          <td>string</td>
          <td>
            Version of the schema the FieldPath is written in terms of, defaults to &#34;v1&#34;.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].env[index].valueFrom.resourceFieldRef {#edgeworkloadspecpodspecephemeralcontainersindexenvindexvaluefromresourcefieldref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexenvindexvaluefrom)</sup></sup>



Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, limits.ephemeral-storage, requests.cpu, requests.memory and requests.ephemeral-storage) are currently supported.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>resource</b></td>
          <td>string</td>
          <td>
            Required: resource to select<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>containerName</b></td>
          <td>string</td>
          <td>
            Container name: required for volumes, optional for env vars<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>divisor</b></td>
          <td>int or string</td>
          <td>
            Specifies the output format of the exposed resources, defaults to &#34;1&#34;<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].env[index].valueFrom.secretKeyRef {#edgeworkloadspecpodspecephemeralcontainersindexenvindexvaluefromsecretkeyref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexenvindexvaluefrom)</sup></sup>



Selects a key of a secret in the pod&#39;s namespace
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            The key of the secret to select from.  Must be a valid secret key.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>optional</b></td>
          <td>boolean</td>
          <td>
            Specify whether the Secret or its key must be defined<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].envFrom[index] {#edgeworkloadspecpodspecephemeralcontainersindexenvfromindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindex)</sup></sup>



EnvFromSource represents the source of a set of ConfigMaps
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexenvfromindexconfigmapref">configMapRef</a></b></td>
          <td>object</td>
          <td>
            The ConfigMap to select from<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>prefix</b></td>
          <td>string</td>
          <td>
            An optional identifier to prepend to each key in the ConfigMap. Must be a C_IDENTIFIER.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexenvfromindexsecretref">secretRef</a></b></td>
          <td>object</td>
          <td>
            The Secret to select from<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].envFrom[index].configMapRef {#edgeworkloadspecpodspecephemeralcontainersindexenvfromindexconfigmapref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexenvfromindex)</sup></sup>



The ConfigMap to select from
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>optional</b></td>
          <td>boolean</td>
          <td>
            Specify whether the ConfigMap must be defined<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].envFrom[index].secretRef {#edgeworkloadspecpodspecephemeralcontainersindexenvfromindexsecretref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexenvfromindex)</sup></sup>



The Secret to select from
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>optional</b></td>
          <td>boolean</td>
          <td>
            Specify whether the Secret must be defined<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].lifecycle {#edgeworkloadspecpodspecephemeralcontainersindexlifecycle}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindex)</sup></sup>



Lifecycle is not allowed for ephemeral containers.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexlifecyclepoststart">postStart</a></b></td>
          <td>object</td>
          <td>
            PostStart is called immediately after a container is created. If the handler fails, the container is terminated and restarted according to its restart policy. Other management of the container blocks until the hook completes. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexlifecycleprestop">preStop</a></b></td>
          <td>object</td>
          <td>
            PreStop is called immediately before a container is terminated due to an API request or management event such as liveness/startup probe failure, preemption, resource contention, etc. The handler is not called if the container crashes or exits. The Pod&#39;s termination grace period countdown begins before the PreStop hook is executed. Regardless of the outcome of the handler, the container will eventually terminate within the Pod&#39;s termination grace period (unless delayed by finalizers). Other management of the container blocks until the hook completes or until the termination grace period is reached. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].lifecycle.postStart {#edgeworkloadspecpodspecephemeralcontainersindexlifecyclepoststart}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexlifecycle)</sup></sup>



PostStart is called immediately after a container is created. If the handler fails, the container is terminated and restarted according to its restart policy. Other management of the container blocks until the hook completes. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexlifecyclepoststartexec">exec</a></b></td>
          <td>object</td>
          <td>
            Exec specifies the action to take.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexlifecyclepoststarthttpget">httpGet</a></b></td>
          <td>object</td>
          <td>
            HTTPGet specifies the http request to perform.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexlifecyclepoststarttcpsocket">tcpSocket</a></b></td>
          <td>object</td>
          <td>
            Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].lifecycle.postStart.exec {#edgeworkloadspecpodspecephemeralcontainersindexlifecyclepoststartexec}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexlifecyclepoststart)</sup></sup>



Exec specifies the action to take.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>command</b></td>
          <td>[]string</td>
          <td>
            Command is the command line to execute inside the container, the working directory for the command  is root (&#39;/&#39;) in the container&#39;s filesystem. The command is simply exec&#39;d, it is not run inside a shell, so traditional shell instructions (&#39;|&#39;, etc) won&#39;t work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].lifecycle.postStart.httpGet {#edgeworkloadspecpodspecephemeralcontainersindexlifecyclepoststarthttpget}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexlifecyclepoststart)</sup></sup>



HTTPGet specifies the http request to perform.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Host name to connect to, defaults to the pod IP. You probably want to set &#34;Host&#34; in httpHeaders instead.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexlifecyclepoststarthttpgethttpheadersindex">httpHeaders</a></b></td>
          <td>[]object</td>
          <td>
            Custom headers to set in the request. HTTP allows repeated headers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path to access on the HTTP server.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>scheme</b></td>
          <td>string</td>
          <td>
            Scheme to use for connecting to the host. Defaults to HTTP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].lifecycle.postStart.httpGet.httpHeaders[index] {#edgeworkloadspecpodspecephemeralcontainersindexlifecyclepoststarthttpgethttpheadersindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexlifecyclepoststarthttpget)</sup></sup>



HTTPHeader describes a custom header to be used in HTTP probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            The header field name<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            The header field value<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].lifecycle.postStart.tcpSocket {#edgeworkloadspecpodspecephemeralcontainersindexlifecyclepoststarttcpsocket}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexlifecyclepoststart)</sup></sup>



Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Optional: Host name to connect to, defaults to the pod IP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].lifecycle.preStop {#edgeworkloadspecpodspecephemeralcontainersindexlifecycleprestop}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexlifecycle)</sup></sup>



PreStop is called immediately before a container is terminated due to an API request or management event such as liveness/startup probe failure, preemption, resource contention, etc. The handler is not called if the container crashes or exits. The Pod&#39;s termination grace period countdown begins before the PreStop hook is executed. Regardless of the outcome of the handler, the container will eventually terminate within the Pod&#39;s termination grace period (unless delayed by finalizers). Other management of the container blocks until the hook completes or until the termination grace period is reached. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexlifecycleprestopexec">exec</a></b></td>
          <td>object</td>
          <td>
            Exec specifies the action to take.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexlifecycleprestophttpget">httpGet</a></b></td>
          <td>object</td>
          <td>
            HTTPGet specifies the http request to perform.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexlifecycleprestoptcpsocket">tcpSocket</a></b></td>
          <td>object</td>
          <td>
            Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].lifecycle.preStop.exec {#edgeworkloadspecpodspecephemeralcontainersindexlifecycleprestopexec}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexlifecycleprestop)</sup></sup>



Exec specifies the action to take.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>command</b></td>
          <td>[]string</td>
          <td>
            Command is the command line to execute inside the container, the working directory for the command  is root (&#39;/&#39;) in the container&#39;s filesystem. The command is simply exec&#39;d, it is not run inside a shell, so traditional shell instructions (&#39;|&#39;, etc) won&#39;t work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].lifecycle.preStop.httpGet {#edgeworkloadspecpodspecephemeralcontainersindexlifecycleprestophttpget}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexlifecycleprestop)</sup></sup>



HTTPGet specifies the http request to perform.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Host name to connect to, defaults to the pod IP. You probably want to set &#34;Host&#34; in httpHeaders instead.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexlifecycleprestophttpgethttpheadersindex">httpHeaders</a></b></td>
          <td>[]object</td>
          <td>
            Custom headers to set in the request. HTTP allows repeated headers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path to access on the HTTP server.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>scheme</b></td>
          <td>string</td>
          <td>
            Scheme to use for connecting to the host. Defaults to HTTP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].lifecycle.preStop.httpGet.httpHeaders[index] {#edgeworkloadspecpodspecephemeralcontainersindexlifecycleprestophttpgethttpheadersindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexlifecycleprestophttpget)</sup></sup>



HTTPHeader describes a custom header to be used in HTTP probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            The header field name<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            The header field value<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].lifecycle.preStop.tcpSocket {#edgeworkloadspecpodspecephemeralcontainersindexlifecycleprestoptcpsocket}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexlifecycleprestop)</sup></sup>



Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Optional: Host name to connect to, defaults to the pod IP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].livenessProbe {#edgeworkloadspecpodspecephemeralcontainersindexlivenessprobe}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindex)</sup></sup>



Probes are not allowed for ephemeral containers.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexlivenessprobeexec">exec</a></b></td>
          <td>object</td>
          <td>
            Exec specifies the action to take.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>failureThreshold</b></td>
          <td>integer</td>
          <td>
            Minimum consecutive failures for the probe to be considered failed after having succeeded. Defaults to 3. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexlivenessprobegrpc">grpc</a></b></td>
          <td>object</td>
          <td>
            GRPC specifies an action involving a GRPC port. This is an alpha field and requires enabling GRPCContainerProbe feature gate.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexlivenessprobehttpget">httpGet</a></b></td>
          <td>object</td>
          <td>
            HTTPGet specifies the http request to perform.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>initialDelaySeconds</b></td>
          <td>integer</td>
          <td>
            Number of seconds after the container has started before liveness probes are initiated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>periodSeconds</b></td>
          <td>integer</td>
          <td>
            How often (in seconds) to perform the probe. Default to 10 seconds. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>successThreshold</b></td>
          <td>integer</td>
          <td>
            Minimum consecutive successes for the probe to be considered successful after having failed. Defaults to 1. Must be 1 for liveness and startup. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexlivenessprobetcpsocket">tcpSocket</a></b></td>
          <td>object</td>
          <td>
            TCPSocket specifies an action involving a TCP port.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>terminationGracePeriodSeconds</b></td>
          <td>integer</td>
          <td>
            Optional duration in seconds the pod needs to terminate gracefully upon probe failure. The grace period is the duration in seconds after the processes running in the pod are sent a termination signal and the time when the processes are forcibly halted with a kill signal. Set this value longer than the expected cleanup time for your process. If this value is nil, the pod&#39;s terminationGracePeriodSeconds will be used. Otherwise, this value overrides the value provided by the pod spec. Value must be non-negative integer. The value zero indicates stop immediately via the kill signal (no opportunity to shut down). This is a beta field and requires enabling ProbeTerminationGracePeriod feature gate. Minimum value is 1. spec.terminationGracePeriodSeconds is used if unset.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>timeoutSeconds</b></td>
          <td>integer</td>
          <td>
            Number of seconds after which the probe times out. Defaults to 1 second. Minimum value is 1. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].livenessProbe.exec {#edgeworkloadspecpodspecephemeralcontainersindexlivenessprobeexec}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexlivenessprobe)</sup></sup>



Exec specifies the action to take.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>command</b></td>
          <td>[]string</td>
          <td>
            Command is the command line to execute inside the container, the working directory for the command  is root (&#39;/&#39;) in the container&#39;s filesystem. The command is simply exec&#39;d, it is not run inside a shell, so traditional shell instructions (&#39;|&#39;, etc) won&#39;t work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].livenessProbe.grpc {#edgeworkloadspecpodspecephemeralcontainersindexlivenessprobegrpc}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexlivenessprobe)</sup></sup>



GRPC specifies an action involving a GRPC port. This is an alpha field and requires enabling GRPCContainerProbe feature gate.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>integer</td>
          <td>
            Port number of the gRPC service. Number must be in the range 1 to 65535.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>service</b></td>
          <td>string</td>
          <td>
            Service is the name of the service to place in the gRPC HealthCheckRequest (see https://github.com/grpc/grpc/blob/master/doc/health-checking.md). 
 If this is not specified, the default behavior is defined by gRPC.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].livenessProbe.httpGet {#edgeworkloadspecpodspecephemeralcontainersindexlivenessprobehttpget}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexlivenessprobe)</sup></sup>



HTTPGet specifies the http request to perform.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Host name to connect to, defaults to the pod IP. You probably want to set &#34;Host&#34; in httpHeaders instead.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexlivenessprobehttpgethttpheadersindex">httpHeaders</a></b></td>
          <td>[]object</td>
          <td>
            Custom headers to set in the request. HTTP allows repeated headers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path to access on the HTTP server.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>scheme</b></td>
          <td>string</td>
          <td>
            Scheme to use for connecting to the host. Defaults to HTTP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].livenessProbe.httpGet.httpHeaders[index] {#edgeworkloadspecpodspecephemeralcontainersindexlivenessprobehttpgethttpheadersindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexlivenessprobehttpget)</sup></sup>



HTTPHeader describes a custom header to be used in HTTP probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            The header field name<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            The header field value<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].livenessProbe.tcpSocket {#edgeworkloadspecpodspecephemeralcontainersindexlivenessprobetcpsocket}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexlivenessprobe)</sup></sup>



TCPSocket specifies an action involving a TCP port.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Optional: Host name to connect to, defaults to the pod IP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].ports[index] {#edgeworkloadspecpodspecephemeralcontainersindexportsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindex)</sup></sup>



ContainerPort represents a network port in a single container.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>containerPort</b></td>
          <td>integer</td>
          <td>
            Number of port to expose on the pod&#39;s IP address. This must be a valid port number, 0 &lt; x &lt; 65536.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>hostIP</b></td>
          <td>string</td>
          <td>
            What host IP to bind the external port to.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>hostPort</b></td>
          <td>integer</td>
          <td>
            Number of port to expose on the host. If specified, this must be a valid port number, 0 &lt; x &lt; 65536. If HostNetwork is specified, this must match ContainerPort. Most containers do not need this.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            If specified, this must be an IANA_SVC_NAME and unique within the pod. Each named port in a pod must have a unique name. Name for the port that can be referred to by services.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>protocol</b></td>
          <td>string</td>
          <td>
            Protocol for port. Must be UDP, TCP, or SCTP. Defaults to &#34;TCP&#34;.<br/>
            <br/>
              <i>Default</i>: TCP<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].readinessProbe {#edgeworkloadspecpodspecephemeralcontainersindexreadinessprobe}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindex)</sup></sup>



Probes are not allowed for ephemeral containers.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexreadinessprobeexec">exec</a></b></td>
          <td>object</td>
          <td>
            Exec specifies the action to take.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>failureThreshold</b></td>
          <td>integer</td>
          <td>
            Minimum consecutive failures for the probe to be considered failed after having succeeded. Defaults to 3. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexreadinessprobegrpc">grpc</a></b></td>
          <td>object</td>
          <td>
            GRPC specifies an action involving a GRPC port. This is an alpha field and requires enabling GRPCContainerProbe feature gate.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexreadinessprobehttpget">httpGet</a></b></td>
          <td>object</td>
          <td>
            HTTPGet specifies the http request to perform.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>initialDelaySeconds</b></td>
          <td>integer</td>
          <td>
            Number of seconds after the container has started before liveness probes are initiated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>periodSeconds</b></td>
          <td>integer</td>
          <td>
            How often (in seconds) to perform the probe. Default to 10 seconds. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>successThreshold</b></td>
          <td>integer</td>
          <td>
            Minimum consecutive successes for the probe to be considered successful after having failed. Defaults to 1. Must be 1 for liveness and startup. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexreadinessprobetcpsocket">tcpSocket</a></b></td>
          <td>object</td>
          <td>
            TCPSocket specifies an action involving a TCP port.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>terminationGracePeriodSeconds</b></td>
          <td>integer</td>
          <td>
            Optional duration in seconds the pod needs to terminate gracefully upon probe failure. The grace period is the duration in seconds after the processes running in the pod are sent a termination signal and the time when the processes are forcibly halted with a kill signal. Set this value longer than the expected cleanup time for your process. If this value is nil, the pod&#39;s terminationGracePeriodSeconds will be used. Otherwise, this value overrides the value provided by the pod spec. Value must be non-negative integer. The value zero indicates stop immediately via the kill signal (no opportunity to shut down). This is a beta field and requires enabling ProbeTerminationGracePeriod feature gate. Minimum value is 1. spec.terminationGracePeriodSeconds is used if unset.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>timeoutSeconds</b></td>
          <td>integer</td>
          <td>
            Number of seconds after which the probe times out. Defaults to 1 second. Minimum value is 1. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].readinessProbe.exec {#edgeworkloadspecpodspecephemeralcontainersindexreadinessprobeexec}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexreadinessprobe)</sup></sup>



Exec specifies the action to take.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>command</b></td>
          <td>[]string</td>
          <td>
            Command is the command line to execute inside the container, the working directory for the command  is root (&#39;/&#39;) in the container&#39;s filesystem. The command is simply exec&#39;d, it is not run inside a shell, so traditional shell instructions (&#39;|&#39;, etc) won&#39;t work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].readinessProbe.grpc {#edgeworkloadspecpodspecephemeralcontainersindexreadinessprobegrpc}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexreadinessprobe)</sup></sup>



GRPC specifies an action involving a GRPC port. This is an alpha field and requires enabling GRPCContainerProbe feature gate.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>integer</td>
          <td>
            Port number of the gRPC service. Number must be in the range 1 to 65535.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>service</b></td>
          <td>string</td>
          <td>
            Service is the name of the service to place in the gRPC HealthCheckRequest (see https://github.com/grpc/grpc/blob/master/doc/health-checking.md). 
 If this is not specified, the default behavior is defined by gRPC.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].readinessProbe.httpGet {#edgeworkloadspecpodspecephemeralcontainersindexreadinessprobehttpget}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexreadinessprobe)</sup></sup>



HTTPGet specifies the http request to perform.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Host name to connect to, defaults to the pod IP. You probably want to set &#34;Host&#34; in httpHeaders instead.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexreadinessprobehttpgethttpheadersindex">httpHeaders</a></b></td>
          <td>[]object</td>
          <td>
            Custom headers to set in the request. HTTP allows repeated headers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path to access on the HTTP server.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>scheme</b></td>
          <td>string</td>
          <td>
            Scheme to use for connecting to the host. Defaults to HTTP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].readinessProbe.httpGet.httpHeaders[index] {#edgeworkloadspecpodspecephemeralcontainersindexreadinessprobehttpgethttpheadersindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexreadinessprobehttpget)</sup></sup>



HTTPHeader describes a custom header to be used in HTTP probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            The header field name<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            The header field value<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].readinessProbe.tcpSocket {#edgeworkloadspecpodspecephemeralcontainersindexreadinessprobetcpsocket}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexreadinessprobe)</sup></sup>



TCPSocket specifies an action involving a TCP port.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Optional: Host name to connect to, defaults to the pod IP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].resources {#edgeworkloadspecpodspecephemeralcontainersindexresources}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindex)</sup></sup>



Resources are not allowed for ephemeral containers. Ephemeral containers use spare resources already allocated to the pod.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>limits</b></td>
          <td>map[string]int or string</td>
          <td>
            Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>requests</b></td>
          <td>map[string]int or string</td>
          <td>
            Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].securityContext {#edgeworkloadspecpodspecephemeralcontainersindexsecuritycontext}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindex)</sup></sup>



Optional: SecurityContext defines the security options the ephemeral container should be run with. If set, the fields of SecurityContext override the equivalent fields of PodSecurityContext.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>allowPrivilegeEscalation</b></td>
          <td>boolean</td>
          <td>
            AllowPrivilegeEscalation controls whether a process can gain more privileges than its parent process. This bool directly controls if the no_new_privs flag will be set on the container process. AllowPrivilegeEscalation is true always when the container is: 1) run as Privileged 2) has CAP_SYS_ADMIN Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexsecuritycontextcapabilities">capabilities</a></b></td>
          <td>object</td>
          <td>
            The capabilities to add/drop when running containers. Defaults to the default set of capabilities granted by the container runtime. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>privileged</b></td>
          <td>boolean</td>
          <td>
            Run container in privileged mode. Processes in privileged containers are essentially equivalent to root on the host. Defaults to false. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>procMount</b></td>
          <td>string</td>
          <td>
            procMount denotes the type of proc mount to use for the containers. The default is DefaultProcMount which uses the container runtime defaults for readonly paths and masked paths. This requires the ProcMountType feature flag to be enabled. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnlyRootFilesystem</b></td>
          <td>boolean</td>
          <td>
            Whether this container has a read-only root filesystem. Default is false. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>runAsGroup</b></td>
          <td>integer</td>
          <td>
            The GID to run the entrypoint of the container process. Uses runtime default if unset. May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>runAsNonRoot</b></td>
          <td>boolean</td>
          <td>
            Indicates that the container must run as a non-root user. If true, the Kubelet will validate the image at runtime to ensure that it does not run as UID 0 (root) and fail to start the container if it does. If unset or false, no such validation will be performed. May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>runAsUser</b></td>
          <td>integer</td>
          <td>
            The UID to run the entrypoint of the container process. Defaults to user specified in image metadata if unspecified. May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexsecuritycontextselinuxoptions">seLinuxOptions</a></b></td>
          <td>object</td>
          <td>
            The SELinux context to be applied to the container. If unspecified, the container runtime will allocate a random SELinux context for each container.  May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexsecuritycontextseccompprofile">seccompProfile</a></b></td>
          <td>object</td>
          <td>
            The seccomp options to use by this container. If seccomp options are provided at both the pod &amp; container level, the container options override the pod options. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexsecuritycontextwindowsoptions">windowsOptions</a></b></td>
          <td>object</td>
          <td>
            The Windows specific settings applied to all containers. If unspecified, the options from the PodSecurityContext will be used. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is linux.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].securityContext.capabilities {#edgeworkloadspecpodspecephemeralcontainersindexsecuritycontextcapabilities}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexsecuritycontext)</sup></sup>



The capabilities to add/drop when running containers. Defaults to the default set of capabilities granted by the container runtime. Note that this field cannot be set when spec.os.name is windows.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>add</b></td>
          <td>[]string</td>
          <td>
            Added capabilities<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>drop</b></td>
          <td>[]string</td>
          <td>
            Removed capabilities<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].securityContext.seLinuxOptions {#edgeworkloadspecpodspecephemeralcontainersindexsecuritycontextselinuxoptions}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexsecuritycontext)</sup></sup>



The SELinux context to be applied to the container. If unspecified, the container runtime will allocate a random SELinux context for each container.  May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>level</b></td>
          <td>string</td>
          <td>
            Level is SELinux level label that applies to the container.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>role</b></td>
          <td>string</td>
          <td>
            Role is a SELinux role label that applies to the container.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>type</b></td>
          <td>string</td>
          <td>
            Type is a SELinux type label that applies to the container.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>user</b></td>
          <td>string</td>
          <td>
            User is a SELinux user label that applies to the container.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].securityContext.seccompProfile {#edgeworkloadspecpodspecephemeralcontainersindexsecuritycontextseccompprofile}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexsecuritycontext)</sup></sup>



The seccomp options to use by this container. If seccomp options are provided at both the pod &amp; container level, the container options override the pod options. Note that this field cannot be set when spec.os.name is windows.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>type</b></td>
          <td>string</td>
          <td>
            type indicates which kind of seccomp profile will be applied. Valid options are: 
 Localhost - a profile defined in a file on the node should be used. RuntimeDefault - the container runtime default profile should be used. Unconfined - no profile should be applied.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>localhostProfile</b></td>
          <td>string</td>
          <td>
            localhostProfile indicates a profile defined in a file on the node should be used. The profile must be preconfigured on the node to work. Must be a descending path, relative to the kubelet&#39;s configured seccomp profile location. Must only be set if type is &#34;Localhost&#34;.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].securityContext.windowsOptions {#edgeworkloadspecpodspecephemeralcontainersindexsecuritycontextwindowsoptions}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexsecuritycontext)</sup></sup>



The Windows specific settings applied to all containers. If unspecified, the options from the PodSecurityContext will be used. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is linux.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>gmsaCredentialSpec</b></td>
          <td>string</td>
          <td>
            GMSACredentialSpec is where the GMSA admission webhook (https://github.com/kubernetes-sigs/windows-gmsa) inlines the contents of the GMSA credential spec named by the GMSACredentialSpecName field.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>gmsaCredentialSpecName</b></td>
          <td>string</td>
          <td>
            GMSACredentialSpecName is the name of the GMSA credential spec to use.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>hostProcess</b></td>
          <td>boolean</td>
          <td>
            HostProcess determines if a container should be run as a &#39;Host Process&#39; container. This field is alpha-level and will only be honored by components that enable the WindowsHostProcessContainers feature flag. Setting this field without the feature flag will result in errors when validating the Pod. All of a Pod&#39;s containers must have the same effective HostProcess value (it is not allowed to have a mix of HostProcess containers and non-HostProcess containers).  In addition, if HostProcess is true then HostNetwork must also be set to true.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>runAsUserName</b></td>
          <td>string</td>
          <td>
            The UserName in Windows to run the entrypoint of the container process. Defaults to the user specified in image metadata if unspecified. May also be set in PodSecurityContext. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].startupProbe {#edgeworkloadspecpodspecephemeralcontainersindexstartupprobe}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindex)</sup></sup>



Probes are not allowed for ephemeral containers.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexstartupprobeexec">exec</a></b></td>
          <td>object</td>
          <td>
            Exec specifies the action to take.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>failureThreshold</b></td>
          <td>integer</td>
          <td>
            Minimum consecutive failures for the probe to be considered failed after having succeeded. Defaults to 3. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexstartupprobegrpc">grpc</a></b></td>
          <td>object</td>
          <td>
            GRPC specifies an action involving a GRPC port. This is an alpha field and requires enabling GRPCContainerProbe feature gate.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexstartupprobehttpget">httpGet</a></b></td>
          <td>object</td>
          <td>
            HTTPGet specifies the http request to perform.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>initialDelaySeconds</b></td>
          <td>integer</td>
          <td>
            Number of seconds after the container has started before liveness probes are initiated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>periodSeconds</b></td>
          <td>integer</td>
          <td>
            How often (in seconds) to perform the probe. Default to 10 seconds. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>successThreshold</b></td>
          <td>integer</td>
          <td>
            Minimum consecutive successes for the probe to be considered successful after having failed. Defaults to 1. Must be 1 for liveness and startup. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexstartupprobetcpsocket">tcpSocket</a></b></td>
          <td>object</td>
          <td>
            TCPSocket specifies an action involving a TCP port.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>terminationGracePeriodSeconds</b></td>
          <td>integer</td>
          <td>
            Optional duration in seconds the pod needs to terminate gracefully upon probe failure. The grace period is the duration in seconds after the processes running in the pod are sent a termination signal and the time when the processes are forcibly halted with a kill signal. Set this value longer than the expected cleanup time for your process. If this value is nil, the pod&#39;s terminationGracePeriodSeconds will be used. Otherwise, this value overrides the value provided by the pod spec. Value must be non-negative integer. The value zero indicates stop immediately via the kill signal (no opportunity to shut down). This is a beta field and requires enabling ProbeTerminationGracePeriod feature gate. Minimum value is 1. spec.terminationGracePeriodSeconds is used if unset.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>timeoutSeconds</b></td>
          <td>integer</td>
          <td>
            Number of seconds after which the probe times out. Defaults to 1 second. Minimum value is 1. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].startupProbe.exec {#edgeworkloadspecpodspecephemeralcontainersindexstartupprobeexec}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexstartupprobe)</sup></sup>



Exec specifies the action to take.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>command</b></td>
          <td>[]string</td>
          <td>
            Command is the command line to execute inside the container, the working directory for the command  is root (&#39;/&#39;) in the container&#39;s filesystem. The command is simply exec&#39;d, it is not run inside a shell, so traditional shell instructions (&#39;|&#39;, etc) won&#39;t work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].startupProbe.grpc {#edgeworkloadspecpodspecephemeralcontainersindexstartupprobegrpc}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexstartupprobe)</sup></sup>



GRPC specifies an action involving a GRPC port. This is an alpha field and requires enabling GRPCContainerProbe feature gate.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>integer</td>
          <td>
            Port number of the gRPC service. Number must be in the range 1 to 65535.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>service</b></td>
          <td>string</td>
          <td>
            Service is the name of the service to place in the gRPC HealthCheckRequest (see https://github.com/grpc/grpc/blob/master/doc/health-checking.md). 
 If this is not specified, the default behavior is defined by gRPC.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].startupProbe.httpGet {#edgeworkloadspecpodspecephemeralcontainersindexstartupprobehttpget}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexstartupprobe)</sup></sup>



HTTPGet specifies the http request to perform.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Host name to connect to, defaults to the pod IP. You probably want to set &#34;Host&#34; in httpHeaders instead.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecephemeralcontainersindexstartupprobehttpgethttpheadersindex">httpHeaders</a></b></td>
          <td>[]object</td>
          <td>
            Custom headers to set in the request. HTTP allows repeated headers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path to access on the HTTP server.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>scheme</b></td>
          <td>string</td>
          <td>
            Scheme to use for connecting to the host. Defaults to HTTP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].startupProbe.httpGet.httpHeaders[index] {#edgeworkloadspecpodspecephemeralcontainersindexstartupprobehttpgethttpheadersindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexstartupprobehttpget)</sup></sup>



HTTPHeader describes a custom header to be used in HTTP probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            The header field name<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            The header field value<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].startupProbe.tcpSocket {#edgeworkloadspecpodspecephemeralcontainersindexstartupprobetcpsocket}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindexstartupprobe)</sup></sup>



TCPSocket specifies an action involving a TCP port.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Optional: Host name to connect to, defaults to the pod IP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].volumeDevices[index] {#edgeworkloadspecpodspecephemeralcontainersindexvolumedevicesindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindex)</sup></sup>



volumeDevice describes a mapping of a raw block device within a container.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>devicePath</b></td>
          <td>string</td>
          <td>
            devicePath is the path inside of the container that the device will be mapped to.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            name must match the name of a persistentVolumeClaim in the pod<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.ephemeralContainers[index].volumeMounts[index] {#edgeworkloadspecpodspecephemeralcontainersindexvolumemountsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecephemeralcontainersindex)</sup></sup>



VolumeMount describes a mounting of a Volume within a container.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>mountPath</b></td>
          <td>string</td>
          <td>
            Path within the container at which the volume should be mounted.  Must not contain &#39;:&#39;.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            This must match the Name of a Volume.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>mountPropagation</b></td>
          <td>string</td>
          <td>
            mountPropagation determines how mounts are propagated from the host to container and the other way around. When not set, MountPropagationNone is used. This field is beta in 1.10.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            Mounted read-only if true, read-write otherwise (false or unspecified). Defaults to false.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>subPath</b></td>
          <td>string</td>
          <td>
            Path within the volume from which the container&#39;s volume should be mounted. Defaults to &#34;&#34; (volume&#39;s root).<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>subPathExpr</b></td>
          <td>string</td>
          <td>
            Expanded path within the volume from which the container&#39;s volume should be mounted. Behaves similarly to SubPath but environment variable references $(VAR_NAME) are expanded using the container&#39;s environment. Defaults to &#34;&#34; (volume&#39;s root). SubPathExpr and SubPath are mutually exclusive.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.hostAliases[index] {#edgeworkloadspecpodspechostaliasesindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspec)</sup></sup>



HostAlias holds the mapping between IP and hostnames that will be injected as an entry in the pod&#39;s hosts file.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>hostnames</b></td>
          <td>[]string</td>
          <td>
            Hostnames for the above IP address.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>ip</b></td>
          <td>string</td>
          <td>
            IP address of the host file entry.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.imagePullSecrets[index] {#edgeworkloadspecpodspecimagepullsecretsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspec)</sup></sup>



LocalObjectReference contains enough information to let you locate the referenced object inside the same namespace.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index] {#edgeworkloadspecpodspecinitcontainersindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspec)</sup></sup>



A single application container that you want to run within a pod.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the container specified as a DNS_LABEL. Each container in a pod must have a unique name (DNS_LABEL). Cannot be updated.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>args</b></td>
          <td>[]string</td>
          <td>
            Arguments to the entrypoint. The docker image&#39;s CMD is used if this is not provided. Variable references $(VAR_NAME) are expanded using the container&#39;s environment. If a variable cannot be resolved, the reference in the input string will be unchanged. Double $$ are reduced to a single $, which allows for escaping the $(VAR_NAME) syntax: i.e. &#34;$$(VAR_NAME)&#34; will produce the string literal &#34;$(VAR_NAME)&#34;. Escaped references will never be expanded, regardless of whether the variable exists or not. Cannot be updated. More info: https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/#running-a-command-in-a-shell<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>command</b></td>
          <td>[]string</td>
          <td>
            Entrypoint array. Not executed within a shell. The docker image&#39;s ENTRYPOINT is used if this is not provided. Variable references $(VAR_NAME) are expanded using the container&#39;s environment. If a variable cannot be resolved, the reference in the input string will be unchanged. Double $$ are reduced to a single $, which allows for escaping the $(VAR_NAME) syntax: i.e. &#34;$$(VAR_NAME)&#34; will produce the string literal &#34;$(VAR_NAME)&#34;. Escaped references will never be expanded, regardless of whether the variable exists or not. Cannot be updated. More info: https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/#running-a-command-in-a-shell<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexenvindex">env</a></b></td>
          <td>[]object</td>
          <td>
            List of environment variables to set in the container. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexenvfromindex">envFrom</a></b></td>
          <td>[]object</td>
          <td>
            List of sources to populate environment variables in the container. The keys defined within a source must be a C_IDENTIFIER. All invalid keys will be reported as an event when the container is starting. When a key exists in multiple sources, the value associated with the last source will take precedence. Values defined by an Env with a duplicate key will take precedence. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>image</b></td>
          <td>string</td>
          <td>
            Docker image name. More info: https://kubernetes.io/docs/concepts/containers/images This field is optional to allow higher level config management to default or override container images in workload controllers like Deployments and StatefulSets.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>imagePullPolicy</b></td>
          <td>string</td>
          <td>
            Image pull policy. One of Always, Never, IfNotPresent. Defaults to Always if :latest tag is specified, or IfNotPresent otherwise. Cannot be updated. More info: https://kubernetes.io/docs/concepts/containers/images#updating-images<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexlifecycle">lifecycle</a></b></td>
          <td>object</td>
          <td>
            Actions that the management system should take in response to container lifecycle events. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexlivenessprobe">livenessProbe</a></b></td>
          <td>object</td>
          <td>
            Periodic probe of container liveness. Container will be restarted if the probe fails. Cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexportsindex">ports</a></b></td>
          <td>[]object</td>
          <td>
            List of ports to expose from the container. Exposing a port here gives the system additional information about the network connections a container uses, but is primarily informational. Not specifying a port here DOES NOT prevent that port from being exposed. Any port which is listening on the default &#34;0.0.0.0&#34; address inside a container will be accessible from the network. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexreadinessprobe">readinessProbe</a></b></td>
          <td>object</td>
          <td>
            Periodic probe of container service readiness. Container will be removed from service endpoints if the probe fails. Cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexresources">resources</a></b></td>
          <td>object</td>
          <td>
            Compute Resources required by this container. Cannot be updated. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexsecuritycontext">securityContext</a></b></td>
          <td>object</td>
          <td>
            SecurityContext defines the security options the container should be run with. If set, the fields of SecurityContext override the equivalent fields of PodSecurityContext. More info: https://kubernetes.io/docs/tasks/configure-pod-container/security-context/<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexstartupprobe">startupProbe</a></b></td>
          <td>object</td>
          <td>
            StartupProbe indicates that the Pod has successfully initialized. If specified, no other probes are executed until this completes successfully. If this probe fails, the Pod will be restarted, just as if the livenessProbe failed. This can be used to provide different probe parameters at the beginning of a Pod&#39;s lifecycle, when it might take a long time to load data or warm a cache, than during steady-state operation. This cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>stdin</b></td>
          <td>boolean</td>
          <td>
            Whether this container should allocate a buffer for stdin in the container runtime. If this is not set, reads from stdin in the container will always result in EOF. Default is false.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>stdinOnce</b></td>
          <td>boolean</td>
          <td>
            Whether the container runtime should close the stdin channel after it has been opened by a single attach. When stdin is true the stdin stream will remain open across multiple attach sessions. If stdinOnce is set to true, stdin is opened on container start, is empty until the first client attaches to stdin, and then remains open and accepts data until the client disconnects, at which time stdin is closed and remains closed until the container is restarted. If this flag is false, a container processes that reads from stdin will never receive an EOF. Default is false<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>terminationMessagePath</b></td>
          <td>string</td>
          <td>
            Optional: Path at which the file to which the container&#39;s termination message will be written is mounted into the container&#39;s filesystem. Message written is intended to be brief final status, such as an assertion failure message. Will be truncated by the node if greater than 4096 bytes. The total message length across all containers will be limited to 12kb. Defaults to /dev/termination-log. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>terminationMessagePolicy</b></td>
          <td>string</td>
          <td>
            Indicate how the termination message should be populated. File will use the contents of terminationMessagePath to populate the container status message on both success and failure. FallbackToLogsOnError will use the last chunk of container log output if the termination message file is empty and the container exited with an error. The log output is limited to 2048 bytes or 80 lines, whichever is smaller. Defaults to File. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>tty</b></td>
          <td>boolean</td>
          <td>
            Whether this container should allocate a TTY for itself, also requires &#39;stdin&#39; to be true. Default is false.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexvolumedevicesindex">volumeDevices</a></b></td>
          <td>[]object</td>
          <td>
            volumeDevices is the list of block devices to be used by the container.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexvolumemountsindex">volumeMounts</a></b></td>
          <td>[]object</td>
          <td>
            Pod volumes to mount into the container&#39;s filesystem. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>workingDir</b></td>
          <td>string</td>
          <td>
            Container&#39;s working directory. If not specified, the container runtime&#39;s default will be used, which might be configured in the container image. Cannot be updated.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].env[index] {#edgeworkloadspecpodspecinitcontainersindexenvindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindex)</sup></sup>



EnvVar represents an environment variable present in a Container.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the environment variable. Must be a C_IDENTIFIER.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            Variable references $(VAR_NAME) are expanded using the previously defined environment variables in the container and any service environment variables. If a variable cannot be resolved, the reference in the input string will be unchanged. Double $$ are reduced to a single $, which allows for escaping the $(VAR_NAME) syntax: i.e. &#34;$$(VAR_NAME)&#34; will produce the string literal &#34;$(VAR_NAME)&#34;. Escaped references will never be expanded, regardless of whether the variable exists or not. Defaults to &#34;&#34;.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexenvindexvaluefrom">valueFrom</a></b></td>
          <td>object</td>
          <td>
            Source for the environment variable&#39;s value. Cannot be used if value is not empty.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].env[index].valueFrom {#edgeworkloadspecpodspecinitcontainersindexenvindexvaluefrom}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexenvindex)</sup></sup>



Source for the environment variable&#39;s value. Cannot be used if value is not empty.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexenvindexvaluefromconfigmapkeyref">configMapKeyRef</a></b></td>
          <td>object</td>
          <td>
            Selects a key of a ConfigMap.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexenvindexvaluefromfieldref">fieldRef</a></b></td>
          <td>object</td>
          <td>
            Selects a field of the pod: supports metadata.name, metadata.namespace, `metadata.labels[&#39;&lt;KEY&gt;&#39;]`, `metadata.annotations[&#39;&lt;KEY&gt;&#39;]`, spec.nodeName, spec.serviceAccountName, status.hostIP, status.podIP, status.podIPs.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexenvindexvaluefromresourcefieldref">resourceFieldRef</a></b></td>
          <td>object</td>
          <td>
            Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, limits.ephemeral-storage, requests.cpu, requests.memory and requests.ephemeral-storage) are currently supported.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexenvindexvaluefromsecretkeyref">secretKeyRef</a></b></td>
          <td>object</td>
          <td>
            Selects a key of a secret in the pod&#39;s namespace<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].env[index].valueFrom.configMapKeyRef {#edgeworkloadspecpodspecinitcontainersindexenvindexvaluefromconfigmapkeyref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexenvindexvaluefrom)</sup></sup>



Selects a key of a ConfigMap.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            The key to select.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>optional</b></td>
          <td>boolean</td>
          <td>
            Specify whether the ConfigMap or its key must be defined<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].env[index].valueFrom.fieldRef {#edgeworkloadspecpodspecinitcontainersindexenvindexvaluefromfieldref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexenvindexvaluefrom)</sup></sup>



Selects a field of the pod: supports metadata.name, metadata.namespace, `metadata.labels[&#39;&lt;KEY&gt;&#39;]`, `metadata.annotations[&#39;&lt;KEY&gt;&#39;]`, spec.nodeName, spec.serviceAccountName, status.hostIP, status.podIP, status.podIPs.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>fieldPath</b></td>
          <td>string</td>
          <td>
            Path of the field to select in the specified API version.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>apiVersion</b></td>
          <td>string</td>
          <td>
            Version of the schema the FieldPath is written in terms of, defaults to &#34;v1&#34;.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].env[index].valueFrom.resourceFieldRef {#edgeworkloadspecpodspecinitcontainersindexenvindexvaluefromresourcefieldref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexenvindexvaluefrom)</sup></sup>



Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, limits.ephemeral-storage, requests.cpu, requests.memory and requests.ephemeral-storage) are currently supported.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>resource</b></td>
          <td>string</td>
          <td>
            Required: resource to select<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>containerName</b></td>
          <td>string</td>
          <td>
            Container name: required for volumes, optional for env vars<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>divisor</b></td>
          <td>int or string</td>
          <td>
            Specifies the output format of the exposed resources, defaults to &#34;1&#34;<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].env[index].valueFrom.secretKeyRef {#edgeworkloadspecpodspecinitcontainersindexenvindexvaluefromsecretkeyref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexenvindexvaluefrom)</sup></sup>



Selects a key of a secret in the pod&#39;s namespace
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            The key of the secret to select from.  Must be a valid secret key.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>optional</b></td>
          <td>boolean</td>
          <td>
            Specify whether the Secret or its key must be defined<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].envFrom[index] {#edgeworkloadspecpodspecinitcontainersindexenvfromindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindex)</sup></sup>



EnvFromSource represents the source of a set of ConfigMaps
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexenvfromindexconfigmapref">configMapRef</a></b></td>
          <td>object</td>
          <td>
            The ConfigMap to select from<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>prefix</b></td>
          <td>string</td>
          <td>
            An optional identifier to prepend to each key in the ConfigMap. Must be a C_IDENTIFIER.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexenvfromindexsecretref">secretRef</a></b></td>
          <td>object</td>
          <td>
            The Secret to select from<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].envFrom[index].configMapRef {#edgeworkloadspecpodspecinitcontainersindexenvfromindexconfigmapref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexenvfromindex)</sup></sup>



The ConfigMap to select from
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>optional</b></td>
          <td>boolean</td>
          <td>
            Specify whether the ConfigMap must be defined<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].envFrom[index].secretRef {#edgeworkloadspecpodspecinitcontainersindexenvfromindexsecretref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexenvfromindex)</sup></sup>



The Secret to select from
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>optional</b></td>
          <td>boolean</td>
          <td>
            Specify whether the Secret must be defined<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].lifecycle {#edgeworkloadspecpodspecinitcontainersindexlifecycle}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindex)</sup></sup>



Actions that the management system should take in response to container lifecycle events. Cannot be updated.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexlifecyclepoststart">postStart</a></b></td>
          <td>object</td>
          <td>
            PostStart is called immediately after a container is created. If the handler fails, the container is terminated and restarted according to its restart policy. Other management of the container blocks until the hook completes. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexlifecycleprestop">preStop</a></b></td>
          <td>object</td>
          <td>
            PreStop is called immediately before a container is terminated due to an API request or management event such as liveness/startup probe failure, preemption, resource contention, etc. The handler is not called if the container crashes or exits. The Pod&#39;s termination grace period countdown begins before the PreStop hook is executed. Regardless of the outcome of the handler, the container will eventually terminate within the Pod&#39;s termination grace period (unless delayed by finalizers). Other management of the container blocks until the hook completes or until the termination grace period is reached. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].lifecycle.postStart {#edgeworkloadspecpodspecinitcontainersindexlifecyclepoststart}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexlifecycle)</sup></sup>



PostStart is called immediately after a container is created. If the handler fails, the container is terminated and restarted according to its restart policy. Other management of the container blocks until the hook completes. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexlifecyclepoststartexec">exec</a></b></td>
          <td>object</td>
          <td>
            Exec specifies the action to take.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexlifecyclepoststarthttpget">httpGet</a></b></td>
          <td>object</td>
          <td>
            HTTPGet specifies the http request to perform.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexlifecyclepoststarttcpsocket">tcpSocket</a></b></td>
          <td>object</td>
          <td>
            Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].lifecycle.postStart.exec {#edgeworkloadspecpodspecinitcontainersindexlifecyclepoststartexec}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexlifecyclepoststart)</sup></sup>



Exec specifies the action to take.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>command</b></td>
          <td>[]string</td>
          <td>
            Command is the command line to execute inside the container, the working directory for the command  is root (&#39;/&#39;) in the container&#39;s filesystem. The command is simply exec&#39;d, it is not run inside a shell, so traditional shell instructions (&#39;|&#39;, etc) won&#39;t work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].lifecycle.postStart.httpGet {#edgeworkloadspecpodspecinitcontainersindexlifecyclepoststarthttpget}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexlifecyclepoststart)</sup></sup>



HTTPGet specifies the http request to perform.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Host name to connect to, defaults to the pod IP. You probably want to set &#34;Host&#34; in httpHeaders instead.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexlifecyclepoststarthttpgethttpheadersindex">httpHeaders</a></b></td>
          <td>[]object</td>
          <td>
            Custom headers to set in the request. HTTP allows repeated headers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path to access on the HTTP server.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>scheme</b></td>
          <td>string</td>
          <td>
            Scheme to use for connecting to the host. Defaults to HTTP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].lifecycle.postStart.httpGet.httpHeaders[index] {#edgeworkloadspecpodspecinitcontainersindexlifecyclepoststarthttpgethttpheadersindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexlifecyclepoststarthttpget)</sup></sup>



HTTPHeader describes a custom header to be used in HTTP probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            The header field name<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            The header field value<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].lifecycle.postStart.tcpSocket {#edgeworkloadspecpodspecinitcontainersindexlifecyclepoststarttcpsocket}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexlifecyclepoststart)</sup></sup>



Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Optional: Host name to connect to, defaults to the pod IP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].lifecycle.preStop {#edgeworkloadspecpodspecinitcontainersindexlifecycleprestop}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexlifecycle)</sup></sup>



PreStop is called immediately before a container is terminated due to an API request or management event such as liveness/startup probe failure, preemption, resource contention, etc. The handler is not called if the container crashes or exits. The Pod&#39;s termination grace period countdown begins before the PreStop hook is executed. Regardless of the outcome of the handler, the container will eventually terminate within the Pod&#39;s termination grace period (unless delayed by finalizers). Other management of the container blocks until the hook completes or until the termination grace period is reached. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexlifecycleprestopexec">exec</a></b></td>
          <td>object</td>
          <td>
            Exec specifies the action to take.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexlifecycleprestophttpget">httpGet</a></b></td>
          <td>object</td>
          <td>
            HTTPGet specifies the http request to perform.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexlifecycleprestoptcpsocket">tcpSocket</a></b></td>
          <td>object</td>
          <td>
            Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].lifecycle.preStop.exec {#edgeworkloadspecpodspecinitcontainersindexlifecycleprestopexec}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexlifecycleprestop)</sup></sup>



Exec specifies the action to take.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>command</b></td>
          <td>[]string</td>
          <td>
            Command is the command line to execute inside the container, the working directory for the command  is root (&#39;/&#39;) in the container&#39;s filesystem. The command is simply exec&#39;d, it is not run inside a shell, so traditional shell instructions (&#39;|&#39;, etc) won&#39;t work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].lifecycle.preStop.httpGet {#edgeworkloadspecpodspecinitcontainersindexlifecycleprestophttpget}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexlifecycleprestop)</sup></sup>



HTTPGet specifies the http request to perform.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Host name to connect to, defaults to the pod IP. You probably want to set &#34;Host&#34; in httpHeaders instead.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexlifecycleprestophttpgethttpheadersindex">httpHeaders</a></b></td>
          <td>[]object</td>
          <td>
            Custom headers to set in the request. HTTP allows repeated headers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path to access on the HTTP server.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>scheme</b></td>
          <td>string</td>
          <td>
            Scheme to use for connecting to the host. Defaults to HTTP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].lifecycle.preStop.httpGet.httpHeaders[index] {#edgeworkloadspecpodspecinitcontainersindexlifecycleprestophttpgethttpheadersindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexlifecycleprestophttpget)</sup></sup>



HTTPHeader describes a custom header to be used in HTTP probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            The header field name<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            The header field value<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].lifecycle.preStop.tcpSocket {#edgeworkloadspecpodspecinitcontainersindexlifecycleprestoptcpsocket}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexlifecycleprestop)</sup></sup>



Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Optional: Host name to connect to, defaults to the pod IP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].livenessProbe {#edgeworkloadspecpodspecinitcontainersindexlivenessprobe}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindex)</sup></sup>



Periodic probe of container liveness. Container will be restarted if the probe fails. Cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexlivenessprobeexec">exec</a></b></td>
          <td>object</td>
          <td>
            Exec specifies the action to take.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>failureThreshold</b></td>
          <td>integer</td>
          <td>
            Minimum consecutive failures for the probe to be considered failed after having succeeded. Defaults to 3. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexlivenessprobegrpc">grpc</a></b></td>
          <td>object</td>
          <td>
            GRPC specifies an action involving a GRPC port. This is an alpha field and requires enabling GRPCContainerProbe feature gate.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexlivenessprobehttpget">httpGet</a></b></td>
          <td>object</td>
          <td>
            HTTPGet specifies the http request to perform.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>initialDelaySeconds</b></td>
          <td>integer</td>
          <td>
            Number of seconds after the container has started before liveness probes are initiated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>periodSeconds</b></td>
          <td>integer</td>
          <td>
            How often (in seconds) to perform the probe. Default to 10 seconds. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>successThreshold</b></td>
          <td>integer</td>
          <td>
            Minimum consecutive successes for the probe to be considered successful after having failed. Defaults to 1. Must be 1 for liveness and startup. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexlivenessprobetcpsocket">tcpSocket</a></b></td>
          <td>object</td>
          <td>
            TCPSocket specifies an action involving a TCP port.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>terminationGracePeriodSeconds</b></td>
          <td>integer</td>
          <td>
            Optional duration in seconds the pod needs to terminate gracefully upon probe failure. The grace period is the duration in seconds after the processes running in the pod are sent a termination signal and the time when the processes are forcibly halted with a kill signal. Set this value longer than the expected cleanup time for your process. If this value is nil, the pod&#39;s terminationGracePeriodSeconds will be used. Otherwise, this value overrides the value provided by the pod spec. Value must be non-negative integer. The value zero indicates stop immediately via the kill signal (no opportunity to shut down). This is a beta field and requires enabling ProbeTerminationGracePeriod feature gate. Minimum value is 1. spec.terminationGracePeriodSeconds is used if unset.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>timeoutSeconds</b></td>
          <td>integer</td>
          <td>
            Number of seconds after which the probe times out. Defaults to 1 second. Minimum value is 1. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].livenessProbe.exec {#edgeworkloadspecpodspecinitcontainersindexlivenessprobeexec}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexlivenessprobe)</sup></sup>



Exec specifies the action to take.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>command</b></td>
          <td>[]string</td>
          <td>
            Command is the command line to execute inside the container, the working directory for the command  is root (&#39;/&#39;) in the container&#39;s filesystem. The command is simply exec&#39;d, it is not run inside a shell, so traditional shell instructions (&#39;|&#39;, etc) won&#39;t work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].livenessProbe.grpc {#edgeworkloadspecpodspecinitcontainersindexlivenessprobegrpc}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexlivenessprobe)</sup></sup>



GRPC specifies an action involving a GRPC port. This is an alpha field and requires enabling GRPCContainerProbe feature gate.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>integer</td>
          <td>
            Port number of the gRPC service. Number must be in the range 1 to 65535.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>service</b></td>
          <td>string</td>
          <td>
            Service is the name of the service to place in the gRPC HealthCheckRequest (see https://github.com/grpc/grpc/blob/master/doc/health-checking.md). 
 If this is not specified, the default behavior is defined by gRPC.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].livenessProbe.httpGet {#edgeworkloadspecpodspecinitcontainersindexlivenessprobehttpget}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexlivenessprobe)</sup></sup>



HTTPGet specifies the http request to perform.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Host name to connect to, defaults to the pod IP. You probably want to set &#34;Host&#34; in httpHeaders instead.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexlivenessprobehttpgethttpheadersindex">httpHeaders</a></b></td>
          <td>[]object</td>
          <td>
            Custom headers to set in the request. HTTP allows repeated headers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path to access on the HTTP server.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>scheme</b></td>
          <td>string</td>
          <td>
            Scheme to use for connecting to the host. Defaults to HTTP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].livenessProbe.httpGet.httpHeaders[index] {#edgeworkloadspecpodspecinitcontainersindexlivenessprobehttpgethttpheadersindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexlivenessprobehttpget)</sup></sup>



HTTPHeader describes a custom header to be used in HTTP probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            The header field name<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            The header field value<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].livenessProbe.tcpSocket {#edgeworkloadspecpodspecinitcontainersindexlivenessprobetcpsocket}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexlivenessprobe)</sup></sup>



TCPSocket specifies an action involving a TCP port.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Optional: Host name to connect to, defaults to the pod IP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].ports[index] {#edgeworkloadspecpodspecinitcontainersindexportsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindex)</sup></sup>



ContainerPort represents a network port in a single container.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>containerPort</b></td>
          <td>integer</td>
          <td>
            Number of port to expose on the pod&#39;s IP address. This must be a valid port number, 0 &lt; x &lt; 65536.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>hostIP</b></td>
          <td>string</td>
          <td>
            What host IP to bind the external port to.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>hostPort</b></td>
          <td>integer</td>
          <td>
            Number of port to expose on the host. If specified, this must be a valid port number, 0 &lt; x &lt; 65536. If HostNetwork is specified, this must match ContainerPort. Most containers do not need this.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            If specified, this must be an IANA_SVC_NAME and unique within the pod. Each named port in a pod must have a unique name. Name for the port that can be referred to by services.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>protocol</b></td>
          <td>string</td>
          <td>
            Protocol for port. Must be UDP, TCP, or SCTP. Defaults to &#34;TCP&#34;.<br/>
            <br/>
              <i>Default</i>: TCP<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].readinessProbe {#edgeworkloadspecpodspecinitcontainersindexreadinessprobe}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindex)</sup></sup>



Periodic probe of container service readiness. Container will be removed from service endpoints if the probe fails. Cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexreadinessprobeexec">exec</a></b></td>
          <td>object</td>
          <td>
            Exec specifies the action to take.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>failureThreshold</b></td>
          <td>integer</td>
          <td>
            Minimum consecutive failures for the probe to be considered failed after having succeeded. Defaults to 3. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexreadinessprobegrpc">grpc</a></b></td>
          <td>object</td>
          <td>
            GRPC specifies an action involving a GRPC port. This is an alpha field and requires enabling GRPCContainerProbe feature gate.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexreadinessprobehttpget">httpGet</a></b></td>
          <td>object</td>
          <td>
            HTTPGet specifies the http request to perform.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>initialDelaySeconds</b></td>
          <td>integer</td>
          <td>
            Number of seconds after the container has started before liveness probes are initiated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>periodSeconds</b></td>
          <td>integer</td>
          <td>
            How often (in seconds) to perform the probe. Default to 10 seconds. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>successThreshold</b></td>
          <td>integer</td>
          <td>
            Minimum consecutive successes for the probe to be considered successful after having failed. Defaults to 1. Must be 1 for liveness and startup. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexreadinessprobetcpsocket">tcpSocket</a></b></td>
          <td>object</td>
          <td>
            TCPSocket specifies an action involving a TCP port.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>terminationGracePeriodSeconds</b></td>
          <td>integer</td>
          <td>
            Optional duration in seconds the pod needs to terminate gracefully upon probe failure. The grace period is the duration in seconds after the processes running in the pod are sent a termination signal and the time when the processes are forcibly halted with a kill signal. Set this value longer than the expected cleanup time for your process. If this value is nil, the pod&#39;s terminationGracePeriodSeconds will be used. Otherwise, this value overrides the value provided by the pod spec. Value must be non-negative integer. The value zero indicates stop immediately via the kill signal (no opportunity to shut down). This is a beta field and requires enabling ProbeTerminationGracePeriod feature gate. Minimum value is 1. spec.terminationGracePeriodSeconds is used if unset.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>timeoutSeconds</b></td>
          <td>integer</td>
          <td>
            Number of seconds after which the probe times out. Defaults to 1 second. Minimum value is 1. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].readinessProbe.exec {#edgeworkloadspecpodspecinitcontainersindexreadinessprobeexec}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexreadinessprobe)</sup></sup>



Exec specifies the action to take.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>command</b></td>
          <td>[]string</td>
          <td>
            Command is the command line to execute inside the container, the working directory for the command  is root (&#39;/&#39;) in the container&#39;s filesystem. The command is simply exec&#39;d, it is not run inside a shell, so traditional shell instructions (&#39;|&#39;, etc) won&#39;t work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].readinessProbe.grpc {#edgeworkloadspecpodspecinitcontainersindexreadinessprobegrpc}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexreadinessprobe)</sup></sup>



GRPC specifies an action involving a GRPC port. This is an alpha field and requires enabling GRPCContainerProbe feature gate.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>integer</td>
          <td>
            Port number of the gRPC service. Number must be in the range 1 to 65535.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>service</b></td>
          <td>string</td>
          <td>
            Service is the name of the service to place in the gRPC HealthCheckRequest (see https://github.com/grpc/grpc/blob/master/doc/health-checking.md). 
 If this is not specified, the default behavior is defined by gRPC.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].readinessProbe.httpGet {#edgeworkloadspecpodspecinitcontainersindexreadinessprobehttpget}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexreadinessprobe)</sup></sup>



HTTPGet specifies the http request to perform.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Host name to connect to, defaults to the pod IP. You probably want to set &#34;Host&#34; in httpHeaders instead.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexreadinessprobehttpgethttpheadersindex">httpHeaders</a></b></td>
          <td>[]object</td>
          <td>
            Custom headers to set in the request. HTTP allows repeated headers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path to access on the HTTP server.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>scheme</b></td>
          <td>string</td>
          <td>
            Scheme to use for connecting to the host. Defaults to HTTP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].readinessProbe.httpGet.httpHeaders[index] {#edgeworkloadspecpodspecinitcontainersindexreadinessprobehttpgethttpheadersindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexreadinessprobehttpget)</sup></sup>



HTTPHeader describes a custom header to be used in HTTP probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            The header field name<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            The header field value<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].readinessProbe.tcpSocket {#edgeworkloadspecpodspecinitcontainersindexreadinessprobetcpsocket}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexreadinessprobe)</sup></sup>



TCPSocket specifies an action involving a TCP port.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Optional: Host name to connect to, defaults to the pod IP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].resources {#edgeworkloadspecpodspecinitcontainersindexresources}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindex)</sup></sup>



Compute Resources required by this container. Cannot be updated. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>limits</b></td>
          <td>map[string]int or string</td>
          <td>
            Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>requests</b></td>
          <td>map[string]int or string</td>
          <td>
            Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].securityContext {#edgeworkloadspecpodspecinitcontainersindexsecuritycontext}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindex)</sup></sup>



SecurityContext defines the security options the container should be run with. If set, the fields of SecurityContext override the equivalent fields of PodSecurityContext. More info: https://kubernetes.io/docs/tasks/configure-pod-container/security-context/
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>allowPrivilegeEscalation</b></td>
          <td>boolean</td>
          <td>
            AllowPrivilegeEscalation controls whether a process can gain more privileges than its parent process. This bool directly controls if the no_new_privs flag will be set on the container process. AllowPrivilegeEscalation is true always when the container is: 1) run as Privileged 2) has CAP_SYS_ADMIN Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexsecuritycontextcapabilities">capabilities</a></b></td>
          <td>object</td>
          <td>
            The capabilities to add/drop when running containers. Defaults to the default set of capabilities granted by the container runtime. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>privileged</b></td>
          <td>boolean</td>
          <td>
            Run container in privileged mode. Processes in privileged containers are essentially equivalent to root on the host. Defaults to false. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>procMount</b></td>
          <td>string</td>
          <td>
            procMount denotes the type of proc mount to use for the containers. The default is DefaultProcMount which uses the container runtime defaults for readonly paths and masked paths. This requires the ProcMountType feature flag to be enabled. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnlyRootFilesystem</b></td>
          <td>boolean</td>
          <td>
            Whether this container has a read-only root filesystem. Default is false. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>runAsGroup</b></td>
          <td>integer</td>
          <td>
            The GID to run the entrypoint of the container process. Uses runtime default if unset. May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>runAsNonRoot</b></td>
          <td>boolean</td>
          <td>
            Indicates that the container must run as a non-root user. If true, the Kubelet will validate the image at runtime to ensure that it does not run as UID 0 (root) and fail to start the container if it does. If unset or false, no such validation will be performed. May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>runAsUser</b></td>
          <td>integer</td>
          <td>
            The UID to run the entrypoint of the container process. Defaults to user specified in image metadata if unspecified. May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexsecuritycontextselinuxoptions">seLinuxOptions</a></b></td>
          <td>object</td>
          <td>
            The SELinux context to be applied to the container. If unspecified, the container runtime will allocate a random SELinux context for each container.  May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexsecuritycontextseccompprofile">seccompProfile</a></b></td>
          <td>object</td>
          <td>
            The seccomp options to use by this container. If seccomp options are provided at both the pod &amp; container level, the container options override the pod options. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexsecuritycontextwindowsoptions">windowsOptions</a></b></td>
          <td>object</td>
          <td>
            The Windows specific settings applied to all containers. If unspecified, the options from the PodSecurityContext will be used. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is linux.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].securityContext.capabilities {#edgeworkloadspecpodspecinitcontainersindexsecuritycontextcapabilities}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexsecuritycontext)</sup></sup>



The capabilities to add/drop when running containers. Defaults to the default set of capabilities granted by the container runtime. Note that this field cannot be set when spec.os.name is windows.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>add</b></td>
          <td>[]string</td>
          <td>
            Added capabilities<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>drop</b></td>
          <td>[]string</td>
          <td>
            Removed capabilities<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].securityContext.seLinuxOptions {#edgeworkloadspecpodspecinitcontainersindexsecuritycontextselinuxoptions}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexsecuritycontext)</sup></sup>



The SELinux context to be applied to the container. If unspecified, the container runtime will allocate a random SELinux context for each container.  May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>level</b></td>
          <td>string</td>
          <td>
            Level is SELinux level label that applies to the container.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>role</b></td>
          <td>string</td>
          <td>
            Role is a SELinux role label that applies to the container.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>type</b></td>
          <td>string</td>
          <td>
            Type is a SELinux type label that applies to the container.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>user</b></td>
          <td>string</td>
          <td>
            User is a SELinux user label that applies to the container.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].securityContext.seccompProfile {#edgeworkloadspecpodspecinitcontainersindexsecuritycontextseccompprofile}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexsecuritycontext)</sup></sup>



The seccomp options to use by this container. If seccomp options are provided at both the pod &amp; container level, the container options override the pod options. Note that this field cannot be set when spec.os.name is windows.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>type</b></td>
          <td>string</td>
          <td>
            type indicates which kind of seccomp profile will be applied. Valid options are: 
 Localhost - a profile defined in a file on the node should be used. RuntimeDefault - the container runtime default profile should be used. Unconfined - no profile should be applied.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>localhostProfile</b></td>
          <td>string</td>
          <td>
            localhostProfile indicates a profile defined in a file on the node should be used. The profile must be preconfigured on the node to work. Must be a descending path, relative to the kubelet&#39;s configured seccomp profile location. Must only be set if type is &#34;Localhost&#34;.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].securityContext.windowsOptions {#edgeworkloadspecpodspecinitcontainersindexsecuritycontextwindowsoptions}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexsecuritycontext)</sup></sup>



The Windows specific settings applied to all containers. If unspecified, the options from the PodSecurityContext will be used. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is linux.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>gmsaCredentialSpec</b></td>
          <td>string</td>
          <td>
            GMSACredentialSpec is where the GMSA admission webhook (https://github.com/kubernetes-sigs/windows-gmsa) inlines the contents of the GMSA credential spec named by the GMSACredentialSpecName field.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>gmsaCredentialSpecName</b></td>
          <td>string</td>
          <td>
            GMSACredentialSpecName is the name of the GMSA credential spec to use.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>hostProcess</b></td>
          <td>boolean</td>
          <td>
            HostProcess determines if a container should be run as a &#39;Host Process&#39; container. This field is alpha-level and will only be honored by components that enable the WindowsHostProcessContainers feature flag. Setting this field without the feature flag will result in errors when validating the Pod. All of a Pod&#39;s containers must have the same effective HostProcess value (it is not allowed to have a mix of HostProcess containers and non-HostProcess containers).  In addition, if HostProcess is true then HostNetwork must also be set to true.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>runAsUserName</b></td>
          <td>string</td>
          <td>
            The UserName in Windows to run the entrypoint of the container process. Defaults to the user specified in image metadata if unspecified. May also be set in PodSecurityContext. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].startupProbe {#edgeworkloadspecpodspecinitcontainersindexstartupprobe}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindex)</sup></sup>



StartupProbe indicates that the Pod has successfully initialized. If specified, no other probes are executed until this completes successfully. If this probe fails, the Pod will be restarted, just as if the livenessProbe failed. This can be used to provide different probe parameters at the beginning of a Pod&#39;s lifecycle, when it might take a long time to load data or warm a cache, than during steady-state operation. This cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexstartupprobeexec">exec</a></b></td>
          <td>object</td>
          <td>
            Exec specifies the action to take.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>failureThreshold</b></td>
          <td>integer</td>
          <td>
            Minimum consecutive failures for the probe to be considered failed after having succeeded. Defaults to 3. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexstartupprobegrpc">grpc</a></b></td>
          <td>object</td>
          <td>
            GRPC specifies an action involving a GRPC port. This is an alpha field and requires enabling GRPCContainerProbe feature gate.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexstartupprobehttpget">httpGet</a></b></td>
          <td>object</td>
          <td>
            HTTPGet specifies the http request to perform.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>initialDelaySeconds</b></td>
          <td>integer</td>
          <td>
            Number of seconds after the container has started before liveness probes are initiated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>periodSeconds</b></td>
          <td>integer</td>
          <td>
            How often (in seconds) to perform the probe. Default to 10 seconds. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>successThreshold</b></td>
          <td>integer</td>
          <td>
            Minimum consecutive successes for the probe to be considered successful after having failed. Defaults to 1. Must be 1 for liveness and startup. Minimum value is 1.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexstartupprobetcpsocket">tcpSocket</a></b></td>
          <td>object</td>
          <td>
            TCPSocket specifies an action involving a TCP port.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>terminationGracePeriodSeconds</b></td>
          <td>integer</td>
          <td>
            Optional duration in seconds the pod needs to terminate gracefully upon probe failure. The grace period is the duration in seconds after the processes running in the pod are sent a termination signal and the time when the processes are forcibly halted with a kill signal. Set this value longer than the expected cleanup time for your process. If this value is nil, the pod&#39;s terminationGracePeriodSeconds will be used. Otherwise, this value overrides the value provided by the pod spec. Value must be non-negative integer. The value zero indicates stop immediately via the kill signal (no opportunity to shut down). This is a beta field and requires enabling ProbeTerminationGracePeriod feature gate. Minimum value is 1. spec.terminationGracePeriodSeconds is used if unset.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>timeoutSeconds</b></td>
          <td>integer</td>
          <td>
            Number of seconds after which the probe times out. Defaults to 1 second. Minimum value is 1. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].startupProbe.exec {#edgeworkloadspecpodspecinitcontainersindexstartupprobeexec}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexstartupprobe)</sup></sup>



Exec specifies the action to take.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>command</b></td>
          <td>[]string</td>
          <td>
            Command is the command line to execute inside the container, the working directory for the command  is root (&#39;/&#39;) in the container&#39;s filesystem. The command is simply exec&#39;d, it is not run inside a shell, so traditional shell instructions (&#39;|&#39;, etc) won&#39;t work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].startupProbe.grpc {#edgeworkloadspecpodspecinitcontainersindexstartupprobegrpc}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexstartupprobe)</sup></sup>



GRPC specifies an action involving a GRPC port. This is an alpha field and requires enabling GRPCContainerProbe feature gate.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>integer</td>
          <td>
            Port number of the gRPC service. Number must be in the range 1 to 65535.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>service</b></td>
          <td>string</td>
          <td>
            Service is the name of the service to place in the gRPC HealthCheckRequest (see https://github.com/grpc/grpc/blob/master/doc/health-checking.md). 
 If this is not specified, the default behavior is defined by gRPC.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].startupProbe.httpGet {#edgeworkloadspecpodspecinitcontainersindexstartupprobehttpget}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexstartupprobe)</sup></sup>



HTTPGet specifies the http request to perform.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Host name to connect to, defaults to the pod IP. You probably want to set &#34;Host&#34; in httpHeaders instead.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecinitcontainersindexstartupprobehttpgethttpheadersindex">httpHeaders</a></b></td>
          <td>[]object</td>
          <td>
            Custom headers to set in the request. HTTP allows repeated headers.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path to access on the HTTP server.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>scheme</b></td>
          <td>string</td>
          <td>
            Scheme to use for connecting to the host. Defaults to HTTP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].startupProbe.httpGet.httpHeaders[index] {#edgeworkloadspecpodspecinitcontainersindexstartupprobehttpgethttpheadersindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexstartupprobehttpget)</sup></sup>



HTTPHeader describes a custom header to be used in HTTP probes
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            The header field name<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            The header field value<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].startupProbe.tcpSocket {#edgeworkloadspecpodspecinitcontainersindexstartupprobetcpsocket}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindexstartupprobe)</sup></sup>



TCPSocket specifies an action involving a TCP port.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>port</b></td>
          <td>int or string</td>
          <td>
            Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>host</b></td>
          <td>string</td>
          <td>
            Optional: Host name to connect to, defaults to the pod IP.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].volumeDevices[index] {#edgeworkloadspecpodspecinitcontainersindexvolumedevicesindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindex)</sup></sup>



volumeDevice describes a mapping of a raw block device within a container.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>devicePath</b></td>
          <td>string</td>
          <td>
            devicePath is the path inside of the container that the device will be mapped to.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            name must match the name of a persistentVolumeClaim in the pod<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.initContainers[index].volumeMounts[index] {#edgeworkloadspecpodspecinitcontainersindexvolumemountsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecinitcontainersindex)</sup></sup>



VolumeMount describes a mounting of a Volume within a container.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>mountPath</b></td>
          <td>string</td>
          <td>
            Path within the container at which the volume should be mounted.  Must not contain &#39;:&#39;.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            This must match the Name of a Volume.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>mountPropagation</b></td>
          <td>string</td>
          <td>
            mountPropagation determines how mounts are propagated from the host to container and the other way around. When not set, MountPropagationNone is used. This field is beta in 1.10.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            Mounted read-only if true, read-write otherwise (false or unspecified). Defaults to false.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>subPath</b></td>
          <td>string</td>
          <td>
            Path within the volume from which the container&#39;s volume should be mounted. Defaults to &#34;&#34; (volume&#39;s root).<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>subPathExpr</b></td>
          <td>string</td>
          <td>
            Expanded path within the volume from which the container&#39;s volume should be mounted. Behaves similarly to SubPath but environment variable references $(VAR_NAME) are expanded using the container&#39;s environment. Defaults to &#34;&#34; (volume&#39;s root). SubPathExpr and SubPath are mutually exclusive.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.os {#edgeworkloadspecpodspecos}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspec)</sup></sup>



Specifies the OS of the containers in the pod. Some pod and container fields are restricted if this is set. 
 If the OS field is set to linux, the following fields must be unset: -securityContext.windowsOptions 
 If the OS field is set to windows, following fields must be unset: - spec.hostPID - spec.hostIPC - spec.securityContext.seLinuxOptions - spec.securityContext.seccompProfile - spec.securityContext.fsGroup - spec.securityContext.fsGroupChangePolicy - spec.securityContext.sysctls - spec.shareProcessNamespace - spec.securityContext.runAsUser - spec.securityContext.runAsGroup - spec.securityContext.supplementalGroups - spec.containers[*].securityContext.seLinuxOptions - spec.containers[*].securityContext.seccompProfile - spec.containers[*].securityContext.capabilities - spec.containers[*].securityContext.readOnlyRootFilesystem - spec.containers[*].securityContext.privileged - spec.containers[*].securityContext.allowPrivilegeEscalation - spec.containers[*].securityContext.procMount - spec.containers[*].securityContext.runAsUser - spec.containers[*].securityContext.runAsGroup This is an alpha field and requires the IdentifyPodOS feature
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name is the name of the operating system. The currently supported values are linux and windows. Additional value may be defined in future and can be one of: https://github.com/opencontainers/runtime-spec/blob/master/config.md#platform-specific-configuration Clients should expect to handle additional values and treat unrecognized values in this field as os: null<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.readinessGates[index] {#edgeworkloadspecpodspecreadinessgatesindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspec)</sup></sup>



PodReadinessGate contains the reference to a pod condition
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>conditionType</b></td>
          <td>string</td>
          <td>
            ConditionType refers to a condition in the pod&#39;s condition list with matching type.<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.securityContext {#edgeworkloadspecpodspecsecuritycontext}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspec)</sup></sup>



SecurityContext holds pod-level security attributes and common container settings. Optional: Defaults to empty.  See type description for default values of each field.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>fsGroup</b></td>
          <td>integer</td>
          <td>
            A special supplemental group that applies to all containers in a pod. Some volume types allow the Kubelet to change the ownership of that volume to be owned by the pod: 
 1. The owning GID will be the FSGroup 2. The setgid bit is set (new files created in the volume will be owned by FSGroup) 3. The permission bits are OR&#39;d with rw-rw---- 
 If unset, the Kubelet will not modify the ownership and permissions of any volume. Note that this field cannot be set when spec.os.name is windows.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>fsGroupChangePolicy</b></td>
          <td>string</td>
          <td>
            fsGroupChangePolicy defines behavior of changing ownership and permission of the volume before being exposed inside Pod. This field will only apply to volume types which support fsGroup based ownership(and permissions). It will have no effect on ephemeral volume types such as: secret, configmaps and emptydir. Valid values are &#34;OnRootMismatch&#34; and &#34;Always&#34;. If not specified, &#34;Always&#34; is used. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>runAsGroup</b></td>
          <td>integer</td>
          <td>
            The GID to run the entrypoint of the container process. Uses runtime default if unset. May also be set in SecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence for that container. Note that this field cannot be set when spec.os.name is windows.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>runAsNonRoot</b></td>
          <td>boolean</td>
          <td>
            Indicates that the container must run as a non-root user. If true, the Kubelet will validate the image at runtime to ensure that it does not run as UID 0 (root) and fail to start the container if it does. If unset or false, no such validation will be performed. May also be set in SecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>runAsUser</b></td>
          <td>integer</td>
          <td>
            The UID to run the entrypoint of the container process. Defaults to user specified in image metadata if unspecified. May also be set in SecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence for that container. Note that this field cannot be set when spec.os.name is windows.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecsecuritycontextselinuxoptions">seLinuxOptions</a></b></td>
          <td>object</td>
          <td>
            The SELinux context to be applied to all containers. If unspecified, the container runtime will allocate a random SELinux context for each container.  May also be set in SecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence for that container. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecsecuritycontextseccompprofile">seccompProfile</a></b></td>
          <td>object</td>
          <td>
            The seccomp options to use by the containers in this pod. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>supplementalGroups</b></td>
          <td>[]integer</td>
          <td>
            A list of groups applied to the first process run in each container, in addition to the container&#39;s primary GID.  If unspecified, no groups will be added to any container. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecsecuritycontextsysctlsindex">sysctls</a></b></td>
          <td>[]object</td>
          <td>
            Sysctls hold a list of namespaced sysctls used for the pod. Pods with unsupported sysctls (by the container runtime) might fail to launch. Note that this field cannot be set when spec.os.name is windows.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecsecuritycontextwindowsoptions">windowsOptions</a></b></td>
          <td>object</td>
          <td>
            The Windows specific settings applied to all containers. If unspecified, the options within a container&#39;s SecurityContext will be used. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is linux.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.securityContext.seLinuxOptions {#edgeworkloadspecpodspecsecuritycontextselinuxoptions}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecsecuritycontext)</sup></sup>



The SELinux context to be applied to all containers. If unspecified, the container runtime will allocate a random SELinux context for each container.  May also be set in SecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence for that container. Note that this field cannot be set when spec.os.name is windows.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>level</b></td>
          <td>string</td>
          <td>
            Level is SELinux level label that applies to the container.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>role</b></td>
          <td>string</td>
          <td>
            Role is a SELinux role label that applies to the container.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>type</b></td>
          <td>string</td>
          <td>
            Type is a SELinux type label that applies to the container.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>user</b></td>
          <td>string</td>
          <td>
            User is a SELinux user label that applies to the container.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.securityContext.seccompProfile {#edgeworkloadspecpodspecsecuritycontextseccompprofile}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecsecuritycontext)</sup></sup>



The seccomp options to use by the containers in this pod. Note that this field cannot be set when spec.os.name is windows.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>type</b></td>
          <td>string</td>
          <td>
            type indicates which kind of seccomp profile will be applied. Valid options are: 
 Localhost - a profile defined in a file on the node should be used. RuntimeDefault - the container runtime default profile should be used. Unconfined - no profile should be applied.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>localhostProfile</b></td>
          <td>string</td>
          <td>
            localhostProfile indicates a profile defined in a file on the node should be used. The profile must be preconfigured on the node to work. Must be a descending path, relative to the kubelet&#39;s configured seccomp profile location. Must only be set if type is &#34;Localhost&#34;.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.securityContext.sysctls[index] {#edgeworkloadspecpodspecsecuritycontextsysctlsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecsecuritycontext)</sup></sup>



Sysctl defines a kernel parameter to be set
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of a property to set<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            Value of a property to set<br/>
          </td>
          <td>true</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.securityContext.windowsOptions {#edgeworkloadspecpodspecsecuritycontextwindowsoptions}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecsecuritycontext)</sup></sup>



The Windows specific settings applied to all containers. If unspecified, the options within a container&#39;s SecurityContext will be used. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is linux.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>gmsaCredentialSpec</b></td>
          <td>string</td>
          <td>
            GMSACredentialSpec is where the GMSA admission webhook (https://github.com/kubernetes-sigs/windows-gmsa) inlines the contents of the GMSA credential spec named by the GMSACredentialSpecName field.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>gmsaCredentialSpecName</b></td>
          <td>string</td>
          <td>
            GMSACredentialSpecName is the name of the GMSA credential spec to use.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>hostProcess</b></td>
          <td>boolean</td>
          <td>
            HostProcess determines if a container should be run as a &#39;Host Process&#39; container. This field is alpha-level and will only be honored by components that enable the WindowsHostProcessContainers feature flag. Setting this field without the feature flag will result in errors when validating the Pod. All of a Pod&#39;s containers must have the same effective HostProcess value (it is not allowed to have a mix of HostProcess containers and non-HostProcess containers).  In addition, if HostProcess is true then HostNetwork must also be set to true.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>runAsUserName</b></td>
          <td>string</td>
          <td>
            The UserName in Windows to run the entrypoint of the container process. Defaults to the user specified in image metadata if unspecified. May also be set in PodSecurityContext. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.tolerations[index] {#edgeworkloadspecpodspectolerationsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspec)</sup></sup>



The pod this Toleration is attached to tolerates any taint that matches the triple &lt;key,value,effect&gt; using the matching operator &lt;operator&gt;.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>effect</b></td>
          <td>string</td>
          <td>
            Effect indicates the taint effect to match. Empty means match all taint effects. When specified, allowed values are NoSchedule, PreferNoSchedule and NoExecute.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            Key is the taint key that the toleration applies to. Empty means match all taint keys. If the key is empty, operator must be Exists; this combination means to match all values and all keys.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>operator</b></td>
          <td>string</td>
          <td>
            Operator represents a key&#39;s relationship to the value. Valid operators are Exists and Equal. Defaults to Equal. Exists is equivalent to wildcard for value, so that a pod can tolerate all taints of a particular category.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>tolerationSeconds</b></td>
          <td>integer</td>
          <td>
            TolerationSeconds represents the period of time the toleration (which must be of effect NoExecute, otherwise this field is ignored) tolerates the taint. By default, it is not set, which means tolerate the taint forever (do not evict). Zero and negative values will be treated as 0 (evict immediately) by the system.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>value</b></td>
          <td>string</td>
          <td>
            Value is the taint value the toleration matches to. If the operator is Exists, the value should be empty, otherwise just a regular string.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.topologySpreadConstraints[index] {#edgeworkloadspecpodspectopologyspreadconstraintsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspec)</sup></sup>



TopologySpreadConstraint specifies how to spread matching pods among the given topology.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>maxSkew</b></td>
          <td>integer</td>
          <td>
            MaxSkew describes the degree to which pods may be unevenly distributed. When `whenUnsatisfiable=DoNotSchedule`, it is the maximum permitted difference between the number of matching pods in the target topology and the global minimum. For example, in a 3-zone cluster, MaxSkew is set to 1, and pods with the same labelSelector spread as 1/1/0: | zone1 | zone2 | zone3 | |   P   |   P   |       | - if MaxSkew is 1, incoming pod can only be scheduled to zone3 to become 1/1/1; scheduling it onto zone1(zone2) would make the ActualSkew(2-0) on zone1(zone2) violate MaxSkew(1). - if MaxSkew is 2, incoming pod can be scheduled onto any zone. When `whenUnsatisfiable=ScheduleAnyway`, it is used to give higher precedence to topologies that satisfy it. It&#39;s a required field. Default value is 1 and 0 is not allowed.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>topologyKey</b></td>
          <td>string</td>
          <td>
            TopologyKey is the key of node labels. Nodes that have a label with this key and identical values are considered to be in the same topology. We consider each &lt;key, value&gt; as a &#34;bucket&#34;, and try to put balanced number of pods into each bucket. It&#39;s a required field.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>whenUnsatisfiable</b></td>
          <td>string</td>
          <td>
            WhenUnsatisfiable indicates how to deal with a pod if it doesn&#39;t satisfy the spread constraint. - DoNotSchedule (default) tells the scheduler not to schedule it. - ScheduleAnyway tells the scheduler to schedule the pod in any location,   but giving higher precedence to topologies that would help reduce the   skew. A constraint is considered &#34;Unsatisfiable&#34; for an incoming pod if and only if every possible node assignment for that pod would violate &#34;MaxSkew&#34; on some topology. For example, in a 3-zone cluster, MaxSkew is set to 1, and pods with the same labelSelector spread as 3/1/1: | zone1 | zone2 | zone3 | | P P P |   P   |   P   | If WhenUnsatisfiable is set to DoNotSchedule, incoming pod can only be scheduled to zone2(zone3) to become 3/2/1(3/1/2) as ActualSkew(2-1) on zone2(zone3) satisfies MaxSkew(1). In other words, the cluster can still be imbalanced, but scheduler won&#39;t make it *more* imbalanced. It&#39;s a required field.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspectopologyspreadconstraintsindexlabelselector">labelSelector</a></b></td>
          <td>object</td>
          <td>
            LabelSelector is used to find matching pods. Pods that match this label selector are counted to determine the number of pods in their corresponding topology domain.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.topologySpreadConstraints[index].labelSelector {#edgeworkloadspecpodspectopologyspreadconstraintsindexlabelselector}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspectopologyspreadconstraintsindex)</sup></sup>



LabelSelector is used to find matching pods. Pods that match this label selector are counted to determine the number of pods in their corresponding topology domain.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspectopologyspreadconstraintsindexlabelselectormatchexpressionsindex">matchExpressions</a></b></td>
          <td>[]object</td>
          <td>
            matchExpressions is a list of label selector requirements. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>matchLabels</b></td>
          <td>map[string]string</td>
          <td>
            matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is &#34;key&#34;, the operator is &#34;In&#34;, and the values array contains only &#34;value&#34;. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.topologySpreadConstraints[index].labelSelector.matchExpressions[index] {#edgeworkloadspecpodspectopologyspreadconstraintsindexlabelselectormatchexpressionsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspectopologyspreadconstraintsindexlabelselector)</sup></sup>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            key is the label key that the selector applies to.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>operator</b></td>
          <td>string</td>
          <td>
            operator represents a key&#39;s relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>values</b></td>
          <td>[]string</td>
          <td>
            values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index] {#edgeworkloadspecpodspecvolumesindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspec)</sup></sup>



Volume represents a named volume in a pod that may be accessed by any container in the pod.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Volume&#39;s name. Must be a DNS_LABEL and unique within the pod. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexawselasticblockstore">awsElasticBlockStore</a></b></td>
          <td>object</td>
          <td>
            AWSElasticBlockStore represents an AWS Disk resource that is attached to a kubelet&#39;s host machine and then exposed to the pod. More info: https://kubernetes.io/docs/concepts/storage/volumes#awselasticblockstore<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexazuredisk">azureDisk</a></b></td>
          <td>object</td>
          <td>
            AzureDisk represents an Azure Data Disk mount on the host and bind mount to the pod.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexazurefile">azureFile</a></b></td>
          <td>object</td>
          <td>
            AzureFile represents an Azure File Service mount on the host and bind mount to the pod.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexcephfs">cephfs</a></b></td>
          <td>object</td>
          <td>
            CephFS represents a Ceph FS mount on the host that shares a pod&#39;s lifetime<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexcinder">cinder</a></b></td>
          <td>object</td>
          <td>
            Cinder represents a cinder volume attached and mounted on kubelets host machine. More info: https://examples.k8s.io/mysql-cinder-pd/README.md<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexconfigmap">configMap</a></b></td>
          <td>object</td>
          <td>
            ConfigMap represents a configMap that should populate this volume<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexcsi">csi</a></b></td>
          <td>object</td>
          <td>
            CSI (Container Storage Interface) represents ephemeral storage that is handled by certain external CSI drivers (Beta feature).<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexdownwardapi">downwardAPI</a></b></td>
          <td>object</td>
          <td>
            DownwardAPI represents downward API about the pod that should populate this volume<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexemptydir">emptyDir</a></b></td>
          <td>object</td>
          <td>
            EmptyDir represents a temporary directory that shares a pod&#39;s lifetime. More info: https://kubernetes.io/docs/concepts/storage/volumes#emptydir<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexephemeral">ephemeral</a></b></td>
          <td>object</td>
          <td>
            Ephemeral represents a volume that is handled by a cluster storage driver. The volume&#39;s lifecycle is tied to the pod that defines it - it will be created before the pod starts, and deleted when the pod is removed. 
 Use this if: a) the volume is only needed while the pod runs, b) features of normal volumes like restoring from snapshot or capacity    tracking are needed, c) the storage driver is specified through a storage class, and d) the storage driver supports dynamic volume provisioning through    a PersistentVolumeClaim (see EphemeralVolumeSource for more    information on the connection between this volume type    and PersistentVolumeClaim). 
 Use PersistentVolumeClaim or one of the vendor-specific APIs for volumes that persist for longer than the lifecycle of an individual pod. 
 Use CSI for light-weight local ephemeral volumes if the CSI driver is meant to be used that way - see the documentation of the driver for more information. 
 A pod can use both types of ephemeral volumes and persistent volumes at the same time.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexfc">fc</a></b></td>
          <td>object</td>
          <td>
            FC represents a Fibre Channel resource that is attached to a kubelet&#39;s host machine and then exposed to the pod.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexflexvolume">flexVolume</a></b></td>
          <td>object</td>
          <td>
            FlexVolume represents a generic volume resource that is provisioned/attached using an exec based plugin.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexflocker">flocker</a></b></td>
          <td>object</td>
          <td>
            Flocker represents a Flocker volume attached to a kubelet&#39;s host machine. This depends on the Flocker control service being running<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexgcepersistentdisk">gcePersistentDisk</a></b></td>
          <td>object</td>
          <td>
            GCEPersistentDisk represents a GCE Disk resource that is attached to a kubelet&#39;s host machine and then exposed to the pod. More info: https://kubernetes.io/docs/concepts/storage/volumes#gcepersistentdisk<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexgitrepo">gitRepo</a></b></td>
          <td>object</td>
          <td>
            GitRepo represents a git repository at a particular revision. DEPRECATED: GitRepo is deprecated. To provision a container with a git repo, mount an EmptyDir into an InitContainer that clones the repo using git, then mount the EmptyDir into the Pod&#39;s container.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexglusterfs">glusterfs</a></b></td>
          <td>object</td>
          <td>
            Glusterfs represents a Glusterfs mount on the host that shares a pod&#39;s lifetime. More info: https://examples.k8s.io/volumes/glusterfs/README.md<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexhostpath">hostPath</a></b></td>
          <td>object</td>
          <td>
            HostPath represents a pre-existing file or directory on the host machine that is directly exposed to the container. This is generally used for system agents or other privileged things that are allowed to see the host machine. Most containers will NOT need this. More info: https://kubernetes.io/docs/concepts/storage/volumes#hostpath --- TODO(jonesdl) We need to restrict who can use host directory mounts and who can/can not mount host directories as read/write.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexiscsi">iscsi</a></b></td>
          <td>object</td>
          <td>
            ISCSI represents an ISCSI Disk resource that is attached to a kubelet&#39;s host machine and then exposed to the pod. More info: https://examples.k8s.io/volumes/iscsi/README.md<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexnfs">nfs</a></b></td>
          <td>object</td>
          <td>
            NFS represents an NFS mount on the host that shares a pod&#39;s lifetime More info: https://kubernetes.io/docs/concepts/storage/volumes#nfs<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexpersistentvolumeclaim">persistentVolumeClaim</a></b></td>
          <td>object</td>
          <td>
            PersistentVolumeClaimVolumeSource represents a reference to a PersistentVolumeClaim in the same namespace. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#persistentvolumeclaims<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexphotonpersistentdisk">photonPersistentDisk</a></b></td>
          <td>object</td>
          <td>
            PhotonPersistentDisk represents a PhotonController persistent disk attached and mounted on kubelets host machine<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexportworxvolume">portworxVolume</a></b></td>
          <td>object</td>
          <td>
            PortworxVolume represents a portworx volume attached and mounted on kubelets host machine<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexprojected">projected</a></b></td>
          <td>object</td>
          <td>
            Items for all in one resources secrets, configmaps, and downward API<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexquobyte">quobyte</a></b></td>
          <td>object</td>
          <td>
            Quobyte represents a Quobyte mount on the host that shares a pod&#39;s lifetime<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexrbd">rbd</a></b></td>
          <td>object</td>
          <td>
            RBD represents a Rados Block Device mount on the host that shares a pod&#39;s lifetime. More info: https://examples.k8s.io/volumes/rbd/README.md<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexscaleio">scaleIO</a></b></td>
          <td>object</td>
          <td>
            ScaleIO represents a ScaleIO persistent volume attached and mounted on Kubernetes nodes.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexsecret">secret</a></b></td>
          <td>object</td>
          <td>
            Secret represents a secret that should populate this volume. More info: https://kubernetes.io/docs/concepts/storage/volumes#secret<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexstorageos">storageos</a></b></td>
          <td>object</td>
          <td>
            StorageOS represents a StorageOS volume attached and mounted on Kubernetes nodes.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexvspherevolume">vsphereVolume</a></b></td>
          <td>object</td>
          <td>
            VsphereVolume represents a vSphere volume attached and mounted on kubelets host machine<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].awsElasticBlockStore {#edgeworkloadspecpodspecvolumesindexawselasticblockstore}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



AWSElasticBlockStore represents an AWS Disk resource that is attached to a kubelet&#39;s host machine and then exposed to the pod. More info: https://kubernetes.io/docs/concepts/storage/volumes#awselasticblockstore
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>volumeID</b></td>
          <td>string</td>
          <td>
            Unique ID of the persistent disk resource in AWS (Amazon EBS volume). More info: https://kubernetes.io/docs/concepts/storage/volumes#awselasticblockstore<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>fsType</b></td>
          <td>string</td>
          <td>
            Filesystem type of the volume that you want to mount. Tip: Ensure that the filesystem type is supported by the host operating system. Examples: &#34;ext4&#34;, &#34;xfs&#34;, &#34;ntfs&#34;. Implicitly inferred to be &#34;ext4&#34; if unspecified. More info: https://kubernetes.io/docs/concepts/storage/volumes#awselasticblockstore TODO: how do we prevent errors in the filesystem from compromising the machine<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>partition</b></td>
          <td>integer</td>
          <td>
            The partition in the volume that you want to mount. If omitted, the default is to mount by volume name. Examples: For volume /dev/sda1, you specify the partition as &#34;1&#34;. Similarly, the volume partition for /dev/sda is &#34;0&#34; (or you can leave the property empty).<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            Specify &#34;true&#34; to force and set the ReadOnly property in VolumeMounts to &#34;true&#34;. If omitted, the default is &#34;false&#34;. More info: https://kubernetes.io/docs/concepts/storage/volumes#awselasticblockstore<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].azureDisk {#edgeworkloadspecpodspecvolumesindexazuredisk}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



AzureDisk represents an Azure Data Disk mount on the host and bind mount to the pod.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>diskName</b></td>
          <td>string</td>
          <td>
            The Name of the data disk in the blob storage<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>diskURI</b></td>
          <td>string</td>
          <td>
            The URI the data disk in the blob storage<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>cachingMode</b></td>
          <td>string</td>
          <td>
            Host Caching mode: None, Read Only, Read Write.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>fsType</b></td>
          <td>string</td>
          <td>
            Filesystem type to mount. Must be a filesystem type supported by the host operating system. Ex. &#34;ext4&#34;, &#34;xfs&#34;, &#34;ntfs&#34;. Implicitly inferred to be &#34;ext4&#34; if unspecified.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>kind</b></td>
          <td>string</td>
          <td>
            Expected values Shared: multiple blob disks per storage account  Dedicated: single blob disk per storage account  Managed: azure managed data disk (only in managed availability set). defaults to shared<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            Defaults to false (read/write). ReadOnly here will force the ReadOnly setting in VolumeMounts.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].azureFile {#edgeworkloadspecpodspecvolumesindexazurefile}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



AzureFile represents an Azure File Service mount on the host and bind mount to the pod.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>secretName</b></td>
          <td>string</td>
          <td>
            the name of secret that contains Azure Storage Account Name and Key<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>shareName</b></td>
          <td>string</td>
          <td>
            Share Name<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            Defaults to false (read/write). ReadOnly here will force the ReadOnly setting in VolumeMounts.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].cephfs {#edgeworkloadspecpodspecvolumesindexcephfs}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



CephFS represents a Ceph FS mount on the host that shares a pod&#39;s lifetime
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>monitors</b></td>
          <td>[]string</td>
          <td>
            Required: Monitors is a collection of Ceph monitors More info: https://examples.k8s.io/volumes/cephfs/README.md#how-to-use-it<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Optional: Used as the mounted root, rather than the full Ceph tree, default is /<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            Optional: Defaults to false (read/write). ReadOnly here will force the ReadOnly setting in VolumeMounts. More info: https://examples.k8s.io/volumes/cephfs/README.md#how-to-use-it<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>secretFile</b></td>
          <td>string</td>
          <td>
            Optional: SecretFile is the path to key ring for User, default is /etc/ceph/user.secret More info: https://examples.k8s.io/volumes/cephfs/README.md#how-to-use-it<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexcephfssecretref">secretRef</a></b></td>
          <td>object</td>
          <td>
            Optional: SecretRef is reference to the authentication secret for User, default is empty. More info: https://examples.k8s.io/volumes/cephfs/README.md#how-to-use-it<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>user</b></td>
          <td>string</td>
          <td>
            Optional: User is the rados user name, default is admin More info: https://examples.k8s.io/volumes/cephfs/README.md#how-to-use-it<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].cephfs.secretRef {#edgeworkloadspecpodspecvolumesindexcephfssecretref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexcephfs)</sup></sup>



Optional: SecretRef is reference to the authentication secret for User, default is empty. More info: https://examples.k8s.io/volumes/cephfs/README.md#how-to-use-it
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].cinder {#edgeworkloadspecpodspecvolumesindexcinder}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



Cinder represents a cinder volume attached and mounted on kubelets host machine. More info: https://examples.k8s.io/mysql-cinder-pd/README.md
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>volumeID</b></td>
          <td>string</td>
          <td>
            volume id used to identify the volume in cinder. More info: https://examples.k8s.io/mysql-cinder-pd/README.md<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>fsType</b></td>
          <td>string</td>
          <td>
            Filesystem type to mount. Must be a filesystem type supported by the host operating system. Examples: &#34;ext4&#34;, &#34;xfs&#34;, &#34;ntfs&#34;. Implicitly inferred to be &#34;ext4&#34; if unspecified. More info: https://examples.k8s.io/mysql-cinder-pd/README.md<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            Optional: Defaults to false (read/write). ReadOnly here will force the ReadOnly setting in VolumeMounts. More info: https://examples.k8s.io/mysql-cinder-pd/README.md<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexcindersecretref">secretRef</a></b></td>
          <td>object</td>
          <td>
            Optional: points to a secret object containing parameters used to connect to OpenStack.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].cinder.secretRef {#edgeworkloadspecpodspecvolumesindexcindersecretref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexcinder)</sup></sup>



Optional: points to a secret object containing parameters used to connect to OpenStack.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].configMap {#edgeworkloadspecpodspecvolumesindexconfigmap}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



ConfigMap represents a configMap that should populate this volume
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>defaultMode</b></td>
          <td>integer</td>
          <td>
            Optional: mode bits used to set permissions on created files by default. Must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. Defaults to 0644. Directories within the path are not affected by this setting. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexconfigmapitemsindex">items</a></b></td>
          <td>[]object</td>
          <td>
            If unspecified, each key-value pair in the Data field of the referenced ConfigMap will be projected into the volume as a file whose name is the key and content is the value. If specified, the listed keys will be projected into the specified paths, and unlisted keys will not be present. If a key is specified which is not present in the ConfigMap, the volume setup will error unless it is marked optional. Paths must be relative and may not contain the &#39;..&#39; path or start with &#39;..&#39;.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>optional</b></td>
          <td>boolean</td>
          <td>
            Specify whether the ConfigMap or its keys must be defined<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].configMap.items[index] {#edgeworkloadspecpodspecvolumesindexconfigmapitemsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexconfigmap)</sup></sup>



Maps a string key to a path within a volume.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            The key to project.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            The relative path of the file to map the key to. May not be an absolute path. May not contain the path element &#39;..&#39;. May not start with the string &#39;..&#39;.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>mode</b></td>
          <td>integer</td>
          <td>
            Optional: mode bits used to set permissions on this file. Must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].csi {#edgeworkloadspecpodspecvolumesindexcsi}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



CSI (Container Storage Interface) represents ephemeral storage that is handled by certain external CSI drivers (Beta feature).
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>driver</b></td>
          <td>string</td>
          <td>
            Driver is the name of the CSI driver that handles this volume. Consult with your admin for the correct name as registered in the cluster.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>fsType</b></td>
          <td>string</td>
          <td>
            Filesystem type to mount. Ex. &#34;ext4&#34;, &#34;xfs&#34;, &#34;ntfs&#34;. If not provided, the empty value is passed to the associated CSI driver which will determine the default filesystem to apply.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexcsinodepublishsecretref">nodePublishSecretRef</a></b></td>
          <td>object</td>
          <td>
            NodePublishSecretRef is a reference to the secret object containing sensitive information to pass to the CSI driver to complete the CSI NodePublishVolume and NodeUnpublishVolume calls. This field is optional, and  may be empty if no secret is required. If the secret object contains more than one secret, all secret references are passed.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            Specifies a read-only configuration for the volume. Defaults to false (read/write).<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>volumeAttributes</b></td>
          <td>map[string]string</td>
          <td>
            VolumeAttributes stores driver-specific properties that are passed to the CSI driver. Consult your driver&#39;s documentation for supported values.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].csi.nodePublishSecretRef {#edgeworkloadspecpodspecvolumesindexcsinodepublishsecretref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexcsi)</sup></sup>



NodePublishSecretRef is a reference to the secret object containing sensitive information to pass to the CSI driver to complete the CSI NodePublishVolume and NodeUnpublishVolume calls. This field is optional, and  may be empty if no secret is required. If the secret object contains more than one secret, all secret references are passed.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].downwardAPI {#edgeworkloadspecpodspecvolumesindexdownwardapi}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



DownwardAPI represents downward API about the pod that should populate this volume
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>defaultMode</b></td>
          <td>integer</td>
          <td>
            Optional: mode bits to use on created files by default. Must be a Optional: mode bits used to set permissions on created files by default. Must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. Defaults to 0644. Directories within the path are not affected by this setting. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexdownwardapiitemsindex">items</a></b></td>
          <td>[]object</td>
          <td>
            Items is a list of downward API volume file<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].downwardAPI.items[index] {#edgeworkloadspecpodspecvolumesindexdownwardapiitemsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexdownwardapi)</sup></sup>



DownwardAPIVolumeFile represents information to create the file containing the pod field
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Required: Path is  the relative path name of the file to be created. Must not be absolute or contain the &#39;..&#39; path. Must be utf-8 encoded. The first item of the relative path must not start with &#39;..&#39;<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexdownwardapiitemsindexfieldref">fieldRef</a></b></td>
          <td>object</td>
          <td>
            Required: Selects a field of the pod: only annotations, labels, name and namespace are supported.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>mode</b></td>
          <td>integer</td>
          <td>
            Optional: mode bits used to set permissions on this file, must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexdownwardapiitemsindexresourcefieldref">resourceFieldRef</a></b></td>
          <td>object</td>
          <td>
            Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, requests.cpu and requests.memory) are currently supported.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].downwardAPI.items[index].fieldRef {#edgeworkloadspecpodspecvolumesindexdownwardapiitemsindexfieldref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexdownwardapiitemsindex)</sup></sup>



Required: Selects a field of the pod: only annotations, labels, name and namespace are supported.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>fieldPath</b></td>
          <td>string</td>
          <td>
            Path of the field to select in the specified API version.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>apiVersion</b></td>
          <td>string</td>
          <td>
            Version of the schema the FieldPath is written in terms of, defaults to &#34;v1&#34;.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].downwardAPI.items[index].resourceFieldRef {#edgeworkloadspecpodspecvolumesindexdownwardapiitemsindexresourcefieldref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexdownwardapiitemsindex)</sup></sup>



Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, requests.cpu and requests.memory) are currently supported.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>resource</b></td>
          <td>string</td>
          <td>
            Required: resource to select<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>containerName</b></td>
          <td>string</td>
          <td>
            Container name: required for volumes, optional for env vars<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>divisor</b></td>
          <td>int or string</td>
          <td>
            Specifies the output format of the exposed resources, defaults to &#34;1&#34;<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].emptyDir {#edgeworkloadspecpodspecvolumesindexemptydir}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



EmptyDir represents a temporary directory that shares a pod&#39;s lifetime. More info: https://kubernetes.io/docs/concepts/storage/volumes#emptydir
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>medium</b></td>
          <td>string</td>
          <td>
            What type of storage medium should back this directory. The default is &#34;&#34; which means to use the node&#39;s default medium. Must be an empty string (default) or Memory. More info: https://kubernetes.io/docs/concepts/storage/volumes#emptydir<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>sizeLimit</b></td>
          <td>int or string</td>
          <td>
            Total amount of local storage required for this EmptyDir volume. The size limit is also applicable for memory medium. The maximum usage on memory medium EmptyDir would be the minimum value between the SizeLimit specified here and the sum of memory limits of all containers in a pod. The default is nil which means that the limit is undefined. More info: http://kubernetes.io/docs/user-guide/volumes#emptydir<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].ephemeral {#edgeworkloadspecpodspecvolumesindexephemeral}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



Ephemeral represents a volume that is handled by a cluster storage driver. The volume&#39;s lifecycle is tied to the pod that defines it - it will be created before the pod starts, and deleted when the pod is removed. 
 Use this if: a) the volume is only needed while the pod runs, b) features of normal volumes like restoring from snapshot or capacity    tracking are needed, c) the storage driver is specified through a storage class, and d) the storage driver supports dynamic volume provisioning through    a PersistentVolumeClaim (see EphemeralVolumeSource for more    information on the connection between this volume type    and PersistentVolumeClaim). 
 Use PersistentVolumeClaim or one of the vendor-specific APIs for volumes that persist for longer than the lifecycle of an individual pod. 
 Use CSI for light-weight local ephemeral volumes if the CSI driver is meant to be used that way - see the documentation of the driver for more information. 
 A pod can use both types of ephemeral volumes and persistent volumes at the same time.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplate">volumeClaimTemplate</a></b></td>
          <td>object</td>
          <td>
            Will be used to create a stand-alone PVC to provision the volume. The pod in which this EphemeralVolumeSource is embedded will be the owner of the PVC, i.e. the PVC will be deleted together with the pod.  The name of the PVC will be `&lt;pod name&gt;-&lt;volume name&gt;` where `&lt;volume name&gt;` is the name from the `PodSpec.Volumes` array entry. Pod validation will reject the pod if the concatenated name is not valid for a PVC (for example, too long). 
 An existing PVC with that name that is not owned by the pod will *not* be used for the pod to avoid using an unrelated volume by mistake. Starting the pod is then blocked until the unrelated PVC is removed. If such a pre-created PVC is meant to be used by the pod, the PVC has to updated with an owner reference to the pod once the pod exists. Normally this should not be necessary, but it may be useful when manually reconstructing a broken cluster. 
 This field is read-only and no changes will be made by Kubernetes to the PVC after it has been created. 
 Required, must not be nil.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].ephemeral.volumeClaimTemplate {#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplate}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexephemeral)</sup></sup>



Will be used to create a stand-alone PVC to provision the volume. The pod in which this EphemeralVolumeSource is embedded will be the owner of the PVC, i.e. the PVC will be deleted together with the pod.  The name of the PVC will be `&lt;pod name&gt;-&lt;volume name&gt;` where `&lt;volume name&gt;` is the name from the `PodSpec.Volumes` array entry. Pod validation will reject the pod if the concatenated name is not valid for a PVC (for example, too long). 
 An existing PVC with that name that is not owned by the pod will *not* be used for the pod to avoid using an unrelated volume by mistake. Starting the pod is then blocked until the unrelated PVC is removed. If such a pre-created PVC is meant to be used by the pod, the PVC has to updated with an owner reference to the pod once the pod exists. Normally this should not be necessary, but it may be useful when manually reconstructing a broken cluster. 
 This field is read-only and no changes will be made by Kubernetes to the PVC after it has been created. 
 Required, must not be nil.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplatespec">spec</a></b></td>
          <td>object</td>
          <td>
            The specification for the PersistentVolumeClaim. The entire content is copied unchanged into the PVC that gets created from this template. The same fields as in a PersistentVolumeClaim are also valid here.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>metadata</b></td>
          <td>object</td>
          <td>
            May contain labels and annotations that will be copied into the PVC when creating it. No other fields are allowed and will be rejected during validation.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].ephemeral.volumeClaimTemplate.spec {#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplatespec}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplate)</sup></sup>



The specification for the PersistentVolumeClaim. The entire content is copied unchanged into the PVC that gets created from this template. The same fields as in a PersistentVolumeClaim are also valid here.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>accessModes</b></td>
          <td>[]string</td>
          <td>
            AccessModes contains the desired access modes the volume should have. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#access-modes-1<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplatespecdatasource">dataSource</a></b></td>
          <td>object</td>
          <td>
            This field can be used to specify either: * An existing VolumeSnapshot object (snapshot.storage.k8s.io/VolumeSnapshot) * An existing PVC (PersistentVolumeClaim) If the provisioner or an external controller can support the specified data source, it will create a new volume based on the contents of the specified data source. If the AnyVolumeDataSource feature gate is enabled, this field will always have the same contents as the DataSourceRef field.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplatespecdatasourceref">dataSourceRef</a></b></td>
          <td>object</td>
          <td>
            Specifies the object from which to populate the volume with data, if a non-empty volume is desired. This may be any local object from a non-empty API group (non core object) or a PersistentVolumeClaim object. When this field is specified, volume binding will only succeed if the type of the specified object matches some installed volume populator or dynamic provisioner. This field will replace the functionality of the DataSource field and as such if both fields are non-empty, they must have the same value. For backwards compatibility, both fields (DataSource and DataSourceRef) will be set to the same value automatically if one of them is empty and the other is non-empty. There are two important differences between DataSource and DataSourceRef: * While DataSource only allows two specific types of objects, DataSourceRef   allows any non-core object, as well as PersistentVolumeClaim objects. * While DataSource ignores disallowed values (dropping them), DataSourceRef   preserves all values, and generates an error if a disallowed value is   specified. (Alpha) Using this field requires the AnyVolumeDataSource feature gate to be enabled.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplatespecresources">resources</a></b></td>
          <td>object</td>
          <td>
            Resources represents the minimum resources the volume should have. If RecoverVolumeExpansionFailure feature is enabled users are allowed to specify resource requirements that are lower than previous value but must still be higher than capacity recorded in the status field of the claim. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#resources<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplatespecselector">selector</a></b></td>
          <td>object</td>
          <td>
            A label query over volumes to consider for binding.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>storageClassName</b></td>
          <td>string</td>
          <td>
            Name of the StorageClass required by the claim. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#class-1<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>volumeMode</b></td>
          <td>string</td>
          <td>
            volumeMode defines what type of volume is required by the claim. Value of Filesystem is implied when not included in claim spec.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>volumeName</b></td>
          <td>string</td>
          <td>
            VolumeName is the binding reference to the PersistentVolume backing this claim.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].ephemeral.volumeClaimTemplate.spec.dataSource {#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplatespecdatasource}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplatespec)</sup></sup>



This field can be used to specify either: * An existing VolumeSnapshot object (snapshot.storage.k8s.io/VolumeSnapshot) * An existing PVC (PersistentVolumeClaim) If the provisioner or an external controller can support the specified data source, it will create a new volume based on the contents of the specified data source. If the AnyVolumeDataSource feature gate is enabled, this field will always have the same contents as the DataSourceRef field.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>kind</b></td>
          <td>string</td>
          <td>
            Kind is the type of resource being referenced<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name is the name of resource being referenced<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>apiGroup</b></td>
          <td>string</td>
          <td>
            APIGroup is the group for the resource being referenced. If APIGroup is not specified, the specified Kind must be in the core API group. For any other third-party types, APIGroup is required.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].ephemeral.volumeClaimTemplate.spec.dataSourceRef {#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplatespecdatasourceref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplatespec)</sup></sup>



Specifies the object from which to populate the volume with data, if a non-empty volume is desired. This may be any local object from a non-empty API group (non core object) or a PersistentVolumeClaim object. When this field is specified, volume binding will only succeed if the type of the specified object matches some installed volume populator or dynamic provisioner. This field will replace the functionality of the DataSource field and as such if both fields are non-empty, they must have the same value. For backwards compatibility, both fields (DataSource and DataSourceRef) will be set to the same value automatically if one of them is empty and the other is non-empty. There are two important differences between DataSource and DataSourceRef: * While DataSource only allows two specific types of objects, DataSourceRef   allows any non-core object, as well as PersistentVolumeClaim objects. * While DataSource ignores disallowed values (dropping them), DataSourceRef   preserves all values, and generates an error if a disallowed value is   specified. (Alpha) Using this field requires the AnyVolumeDataSource feature gate to be enabled.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>kind</b></td>
          <td>string</td>
          <td>
            Kind is the type of resource being referenced<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name is the name of resource being referenced<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>apiGroup</b></td>
          <td>string</td>
          <td>
            APIGroup is the group for the resource being referenced. If APIGroup is not specified, the specified Kind must be in the core API group. For any other third-party types, APIGroup is required.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].ephemeral.volumeClaimTemplate.spec.resources {#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplatespecresources}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplatespec)</sup></sup>



Resources represents the minimum resources the volume should have. If RecoverVolumeExpansionFailure feature is enabled users are allowed to specify resource requirements that are lower than previous value but must still be higher than capacity recorded in the status field of the claim. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#resources
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>limits</b></td>
          <td>map[string]int or string</td>
          <td>
            Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>requests</b></td>
          <td>map[string]int or string</td>
          <td>
            Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].ephemeral.volumeClaimTemplate.spec.selector {#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplatespecselector}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplatespec)</sup></sup>



A label query over volumes to consider for binding.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplatespecselectormatchexpressionsindex">matchExpressions</a></b></td>
          <td>[]object</td>
          <td>
            matchExpressions is a list of label selector requirements. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>matchLabels</b></td>
          <td>map[string]string</td>
          <td>
            matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is &#34;key&#34;, the operator is &#34;In&#34;, and the values array contains only &#34;value&#34;. The requirements are ANDed.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].ephemeral.volumeClaimTemplate.spec.selector.matchExpressions[index] {#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplatespecselectormatchexpressionsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexephemeralvolumeclaimtemplatespecselector)</sup></sup>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            key is the label key that the selector applies to.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>operator</b></td>
          <td>string</td>
          <td>
            operator represents a key&#39;s relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>values</b></td>
          <td>[]string</td>
          <td>
            values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].fc {#edgeworkloadspecpodspecvolumesindexfc}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



FC represents a Fibre Channel resource that is attached to a kubelet&#39;s host machine and then exposed to the pod.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>fsType</b></td>
          <td>string</td>
          <td>
            Filesystem type to mount. Must be a filesystem type supported by the host operating system. Ex. &#34;ext4&#34;, &#34;xfs&#34;, &#34;ntfs&#34;. Implicitly inferred to be &#34;ext4&#34; if unspecified. TODO: how do we prevent errors in the filesystem from compromising the machine<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>lun</b></td>
          <td>integer</td>
          <td>
            Optional: FC target lun number<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            Optional: Defaults to false (read/write). ReadOnly here will force the ReadOnly setting in VolumeMounts.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>targetWWNs</b></td>
          <td>[]string</td>
          <td>
            Optional: FC target worldwide names (WWNs)<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>wwids</b></td>
          <td>[]string</td>
          <td>
            Optional: FC volume world wide identifiers (wwids) Either wwids or combination of targetWWNs and lun must be set, but not both simultaneously.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].flexVolume {#edgeworkloadspecpodspecvolumesindexflexvolume}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



FlexVolume represents a generic volume resource that is provisioned/attached using an exec based plugin.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>driver</b></td>
          <td>string</td>
          <td>
            Driver is the name of the driver to use for this volume.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>fsType</b></td>
          <td>string</td>
          <td>
            Filesystem type to mount. Must be a filesystem type supported by the host operating system. Ex. &#34;ext4&#34;, &#34;xfs&#34;, &#34;ntfs&#34;. The default filesystem depends on FlexVolume script.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>options</b></td>
          <td>map[string]string</td>
          <td>
            Optional: Extra command options if any.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            Optional: Defaults to false (read/write). ReadOnly here will force the ReadOnly setting in VolumeMounts.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexflexvolumesecretref">secretRef</a></b></td>
          <td>object</td>
          <td>
            Optional: SecretRef is reference to the secret object containing sensitive information to pass to the plugin scripts. This may be empty if no secret object is specified. If the secret object contains more than one secret, all secrets are passed to the plugin scripts.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].flexVolume.secretRef {#edgeworkloadspecpodspecvolumesindexflexvolumesecretref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexflexvolume)</sup></sup>



Optional: SecretRef is reference to the secret object containing sensitive information to pass to the plugin scripts. This may be empty if no secret object is specified. If the secret object contains more than one secret, all secrets are passed to the plugin scripts.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].flocker {#edgeworkloadspecpodspecvolumesindexflocker}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



Flocker represents a Flocker volume attached to a kubelet&#39;s host machine. This depends on the Flocker control service being running
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>datasetName</b></td>
          <td>string</td>
          <td>
            Name of the dataset stored as metadata -&gt; name on the dataset for Flocker should be considered as deprecated<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>datasetUUID</b></td>
          <td>string</td>
          <td>
            UUID of the dataset. This is unique identifier of a Flocker dataset<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].gcePersistentDisk {#edgeworkloadspecpodspecvolumesindexgcepersistentdisk}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



GCEPersistentDisk represents a GCE Disk resource that is attached to a kubelet&#39;s host machine and then exposed to the pod. More info: https://kubernetes.io/docs/concepts/storage/volumes#gcepersistentdisk
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>pdName</b></td>
          <td>string</td>
          <td>
            Unique name of the PD resource in GCE. Used to identify the disk in GCE. More info: https://kubernetes.io/docs/concepts/storage/volumes#gcepersistentdisk<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>fsType</b></td>
          <td>string</td>
          <td>
            Filesystem type of the volume that you want to mount. Tip: Ensure that the filesystem type is supported by the host operating system. Examples: &#34;ext4&#34;, &#34;xfs&#34;, &#34;ntfs&#34;. Implicitly inferred to be &#34;ext4&#34; if unspecified. More info: https://kubernetes.io/docs/concepts/storage/volumes#gcepersistentdisk TODO: how do we prevent errors in the filesystem from compromising the machine<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>partition</b></td>
          <td>integer</td>
          <td>
            The partition in the volume that you want to mount. If omitted, the default is to mount by volume name. Examples: For volume /dev/sda1, you specify the partition as &#34;1&#34;. Similarly, the volume partition for /dev/sda is &#34;0&#34; (or you can leave the property empty). More info: https://kubernetes.io/docs/concepts/storage/volumes#gcepersistentdisk<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            ReadOnly here will force the ReadOnly setting in VolumeMounts. Defaults to false. More info: https://kubernetes.io/docs/concepts/storage/volumes#gcepersistentdisk<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].gitRepo {#edgeworkloadspecpodspecvolumesindexgitrepo}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



GitRepo represents a git repository at a particular revision. DEPRECATED: GitRepo is deprecated. To provision a container with a git repo, mount an EmptyDir into an InitContainer that clones the repo using git, then mount the EmptyDir into the Pod&#39;s container.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>repository</b></td>
          <td>string</td>
          <td>
            Repository URL<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>directory</b></td>
          <td>string</td>
          <td>
            Target directory name. Must not contain or start with &#39;..&#39;.  If &#39;.&#39; is supplied, the volume directory will be the git repository.  Otherwise, if specified, the volume will contain the git repository in the subdirectory with the given name.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>revision</b></td>
          <td>string</td>
          <td>
            Commit hash for the specified revision.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].glusterfs {#edgeworkloadspecpodspecvolumesindexglusterfs}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



Glusterfs represents a Glusterfs mount on the host that shares a pod&#39;s lifetime. More info: https://examples.k8s.io/volumes/glusterfs/README.md
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>endpoints</b></td>
          <td>string</td>
          <td>
            EndpointsName is the endpoint name that details Glusterfs topology. More info: https://examples.k8s.io/volumes/glusterfs/README.md#create-a-pod<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path is the Glusterfs volume path. More info: https://examples.k8s.io/volumes/glusterfs/README.md#create-a-pod<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            ReadOnly here will force the Glusterfs volume to be mounted with read-only permissions. Defaults to false. More info: https://examples.k8s.io/volumes/glusterfs/README.md#create-a-pod<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].hostPath {#edgeworkloadspecpodspecvolumesindexhostpath}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



HostPath represents a pre-existing file or directory on the host machine that is directly exposed to the container. This is generally used for system agents or other privileged things that are allowed to see the host machine. Most containers will NOT need this. More info: https://kubernetes.io/docs/concepts/storage/volumes#hostpath --- TODO(jonesdl) We need to restrict who can use host directory mounts and who can/can not mount host directories as read/write.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path of the directory on the host. If the path is a symlink, it will follow the link to the real path. More info: https://kubernetes.io/docs/concepts/storage/volumes#hostpath<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>type</b></td>
          <td>string</td>
          <td>
            Type for HostPath Volume Defaults to &#34;&#34; More info: https://kubernetes.io/docs/concepts/storage/volumes#hostpath<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].iscsi {#edgeworkloadspecpodspecvolumesindexiscsi}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



ISCSI represents an ISCSI Disk resource that is attached to a kubelet&#39;s host machine and then exposed to the pod. More info: https://examples.k8s.io/volumes/iscsi/README.md
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>iqn</b></td>
          <td>string</td>
          <td>
            Target iSCSI Qualified Name.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>lun</b></td>
          <td>integer</td>
          <td>
            iSCSI Target Lun number.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>targetPortal</b></td>
          <td>string</td>
          <td>
            iSCSI Target Portal. The Portal is either an IP or ip_addr:port if the port is other than default (typically TCP ports 860 and 3260).<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>chapAuthDiscovery</b></td>
          <td>boolean</td>
          <td>
            whether support iSCSI Discovery CHAP authentication<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>chapAuthSession</b></td>
          <td>boolean</td>
          <td>
            whether support iSCSI Session CHAP authentication<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>fsType</b></td>
          <td>string</td>
          <td>
            Filesystem type of the volume that you want to mount. Tip: Ensure that the filesystem type is supported by the host operating system. Examples: &#34;ext4&#34;, &#34;xfs&#34;, &#34;ntfs&#34;. Implicitly inferred to be &#34;ext4&#34; if unspecified. More info: https://kubernetes.io/docs/concepts/storage/volumes#iscsi TODO: how do we prevent errors in the filesystem from compromising the machine<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>initiatorName</b></td>
          <td>string</td>
          <td>
            Custom iSCSI Initiator Name. If initiatorName is specified with iscsiInterface simultaneously, new iSCSI interface &lt;target portal&gt;:&lt;volume name&gt; will be created for the connection.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>iscsiInterface</b></td>
          <td>string</td>
          <td>
            iSCSI Interface Name that uses an iSCSI transport. Defaults to &#39;default&#39; (tcp).<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>portals</b></td>
          <td>[]string</td>
          <td>
            iSCSI Target Portal List. The portal is either an IP or ip_addr:port if the port is other than default (typically TCP ports 860 and 3260).<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            ReadOnly here will force the ReadOnly setting in VolumeMounts. Defaults to false.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexiscsisecretref">secretRef</a></b></td>
          <td>object</td>
          <td>
            CHAP Secret for iSCSI target and initiator authentication<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].iscsi.secretRef {#edgeworkloadspecpodspecvolumesindexiscsisecretref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexiscsi)</sup></sup>



CHAP Secret for iSCSI target and initiator authentication
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].nfs {#edgeworkloadspecpodspecvolumesindexnfs}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



NFS represents an NFS mount on the host that shares a pod&#39;s lifetime More info: https://kubernetes.io/docs/concepts/storage/volumes#nfs
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path that is exported by the NFS server. More info: https://kubernetes.io/docs/concepts/storage/volumes#nfs<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>server</b></td>
          <td>string</td>
          <td>
            Server is the hostname or IP address of the NFS server. More info: https://kubernetes.io/docs/concepts/storage/volumes#nfs<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            ReadOnly here will force the NFS export to be mounted with read-only permissions. Defaults to false. More info: https://kubernetes.io/docs/concepts/storage/volumes#nfs<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].persistentVolumeClaim {#edgeworkloadspecpodspecvolumesindexpersistentvolumeclaim}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



PersistentVolumeClaimVolumeSource represents a reference to a PersistentVolumeClaim in the same namespace. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#persistentvolumeclaims
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>claimName</b></td>
          <td>string</td>
          <td>
            ClaimName is the name of a PersistentVolumeClaim in the same namespace as the pod using this volume. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#persistentvolumeclaims<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            Will force the ReadOnly setting in VolumeMounts. Default false.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].photonPersistentDisk {#edgeworkloadspecpodspecvolumesindexphotonpersistentdisk}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



PhotonPersistentDisk represents a PhotonController persistent disk attached and mounted on kubelets host machine
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>pdID</b></td>
          <td>string</td>
          <td>
            ID that identifies Photon Controller persistent disk<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>fsType</b></td>
          <td>string</td>
          <td>
            Filesystem type to mount. Must be a filesystem type supported by the host operating system. Ex. &#34;ext4&#34;, &#34;xfs&#34;, &#34;ntfs&#34;. Implicitly inferred to be &#34;ext4&#34; if unspecified.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].portworxVolume {#edgeworkloadspecpodspecvolumesindexportworxvolume}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



PortworxVolume represents a portworx volume attached and mounted on kubelets host machine
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>volumeID</b></td>
          <td>string</td>
          <td>
            VolumeID uniquely identifies a Portworx volume<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>fsType</b></td>
          <td>string</td>
          <td>
            FSType represents the filesystem type to mount Must be a filesystem type supported by the host operating system. Ex. &#34;ext4&#34;, &#34;xfs&#34;. Implicitly inferred to be &#34;ext4&#34; if unspecified.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            Defaults to false (read/write). ReadOnly here will force the ReadOnly setting in VolumeMounts.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].projected {#edgeworkloadspecpodspecvolumesindexprojected}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



Items for all in one resources secrets, configmaps, and downward API
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>defaultMode</b></td>
          <td>integer</td>
          <td>
            Mode bits used to set permissions on created files by default. Must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. Directories within the path are not affected by this setting. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexprojectedsourcesindex">sources</a></b></td>
          <td>[]object</td>
          <td>
            list of volume projections<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].projected.sources[index] {#edgeworkloadspecpodspecvolumesindexprojectedsourcesindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexprojected)</sup></sup>



Projection that may be projected along with other supported volume types
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexconfigmap">configMap</a></b></td>
          <td>object</td>
          <td>
            information about the configMap data to project<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexdownwardapi">downwardAPI</a></b></td>
          <td>object</td>
          <td>
            information about the downwardAPI data to project<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexsecret">secret</a></b></td>
          <td>object</td>
          <td>
            information about the secret data to project<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexserviceaccounttoken">serviceAccountToken</a></b></td>
          <td>object</td>
          <td>
            information about the serviceAccountToken data to project<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].projected.sources[index].configMap {#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexconfigmap}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexprojectedsourcesindex)</sup></sup>



information about the configMap data to project
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexconfigmapitemsindex">items</a></b></td>
          <td>[]object</td>
          <td>
            If unspecified, each key-value pair in the Data field of the referenced ConfigMap will be projected into the volume as a file whose name is the key and content is the value. If specified, the listed keys will be projected into the specified paths, and unlisted keys will not be present. If a key is specified which is not present in the ConfigMap, the volume setup will error unless it is marked optional. Paths must be relative and may not contain the &#39;..&#39; path or start with &#39;..&#39;.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>optional</b></td>
          <td>boolean</td>
          <td>
            Specify whether the ConfigMap or its keys must be defined<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].projected.sources[index].configMap.items[index] {#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexconfigmapitemsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexconfigmap)</sup></sup>



Maps a string key to a path within a volume.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            The key to project.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            The relative path of the file to map the key to. May not be an absolute path. May not contain the path element &#39;..&#39;. May not start with the string &#39;..&#39;.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>mode</b></td>
          <td>integer</td>
          <td>
            Optional: mode bits used to set permissions on this file. Must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].projected.sources[index].downwardAPI {#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexdownwardapi}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexprojectedsourcesindex)</sup></sup>



information about the downwardAPI data to project
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexdownwardapiitemsindex">items</a></b></td>
          <td>[]object</td>
          <td>
            Items is a list of DownwardAPIVolume file<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].projected.sources[index].downwardAPI.items[index] {#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexdownwardapiitemsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexdownwardapi)</sup></sup>



DownwardAPIVolumeFile represents information to create the file containing the pod field
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Required: Path is  the relative path name of the file to be created. Must not be absolute or contain the &#39;..&#39; path. Must be utf-8 encoded. The first item of the relative path must not start with &#39;..&#39;<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexdownwardapiitemsindexfieldref">fieldRef</a></b></td>
          <td>object</td>
          <td>
            Required: Selects a field of the pod: only annotations, labels, name and namespace are supported.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>mode</b></td>
          <td>integer</td>
          <td>
            Optional: mode bits used to set permissions on this file, must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexdownwardapiitemsindexresourcefieldref">resourceFieldRef</a></b></td>
          <td>object</td>
          <td>
            Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, requests.cpu and requests.memory) are currently supported.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].projected.sources[index].downwardAPI.items[index].fieldRef {#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexdownwardapiitemsindexfieldref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexdownwardapiitemsindex)</sup></sup>



Required: Selects a field of the pod: only annotations, labels, name and namespace are supported.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>fieldPath</b></td>
          <td>string</td>
          <td>
            Path of the field to select in the specified API version.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>apiVersion</b></td>
          <td>string</td>
          <td>
            Version of the schema the FieldPath is written in terms of, defaults to &#34;v1&#34;.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].projected.sources[index].downwardAPI.items[index].resourceFieldRef {#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexdownwardapiitemsindexresourcefieldref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexdownwardapiitemsindex)</sup></sup>



Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, requests.cpu and requests.memory) are currently supported.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>resource</b></td>
          <td>string</td>
          <td>
            Required: resource to select<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>containerName</b></td>
          <td>string</td>
          <td>
            Container name: required for volumes, optional for env vars<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>divisor</b></td>
          <td>int or string</td>
          <td>
            Specifies the output format of the exposed resources, defaults to &#34;1&#34;<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].projected.sources[index].secret {#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexsecret}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexprojectedsourcesindex)</sup></sup>



information about the secret data to project
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexsecretitemsindex">items</a></b></td>
          <td>[]object</td>
          <td>
            If unspecified, each key-value pair in the Data field of the referenced Secret will be projected into the volume as a file whose name is the key and content is the value. If specified, the listed keys will be projected into the specified paths, and unlisted keys will not be present. If a key is specified which is not present in the Secret, the volume setup will error unless it is marked optional. Paths must be relative and may not contain the &#39;..&#39; path or start with &#39;..&#39;.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>optional</b></td>
          <td>boolean</td>
          <td>
            Specify whether the Secret or its key must be defined<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].projected.sources[index].secret.items[index] {#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexsecretitemsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexsecret)</sup></sup>



Maps a string key to a path within a volume.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            The key to project.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            The relative path of the file to map the key to. May not be an absolute path. May not contain the path element &#39;..&#39;. May not start with the string &#39;..&#39;.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>mode</b></td>
          <td>integer</td>
          <td>
            Optional: mode bits used to set permissions on this file. Must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].projected.sources[index].serviceAccountToken {#edgeworkloadspecpodspecvolumesindexprojectedsourcesindexserviceaccounttoken}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexprojectedsourcesindex)</sup></sup>



information about the serviceAccountToken data to project
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            Path is the path relative to the mount point of the file to project the token into.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>audience</b></td>
          <td>string</td>
          <td>
            Audience is the intended audience of the token. A recipient of a token must identify itself with an identifier specified in the audience of the token, and otherwise should reject the token. The audience defaults to the identifier of the apiserver.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>expirationSeconds</b></td>
          <td>integer</td>
          <td>
            ExpirationSeconds is the requested duration of validity of the service account token. As the token approaches expiration, the kubelet volume plugin will proactively rotate the service account token. The kubelet will start trying to rotate the token if the token is older than 80 percent of its time to live or if the token is older than 24 hours.Defaults to 1 hour and must be at least 10 minutes.<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].quobyte {#edgeworkloadspecpodspecvolumesindexquobyte}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



Quobyte represents a Quobyte mount on the host that shares a pod&#39;s lifetime
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>registry</b></td>
          <td>string</td>
          <td>
            Registry represents a single or multiple Quobyte Registry services specified as a string as host:port pair (multiple entries are separated with commas) which acts as the central registry for volumes<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>volume</b></td>
          <td>string</td>
          <td>
            Volume is a string that references an already created Quobyte volume by name.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>group</b></td>
          <td>string</td>
          <td>
            Group to map volume access to Default is no group<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            ReadOnly here will force the Quobyte volume to be mounted with read-only permissions. Defaults to false.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>tenant</b></td>
          <td>string</td>
          <td>
            Tenant owning the given Quobyte volume in the Backend Used with dynamically provisioned Quobyte volumes, value is set by the plugin<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>user</b></td>
          <td>string</td>
          <td>
            User to map volume access to Defaults to serivceaccount user<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].rbd {#edgeworkloadspecpodspecvolumesindexrbd}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



RBD represents a Rados Block Device mount on the host that shares a pod&#39;s lifetime. More info: https://examples.k8s.io/volumes/rbd/README.md
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>image</b></td>
          <td>string</td>
          <td>
            The rados image name. More info: https://examples.k8s.io/volumes/rbd/README.md#how-to-use-it<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>monitors</b></td>
          <td>[]string</td>
          <td>
            A collection of Ceph monitors. More info: https://examples.k8s.io/volumes/rbd/README.md#how-to-use-it<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>fsType</b></td>
          <td>string</td>
          <td>
            Filesystem type of the volume that you want to mount. Tip: Ensure that the filesystem type is supported by the host operating system. Examples: &#34;ext4&#34;, &#34;xfs&#34;, &#34;ntfs&#34;. Implicitly inferred to be &#34;ext4&#34; if unspecified. More info: https://kubernetes.io/docs/concepts/storage/volumes#rbd TODO: how do we prevent errors in the filesystem from compromising the machine<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>keyring</b></td>
          <td>string</td>
          <td>
            Keyring is the path to key ring for RBDUser. Default is /etc/ceph/keyring. More info: https://examples.k8s.io/volumes/rbd/README.md#how-to-use-it<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>pool</b></td>
          <td>string</td>
          <td>
            The rados pool name. Default is rbd. More info: https://examples.k8s.io/volumes/rbd/README.md#how-to-use-it<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            ReadOnly here will force the ReadOnly setting in VolumeMounts. Defaults to false. More info: https://examples.k8s.io/volumes/rbd/README.md#how-to-use-it<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexrbdsecretref">secretRef</a></b></td>
          <td>object</td>
          <td>
            SecretRef is name of the authentication secret for RBDUser. If provided overrides keyring. Default is nil. More info: https://examples.k8s.io/volumes/rbd/README.md#how-to-use-it<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>user</b></td>
          <td>string</td>
          <td>
            The rados user name. Default is admin. More info: https://examples.k8s.io/volumes/rbd/README.md#how-to-use-it<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].rbd.secretRef {#edgeworkloadspecpodspecvolumesindexrbdsecretref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexrbd)</sup></sup>



SecretRef is name of the authentication secret for RBDUser. If provided overrides keyring. Default is nil. More info: https://examples.k8s.io/volumes/rbd/README.md#how-to-use-it
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].scaleIO {#edgeworkloadspecpodspecvolumesindexscaleio}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



ScaleIO represents a ScaleIO persistent volume attached and mounted on Kubernetes nodes.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>gateway</b></td>
          <td>string</td>
          <td>
            The host address of the ScaleIO API Gateway.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexscaleiosecretref">secretRef</a></b></td>
          <td>object</td>
          <td>
            SecretRef references to the secret for ScaleIO user and other sensitive information. If this is not provided, Login operation will fail.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>system</b></td>
          <td>string</td>
          <td>
            The name of the storage system as configured in ScaleIO.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>fsType</b></td>
          <td>string</td>
          <td>
            Filesystem type to mount. Must be a filesystem type supported by the host operating system. Ex. &#34;ext4&#34;, &#34;xfs&#34;, &#34;ntfs&#34;. Default is &#34;xfs&#34;.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>protectionDomain</b></td>
          <td>string</td>
          <td>
            The name of the ScaleIO Protection Domain for the configured storage.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            Defaults to false (read/write). ReadOnly here will force the ReadOnly setting in VolumeMounts.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>sslEnabled</b></td>
          <td>boolean</td>
          <td>
            Flag to enable/disable SSL communication with Gateway, default false<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>storageMode</b></td>
          <td>string</td>
          <td>
            Indicates whether the storage for a volume should be ThickProvisioned or ThinProvisioned. Default is ThinProvisioned.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>storagePool</b></td>
          <td>string</td>
          <td>
            The ScaleIO Storage Pool associated with the protection domain.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>volumeName</b></td>
          <td>string</td>
          <td>
            The name of a volume already created in the ScaleIO system that is associated with this volume source.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].scaleIO.secretRef {#edgeworkloadspecpodspecvolumesindexscaleiosecretref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexscaleio)</sup></sup>



SecretRef references to the secret for ScaleIO user and other sensitive information. If this is not provided, Login operation will fail.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].secret {#edgeworkloadspecpodspecvolumesindexsecret}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



Secret represents a secret that should populate this volume. More info: https://kubernetes.io/docs/concepts/storage/volumes#secret
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>defaultMode</b></td>
          <td>integer</td>
          <td>
            Optional: mode bits used to set permissions on created files by default. Must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. Defaults to 0644. Directories within the path are not affected by this setting. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexsecretitemsindex">items</a></b></td>
          <td>[]object</td>
          <td>
            If unspecified, each key-value pair in the Data field of the referenced Secret will be projected into the volume as a file whose name is the key and content is the value. If specified, the listed keys will be projected into the specified paths, and unlisted keys will not be present. If a key is specified which is not present in the Secret, the volume setup will error unless it is marked optional. Paths must be relative and may not contain the &#39;..&#39; path or start with &#39;..&#39;.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>optional</b></td>
          <td>boolean</td>
          <td>
            Specify whether the Secret or its keys must be defined<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>secretName</b></td>
          <td>string</td>
          <td>
            Name of the secret in the pod&#39;s namespace to use. More info: https://kubernetes.io/docs/concepts/storage/volumes#secret<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].secret.items[index] {#edgeworkloadspecpodspecvolumesindexsecretitemsindex}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexsecret)</sup></sup>



Maps a string key to a path within a volume.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>key</b></td>
          <td>string</td>
          <td>
            The key to project.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>path</b></td>
          <td>string</td>
          <td>
            The relative path of the file to map the key to. May not be an absolute path. May not contain the path element &#39;..&#39;. May not start with the string &#39;..&#39;.<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>mode</b></td>
          <td>integer</td>
          <td>
            Optional: mode bits used to set permissions on this file. Must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set.<br/>
            <br/>
              <i>Format</i>: int32<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].storageos {#edgeworkloadspecpodspecvolumesindexstorageos}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



StorageOS represents a StorageOS volume attached and mounted on Kubernetes nodes.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>fsType</b></td>
          <td>string</td>
          <td>
            Filesystem type to mount. Must be a filesystem type supported by the host operating system. Ex. &#34;ext4&#34;, &#34;xfs&#34;, &#34;ntfs&#34;. Implicitly inferred to be &#34;ext4&#34; if unspecified.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>readOnly</b></td>
          <td>boolean</td>
          <td>
            Defaults to false (read/write). ReadOnly here will force the ReadOnly setting in VolumeMounts.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#edgeworkloadspecpodspecvolumesindexstorageossecretref">secretRef</a></b></td>
          <td>object</td>
          <td>
            SecretRef specifies the secret to use for obtaining the StorageOS API credentials.  If not specified, default values will be attempted.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>volumeName</b></td>
          <td>string</td>
          <td>
            VolumeName is the human-readable name of the StorageOS volume.  Volume names are only unique within a namespace.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>volumeNamespace</b></td>
          <td>string</td>
          <td>
            VolumeNamespace specifies the scope of the volume within StorageOS.  If no namespace is specified then the Pod&#39;s namespace will be used.  This allows the Kubernetes name scoping to be mirrored within StorageOS for tighter integration. Set VolumeName to any name to override the default behaviour. Set to &#34;default&#34; if you are not using namespaces within StorageOS. Namespaces that do not pre-exist within StorageOS will be created.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].storageos.secretRef {#edgeworkloadspecpodspecvolumesindexstorageossecretref}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindexstorageos)</sup></sup>



SecretRef specifies the secret to use for obtaining the StorageOS API credentials.  If not specified, default values will be attempted.
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>name</b></td>
          <td>string</td>
          <td>
            Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid?<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### EdgeWorkload.spec.pod.spec.volumes[index].vsphereVolume {#edgeworkloadspecpodspecvolumesindexvspherevolume}
<sup><sup>[↩ Parent](#edgeworkloadspecpodspecvolumesindex)</sup></sup>



VsphereVolume represents a vSphere volume attached and mounted on kubelets host machine
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>volumePath</b></td>
          <td>string</td>
          <td>
            Path that identifies vSphere volume vmdk<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>fsType</b></td>
          <td>string</td>
          <td>
            Filesystem type to mount. Must be a filesystem type supported by the host operating system. Ex. &#34;ext4&#34;, &#34;xfs&#34;, &#34;ntfs&#34;. Implicitly inferred to be &#34;ext4&#34; if unspecified.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>storagePolicyID</b></td>
          <td>string</td>
          <td>
            Storage Policy Based Management (SPBM) profile ID associated with the StoragePolicyName.<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>storagePolicyName</b></td>
          <td>string</td>
          <td>
            Storage Policy Based Management (SPBM) profile name.<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>

### PlaybookExecution {#playbookexecution}
<sup><sup>[↩ Parent](#managementproject-flottaiov1alpha1 )</sup></sup>






PlaybookExecution is the Schema for the playbookexecutions API
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr>
        <td><b>apiVersion</b></td>
        <td>string</td>
        <td>management.project-flotta.io/v1alpha1</td>
        <td>true</td>
        </tr>
        <tr>
        <td><b>kind</b></td>
        <td>string</td>
        <td>PlaybookExecution</td>
        <td>true</td>
        </tr>
        <tr>
        <td><b><a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#objectmeta-v1-meta">metadata</a></b></td>
        <td>object</td>
        <td>Refer to the Kubernetes API documentation for the fields of the `metadata` field.</td>
        <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#playbookexecutionspec">spec</a></b></td>
          <td>object</td>
          <td>
            PlaybookExecutionSpec defines the desired state of PlaybookExecution<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#playbookexecutionstatus">status</a></b></td>
          <td>object</td>
          <td>
            PlaybookExecutionStatus defines the observed state of PlaybookExecution<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### PlaybookExecution.spec {#playbookexecutionspec}
<sup><sup>[↩ Parent](#playbookexecution)</sup></sup>



PlaybookExecutionSpec defines the desired state of PlaybookExecution
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>executionAttempt</b></td>
          <td>integer</td>
          <td>
            <br/>
            <br/>
              <i>Minimum</i>: 0<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#playbookexecutionspecplaybook">playbook</a></b></td>
          <td>object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### PlaybookExecution.spec.playbook {#playbookexecutionspecplaybook}
<sup><sup>[↩ Parent](#playbookexecutionspec)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>content</b></td>
          <td>string</td>
          <td>
            Playbook content<br/>
            <br/>
              <i>Format</i>: byte<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b><a href="#playbookexecutionspecplaybookansibleoptions">ansibleOptions</a></b></td>
          <td>object</td>
          <td>
            the ansible&#39;s playbook options for the playbook<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>executionStrategy</b></td>
          <td>string</td>
          <td>
            Execution strategy for the playbook<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#playbookexecutionspecplaybookprivilegeescalationoptions">privilegeEscalationOptions</a></b></td>
          <td>object</td>
          <td>
            the ansible&#39;s playbook privilege escalation options for the playbook<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b><a href="#playbookexecutionspecplaybookrequiredprivilegelevel">requiredPrivilegeLevel</a></b></td>
          <td>object</td>
          <td>
            The required privelege level necessary to execute the playbook<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>timeoutSeconds</b></td>
          <td>integer</td>
          <td>
            The connection timeout on ansible-playbook<br/>
            <br/>
              <i>Format</i>: int64<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### PlaybookExecution.spec.playbook.ansibleOptions {#playbookexecutionspecplaybookansibleoptions}
<sup><sup>[↩ Parent](#playbookexecutionspecplaybook)</sup></sup>



the ansible&#39;s playbook options for the playbook
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>check</b></td>
          <td>boolean</td>
          <td>
            don&#39;t make any changes; instead, try to predict some of the changes that may occur<br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### PlaybookExecution.spec.playbook.privilegeEscalationOptions {#playbookexecutionspecplaybookprivilegeescalationoptions}
<sup><sup>[↩ Parent](#playbookexecutionspecplaybook)</sup></sup>



the ansible&#39;s playbook privilege escalation options for the playbook
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>become</b></td>
          <td>boolean</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>becomeMethod</b></td>
          <td>enum</td>
          <td>
            <br/>
            <br/>
              <i>Enum</i>: sudo, su<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>becomeUser</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### PlaybookExecution.spec.playbook.requiredPrivilegeLevel {#playbookexecutionspecplaybookrequiredprivilegelevel}
<sup><sup>[↩ Parent](#playbookexecutionspecplaybook)</sup></sup>



The required privelege level necessary to execute the playbook
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>capAdd</b></td>
          <td>[]integer</td>
          <td>
            See https://man7.org/linux/man-pages/man7/capabilities.7.html<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>capDrop</b></td>
          <td>[]integer</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### PlaybookExecution.status {#playbookexecutionstatus}
<sup><sup>[↩ Parent](#playbookexecution)</sup></sup>



PlaybookExecutionStatus defines the observed state of PlaybookExecution
<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b><a href="#playbookexecutionstatusconditionsindex">conditions</a></b></td>
          <td>[]object</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>


##### PlaybookExecution.status.conditions[index] {#playbookexecutionstatusconditionsindex}
<sup><sup>[↩ Parent](#playbookexecutionstatus)</sup></sup>




<div class="table-responsive" >
  <table class="table table-sm">
      <thead>
          <tr>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Description</th>
              <th scope="col">Required</th>
          </tr>
      </thead>
      <tbody><tr scope="row">
          <td><b>status</b></td>
          <td>string</td>
          <td>
            Indicates whether that condition is applicable, with possible values &#34;True&#34;, &#34;False&#34;, or &#34;Unknown&#34; The absence of a condition should be interpreted the same as Unknown<br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>type</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>true</td>
        </tr><tr scope="row">
          <td><b>lastTransitionTime</b></td>
          <td>string</td>
          <td>
            <br/>
            <br/>
              <i>Format</i>: date-time<br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>message</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr><tr scope="row">
          <td><b>reason</b></td>
          <td>string</td>
          <td>
            <br/>
          </td>
          <td>false</td>
        </tr></tbody>
  </table>
</div>
