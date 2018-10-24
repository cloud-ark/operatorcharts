====================
Operator Charts
====================

Repository of Helm charts for Operators. 




Best practice Operator Development Guidelines
----------------------------------------------

Checkout `Operator Guidelines`__ when developing your Operator

.. _guidelines: https://github.com/cloud-ark/kubeplus/blob/master/Guidelines.md

__ guidelines_



Include you Operator in this repository
----------------------------------------

0. Install Helm


1. Create Helm chart for your Operator

   This involves three steps:

   a] Creating the helm chart directory and populating it with helm related artifacts

      - Check the following as an example of helm chart directory:
        
        https://github.com/cloud-ark/kubeplus/tree/master/operator-manager/operator-manager-chart

      - Create a directory inside your operator source and name it: <name>-operator-chart

      - Inside <name>-operator-chart directory include Chart.yaml, Values.yaml and template folder

      - Inside template folder define all the YAML files required for deploying your Chart

   b] Generating OpenAPI Spec for the custom resources managed by your Operator

      - Go inside your helm chart directory and then follow the steps from:

        https://github.com/cloud-ark/kubeplus/tree/master/openapi-spec-generator
         

   c] Creating the helm chart

      - From the parent directory of the helm chart directory, execute following command:

        - helm package ./<name>-operator-chart

        - This should create <name>-operator-chart.tgz file


2. Fork this repository

3. Add the helm chart tgz file to the repository

4. Update index.yaml to include information about your chart's tgz file

   - ./helm repo index --merge index.yaml --url http:///charts/ ./

5. Send a Pull Request to get your Operator chart included
   in this repository


Once your Operator is included we will provide you feedback on how 
your Operator compares with above best practice Guidelines.

