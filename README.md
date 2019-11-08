Red Hat Process Automation Manager - DMN PMML Demo
=============================

This demo shows a Credit Card Dispute demo, in which we demonstrate the combination of declarative decisions defined DMN (Decision Model & Notation) with predictive decisions defined in PMML (Predictive Model Markup Language). Monitoring of decision metrics is done via Prometheus and visualized with Grafana.

Software
--------
This demo runs on *OpenShift 4.x*, and therefore requires an available OpenShift 4.x runtime. This can be a OpenShift Container Platform 4.z instance, a Code Ready Containers instance, etc. The only requirement is that there are enough resource available to run the 4 OpenShift pods that this demo consists off.

Install on OpenShift
-------------------------------
This demo can be installed on Red Hat OpenShift in various ways. We'll explain the different options provided.

All installation options require an `oc` client installation that is connected to a running OpenShift 4 instance. More information on OpenShift and how to setup a local OpenShift development environment using CodeReady Containers can be found [here](https://github.com/code-ready/crc).

---
**NOTE**

The Red Hat Process Automation Manager 7 - Business Central image requires a [Persistent Volume](https://docs.openshift.com/container-platform/3.7/architecture/additional_concepts/storage.html) which has both `ReadWriteOnce` (RWO) *and* `ReadWriteMany` (RWX) Access Types. If no PVs matching this description are available, deployment of that image will fail until a PV of that type is available.

---

### Automated installation
This installation option will install the demo in OpenShift using a single script, after which the demo project needs to be manually imported.

1. [Download and unzip](https://github.com/jbossdemocentral/rhpam7-dmn-pmml-demo/archive/master.zip) or [clone this repo](https://github.com/jbossdemocentral/rhpam7-dmn-pmml-demo.git).

2. Run the `init-openshift.sh` (Linux/macOS) or `init-openshift.ps1` (Windows) file. This will create a new project and application in OpenShift 4 and deploy the demo.

3. Login to your OpenShift console. For a local [CodeReady Containers](https://github.com/code-ready/crc) OpenShift 4 installation, the console can be accessed by executing `crc console` from a terminal.

4. A full walkthrough script of the demo can be found [here](https://docs.google.com/document/d/1TVrTkQRZoQAQoOGDzKpWOI68x2Mre_dXifTWf9lzKsE/)

### Scripted installation
This installation option will install the demo in OpenShift using the provided `provision.sh` (Linux/macOS) or `provision.ps1` (Windows) script, which gives the user a bit more control how to provision to OpenShift.

1. [Download and unzip.](https://github.com/jbossdemocentral/rhpam7-dmn-pmml-demo/archive/master.zip) or [clone this repo](https://github.com/jbossdemocentral/rhpam7-dmn-pmml-demo.git).

2. In the demo directory, go to `./support/openshift`. In that directory you will find the `provision.sh` (Linux/macOS) and `provision.ps1` (Windows) script.

3. Run `./provision.sh -h` (Linux/macOS) or `./provision.ps1 -h` (Windows) to inspect the installation options.

4. To provision the demo, with the OpenShift ImageStreams in the project's namespace, run `./provision.sh setup rhpam7-dmn-pmml --with-imagestreams` (Linux/macOS) or `./provision.sh -command setup -demo rhpam7-dmn-pmml -with-imagestreams` (Windows)

    ---
    **NOTE**

    The `with-imagestreams` parameter installs the Process Automation Manager 7 image streams and templates into the project namespace instead of the `openshift` namespace (for which you need admin rights). If you already have the required image-streams and templates installed in your OpenShift environment in the `openshift` namespace, you can omit the `with-imagestreams` from the setup command.

    ---

5. After provisioning, follow the instructions from above "Automated installation", starting at step 3.

6. To delete an already provisioned demo, run `./provision.sh delete rhpam7-dmn-pmml` (Linux/macOS) or `./provision.ps1 -command delete -demo rhpam7-dmm-pmml` (Windows).

Notes
-----
The following functionality is covered:

- _Case Management_: The Credit Card Dispute process is defined as a dynamic case.

- _DMN_: Some of the decisions in the workflow are defined and evaluated in DMN (Decision Model & Notation).

- _Artificial Intelligence and Machine Learning_: parts of the decision logic are implemented with _Machine Learned_ models, integrated with DMN using PMML (Predictive Model Markup Language).

- _AppBuilder_: the client and admin application are build with and running on Entando AppBuilder.

- _Prometheus_: DMN decision metrics are exposed by the Execution Server/KIE-Server to Prometheus.

- _Grafana_: Grafana dashboards are used to visualize the DMN decision metrics monitored by Prometheus.


Supporting Articles
-------------------


Released versions
-----------------
See the tagged releases for the following versions of the product:
