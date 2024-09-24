# JasperReports OpenShift Template

This repository contains an OpenShift template for deploying a JasperReports instance along with a MariaDB database. The template provides an easy and scalable setup for running JasperReports within an OpenShift environment.

## Template Components

The OpenShift template deploys the following components:

1. **JasperReports Deployment**:  
   Deploys the Bitnami JasperReports image with environment variables for database connectivity and application setup.
   
2. **MariaDB Deployment**:  
   Deploys a MariaDB database for use with JasperReports, including necessary credentials and database configuration.

3. **Services**:  
   - A service for JasperReports exposing port `8080`.
   - A service for MariaDB exposing port `3306`.

4. **Route**:  
   Exposes JasperReports via an OpenShift route on port `8080` to provide external access.

## Parameters

The template supports several parameters to customize the deployment:

| Parameter                         | Description                                  | Default Value               |
| ---------------------------------- | -------------------------------------------- | --------------------------- |
| `NAME`                             | Name for the frontend objects                | `jasper-reports`             |
| `JASPERREPORTS_DATABASE_USER`      | Database username for JasperReports          | `bn_jasperreports`           |
| `JASPERREPORTS_DATABASE_PASSWORD`  | Database password for JasperReports          | `bitnami`                    |
| `JASPERREPORTS_DATABASE_NAME`      | Database name for JasperReports              | `bitnami_jasperreports`      |
| `JASPERREPORTS_DATABASE_HOST`      | Hostname of the MariaDB service              | `mariadb.developer.svc`      |
| `DB_NAME`                          | Name for the MariaDB-related objects         | `mariadb`                    |

## How to Use

1. **Clone the Repository**:  
   Clone this repository to your local machine:

   ```bash
   git clone https://github.com/yourusername/jasper-reports-openshift-template.git

2. **Create the Template in OpenShift**:
   Create the template in your OpenShift project:

   ```bash
   oc create -f jasper-reports-template.yaml

3. **Process and Apply the Template**:
   Process and deploy the template with the necessary parameters:

   ```bash
    oc process jasper-reports \
      -p NAME=jasper-reports \
      -p JASPERREPORTS_DATABASE_USER=bn_jasperreports \
      -p JASPERREPORTS_DATABASE_PASSWORD=bitnami \
      -p JASPERREPORTS_DATABASE_NAME=bitnami_jasperreports \
      -p JASPERREPORTS_DATABASE_HOST=mariadb.developer.svc \
      -p DB_NAME=mariadb | oc apply -f -
