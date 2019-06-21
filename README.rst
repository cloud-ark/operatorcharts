====================
Operator Charts
====================

Repository of Operator Helm charts curated for discoverability and interoperability.

Each Helm chart contains CRD YAML annotated with Platform-as-Code annotations (https://github.com/cloud-ark/kubeplus#platform-as-code-annotations)


Available Operators
--------------------

1. moodle-operator-chart (CloudARK)

    Moodle Operator supports creating multiple Moodle instances, plugin installation, DNS, SSL
    
    https://github.com/cloud-ark/kubeplus-operators/tree/master/moodle

   - Version: 0.4.7 -> Contains SSL support for Moodle Instances

   - Version: 0.4.6 -> Domain Name support

   - Versoin: 0.4.4 -> Works with MySQL Custom Resource Instances

   - Versions < 0.4.4 -> Initial versions (legacy)

2. mysql-operator (PressLabs)

    MySQL Operator supports creating, backing up, restoring MySQL clusters.

    https://github.com/presslabs/mysql-operator

   - Version: 0.2.5-1 -> PaC annotations

   - Versions < 0.2.5-1 -> Legacy version

3. mysql-operator-chart (Oracle)

   https://github.com/oracle/mysql-operator

4. postgres-crd-v2 (CloudARK)

   https://github.com/cloud-ark/kubeplus/tree/master/postgres-crd-v2

   - Version: 0.0.3 -> PaC annotations

   - Versions < 0.0.3 -> Legacy version

5. stash-operator (Appscode Stash)

   https://github.com/stashed/stash

   - Version: 0.8.4 -> PaC annotations

   - Versions < 0.8.4 -> Legacy version


Best practice Operator Development Guidelines
----------------------------------------------

Checkout following Operator developing guidelines when developing your Operator

https://github.com/cloud-ark/kubeplus/blob/master/Guidelines.md



Include you Operator in this repository
----------------------------------------

1. Install Helm

2. Create Helm chart for your Operator

   This involves three steps:

   a] Create the helm chart directory and populate it with helm related artifacts

      - Create a directory inside your operator source and name it: <name>-operator-chart

      - Inside <name>-operator-chart directory include Chart.yaml, Values.yaml and template folder

      - Inside template folder define all the YAML files required for deploying your Chart

      - Check the following as an example of helm chart directory:
	https://github.com/cloud-ark/kubeplus-operators/tree/master/moodle/moodle-operator-chart

   b] Annotate your CRD definition with Platform-as-Code annotations. Check https://github.com/cloud-ark/kubeplus
      for what PaC annotations are available for you to use.

      - Create the required ConfigMaps that go along with your PaC annotations.

      - Check Moodle CRD definition for example of PaC annotations:

https://github.com/cloud-ark/kubeplus-operators/blob/master/moodle/moodle-operator-chart/templates/deployment.yaml#L17


   c] Create the helm chart

      - From the parent directory of the helm chart directory, execute following command:

        - helm package ./<name>-operator-chart

        - This should create <name>-operator-chart.tgz file


3. Fork this repository

4. Add the helm chart tgz file to the repository

5. Update index.yaml to include information about your chart's tgz file

   - helm repo index --merge index.yaml --url https://github.com/cloud-ark/operatorcharts/blob/master ./

6. Send a Pull Request to get your Operator chart included
   in this repository


Once your Operator is included we will provide you feedback on how 
your Operator compares with above best practice Guidelines.

