# New England Research Cloud (NERC) Service Description

## **I. Service Overview**

### **Description**

The New England Research Cloud (NERC) provides a secure on-premise
private cloud solution that is integrated with the [Massachusetts Green
High Performance Computing Center's
(MGHPCC)](https://www.mghpcc.org/) networking facilities
and the Northeast Storage Exchange's (NESE) storage services. Using
self-service portals or public interfaces, users can request cloud
resources for testing, development, and production purposes. NERC
provides the following types of services: Virtual Machine (VM)
orchestration and storage services i.e. Block Storage (Volume) and
Object Storage (Swift) through Red Hat's OpenStack platform, Container
orchestration services through Red Hat's OpenShift platform, and a data
science platform through Red Hat's OpenShift AI (RHOAI). These services
enable users to use only what they need when they need it, e.g., rapidly
scaling from a tiny fraction of a single CPU with a small amount of
memory to (depending on quota and availability) hundreds of computers
with dedicated GPUs.

![NERC Overview](https://github.com/nerc-project/nerc-service-description/blob/main/images/NERC-overview.png)

### **Key Features, Definitions, and Benefits**

#### Roles & Responsibilities

**NERC/MOC-A Operations:** A working group composed of key NERC and MOC
Alliance stakeholders that make strategic decisions on daily operations,
directing resources to MOC-A projects, and development activities that
will support NERC production services.

**NERC Engineering:** A systems engineering group composed of
individuals from Boston University and Harvard University manages NERC
infrastructure and services. Additional resources from Red Hat and the
MOC Alliance (MOC-A) also assist with Systems Engineering efforts
through the development and integration of new NERC production services.

**NERC Facilitation:** This is the group of facilitators that develop
customer facing documentation, assist with onboarding new customers,
triage support tickets, and train facilitators from other institutions
to better support their researchers.

**NERC Institutional Customer:** NERC is a shared service offered to (1)
MGHPCC Consortium Member Institutions and (2) Institutions External to
the MGHPCC Consortium.

-   ***MGHPCC Consortium Member Institutions***: NERC shared services
    are offered through the MGHPCC and operated by the Trustees of
    Boston University acting on behalf of the Mass Open Cloud Alliance
    (MOC-A) and the New England Research Cloud (NERC). The MGHPCC will
    enter into a Memorandum of Understanding (MOU) with each
    institutional customer that consumes NERC services.

-   ***Institutions External to the MGHPCC Consortium***: NERC shared
    services are offered and operated by the Trustees of Boston
    University acting on behalf of the Mass Open Cloud Alliance (MOC-A)
    and the New England Research Cloud (NERC). The Trustees of Boston
    University will enter into a Memorandum of Understanding (MOU) with
    each institutional customer that consumes NERC services.

The MOU is intended to ensure the institution maintains access to
valuable and relevant cloud services provided by the New England
Research Cloud (NERC) and ensure NERC remains sustainable over time. For
cost recovery purposes, institutional customers may elect to receive one
invoice for the usage of NERC services by its PIs and cost recovery
internally. PIs from institutions without MOUs can still utilize NERC
services with the understanding that they are directly accountable for
managing their usage and ensuring all service charges are paid promptly.

**NERC Principal Investigators (PIs):** PIs have appointments at their
institution that allow them to sponsor end-user accounts. In ColdFront,
PIs can build and manage projects and add resources and users. All
utilization of projects and associated costs are aggregated to the PI.
PIs are ultimately responsible for their end-users and the security of
the systems and applications that are deployed as part of their
project(s).

**NERC Project Managers:** A PI may designate one or more project
managers, who have the ability to build and manage projects and add
resources and End Users on behalf of the PI.

**NERC End Users:** Researchers and students who access data storage,
networking, and cloud computing services provided by NERC. End users
obtain access to NERC offerings by having a PI add them to projects in
ColdFront. End users may stand up services and manage VMs, containers,
volume, and object storage. However, the PI is ultimately responsible
for their use and security.

**Principal Investigator and End User Responsibilities:** NERC service
requestors must ensure the following actions are performed:

-   Comply with your Institution's **Security** and **Privacy**
    policies. Without prior notice, NERC reserves the right to shut down
    any VM or container that is causing internal or external problems or
    violating these policies. Examples of institutional policies can be
    found
    [here](https://nerc.mghpcc.org/privacy-and-security/).
    PI's are responsible for their (and, in turn, their project users)
    use of NERC services, which include:

    *   Following best practices for security on NERC services.

    *   Complying with security policies regarding VMs and containers.
        NERC admins are not responsible for maintaining or deploying VMs
        or containers created by PIs for their projects.

    *   Adhering to institutional restrictions and compliance policies
        around the data they upload and provide access to/from NERC.

-   [Backups and/or
    snapshots](https://nerc-project.github.io/nerc-docs/openstack/backup/backup-with-snapshots/)
    are the responsibility of End Users for volumes/data,
    configurations, objects, and their state, which are useful in the
    case when users accidentally delete/lose their data. **NERC admins
    cannot recover lost data.** In addition, while NERC
    stores data with high redundancy to deal with computer or disk
    failures, PIs should ensure they have off-site backups for disaster
    recovery, e.g., to deal with natural disasters that impact the
    MGHPCC data center.

-   Provide timely responses to e-mails from the NERC administrators and
    cloud facilitators regarding service issues and requests of
    information.

-   Delete all resources (including project accounts, allocations,
    storage, VMs, and pods) that are no longer needed or used.

### User & Resource Management

**NERC Project, Account & Allocation Management:** NERC leverages
federated access (via the [MGHPCC
RegApp](https://nerc-project.github.io/nerc-docs/get-started/create-a-user-portal-account/)
service), enabling PIs and End Users to access services using their
institutional credentials. Once federated access is established, PIs and
Project Manager, utilize the
[ColdFront](https://nerc-project.github.io/nerc-docs/get-started/get-an-allocation/)
service to establish research and course projects which may consist of
multiple End Users of their choosing. ColdFront is also utilized to
request, track, and manage resource allocation quotas for the various
NERC services.

**Resource Allocation Quotas:** NERC services utilize [resource
allocation](https://nerc-project.github.io/nerc-docs/get-started/get-an-allocation/)
quotas, which are managed through the ColdFront interface to allow users
to request variable units of resources, providing them the flexibility
to increase and decrease their use of a service as long as their demand
is less than their current quota. As PIs are responsible for all charges
incurred by their users, resource quotas provide a method to avoid
excessive service charges due to user error.

## **NERC Service Offerings**

### NERC OpenStack

NERC leverages the open-source OpenStack platform provided and supported
by Red Hat for the deployment of a secure on-premise private cloud
infrastructure including Virtual Machines (VMs), images, volumes, and
object storage. This enables end-users to virtualize the underlying
pools of resources and access storage, network, and compute servers on
demand. Users can secure access and manage their infrastructures through
a web-based Horizon dashboard or through command line tools or through a
restful API that is controlled by federated identity access management
by MGHPCC's RegApp service.

***Note:** The core OpenStack service is protected against disaster
recovery; however, NERC does not offer automatic backups of users
virtual machines or data. Please refer to the [backup with
snapshots](https://nerc-project.github.io/nerc-docs/openstack/backup/backup-with-snapshots/)
page options on how to configure backups and rollbacks of VMs or volumes
including data.*

#### NERC OpenStack Specific Definitions

**Virtual Machine (VM):** A virtual machine emulates a computer system
at the device level.

**Glance Image**: A virtual collection of a kernel, operating system,
and configuration. NERC provides a set of default images, which can be
found
[here](https://nerc-project.github.io/nerc-docs/openstack/create-and-connect-to-the-VM/images/).
Users can also upload their own custom images and launch VMs based on
them, as demonstrated in [this
documentation](https://nerc-project.github.io/nerc-docs/openstack/advanced-openstack-topics/setting-up-your-own-images/how-to-build-windows-image/).

**Flavors:** Flavors are virtual hardware templates that define the
compute, memory, and storage capacity of computing VMs(i.e., the defined
size or hardware configuration for a server that can be launched). A
full list of flavors can be found
[here](https://nerc-project.github.io/nerc-docs/openstack/create-and-connect-to-the-VM/flavors/)
and are closely aligned with the consumables and related costs defined
below.

**Project:** Projects are isolated resource containers that form the
principal organizational structure within the NERC's compute service.
They typically consist of networks, volumes, VMs, images, key pairs, and
users, etc.

[**Horizon Dashboard:** The OpenStack dashboard, also referred to as
[Horizon](https://nerc-project.github.io/nerc-docs/openstack/logging-in/access-the-openstack-dashboard/),
is a web-based graphical interface accessible to authorized users who
log in through their institution accounts using federated login. In the
OpenStack Horizon Dashboard, roles serve as a mechanism defining a
user's rights or privileges within specific projects. Upon logging in,
users are presented with a unified view of all projects where they have
assigned roles. The actions users can take, and the information they can
view within each project are determined by their respective roles.

**Storage Snapshot**: Point-in-time copy of a virtual machine's root
and/or data disk.

### NERC OpenShift

NERC leverages the open-source OpenShift Container Platform provided and
supported by Red Hat, a cloud-based open-sourced Kubernetes (K8s)
container orchestration platform that provides an isolated, multi-tenant
container environment for application development and deployment. This
is optimized for continuous containerized application development and
multi-tenant deployment using a [web-based
console](https://nerc-project.github.io/nerc-docs/openshift/logging-in/web-console-overview/)
which allows you and your team to focus on solving your research
problems and not infrastructure management.

#### NERC OpenShift Specific Definitions

**Pod:** In OpenShift, pods represent the smallest deployable units,
defining, deploying, and managing related resources that share one or
more containers, facilitating resource sharing.

**Ephemeral Storage:**

Ephemeral Storage refers to temporary and non-persistent storage
attached to pods during their lifecycle, which is automatically deleted
when the pod terminates.

**Persistent Storage:**

Persistent Volumes (PV): PVs are a cluster-wide resource that
represents physical storage resources available to containers for
dynamically binding to a user or application requested storage
requirements in terms of Persistent Volume Claims (PVC). PVs decouple
storage from individual pods, allowing data to persist beyond the
lifecycle of a pod or a container.

### NERC Red Hat OpenShift AI (RHOAI) platform

[NERC's RHOAI
platform](https://nerc-project.github.io/nerc-docs/openshift-ai/get-started/rhoai-overview/)
provided and supported by Red Hat provides a fully supported sandbox
environment for data scientists/researchers to develop, train and test
Artificial intelligence (AI), Machine Learning (ML), and Deep Learning
(DL) models and deploy them for use in intelligent applications. This
service enables JupyterLab to allow users to develop and design AI/ML
workflows and implement analytic techniques in Jupyter Notebooks with
access to core AI/ML libraries and frameworks, including TensorFlow,
PyTorch, CUDA, etc. With the ability to connect to GPUs on-demand, model
training, and testing can be accelerated, reducing the time needed to
develop models and gain insights.

### NERC Storage Service

The NERC storage service leverages Ceph, a distributed and
high-performance storage solution supported by the [Northeast Storage
Exchange (NESE)](https://nese.mghpcc.org/), to offer block
and object storage for OpenStack and persistent volumes for OpenShift.
The storage allocation for OpenStack is based on the requested Volume
Storage (GiB) and Object Storage (GiB) quota allocated through NERC's
ColdFront. Whereas the OpenShift project is governed by Ephemeral
Storage (GiB) and Volume Storage (GiB) quota. Additionally, the number
of volumes allowed in a project is tracked through "Volumes" and "PVC"
respectively. Any necessary adjustments to the storage allocation can be
easily made later to accommodate the project's specific needs.

### Tracking Consumption of NERC Services

NERC services utilize underlying hardware infrastructure to support
their use. Pre-defined consumables based on Service Units (SU) track the
use of these hardware resources and are the basis for utilization
reports and cost recovery. Over time additional types (or tiers) of
hardware will be introduced and deprecated. Further details on how the
costs/hr for each consumable are arrived at can be found in the
financial model section below. Currently, there are three types of
service units (SUs) that can be consumed: Standard Compute, GPU (model
specific), and Storage. The definitions and associated costs with each
of these types of service units can be found on the [following
page](https://nerc-project.github.io/nerc-docs/get-started/cost-billing/how-pricing-works/).

## **II. Service Operations**

### **Service Team**

| NAME OF FUNCTIONAL TEAM               | NAME OF INDIVIDUAL/GROUP                            | AREA OF EXPERTISE                                                                                                                             |
| ------------------------------------- | --------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Ticketing System                      | [help@nerc.mghpcc.org](mailto:help@nerc.mghpcc.org) | Intake of incidents relating to service; troubleshooting according to standard; Troubleshooting Guide knowledge; escalation to Service Owners |
| Engineering, Operations, Facilitation | Harvard University & Boston University              | Multi-storage platforms and all-around systems administration                                                                                 |
| Service Delivery Manager              | Scott Yockel & Wayne Gilmore                        | Accountable for service operations. Responsible for strategy and development of service.                                                      |

### **Service Objectives**

NERC availability and uptime is provided as best effort with staff that
do not have rotating 24/7/365 shifts. NERC Administrators will aim to
acknowledge service issue(s) within 24 hours and resolve issue(s) within
2 business days. NERC does not currently provide disaster recovery for
its services.

### **Service Requests**

Requests for services or technical support and issues with service
should be sent via email to
[help@nerc.mghpcc.org](mailto:help@nerc.mghpcc.org) or, by
submitting a new ticket at the [NERC's Support Ticketing
System](https://mghpcc.supportsystem.com/open.php)
(osTicket).

### **Maintenance**

-   Planned maintenance is generally performed during the work week
    (Monday-Friday), with an email notification sent at least a week
    prior with details.

-   Annual facilities maintenance at MGHPCC requires a multi-day outage
    with notification sent two months in advance. This typically occurs
    in the May/June time frame. A notice will be sent to all NERC users
    regarding the exact time period of the outage, including the
    estimated time for restoration of services.

-   Unplanned maintenance can occur at any time, depending on the
    severity of the need. Notification will be emailed, and the status
    page will be updated.

### **Incidents**

Customers will be sent email notifications about major NERC resource
outages and scheduled downtimes for upgrades and maintenance. NERC's
system status can be found at
[https://nerc.instatus.com/](https://nerc.instatus.com/),
and end-users can subscribe to NERC's status updates
[here](https://nerc.instatus.com/subscribe/email). Also,
end-users can report incidents/problems by sending an email to
[help@nerc.mghpcc.org](mailto:help@nerc.mghpcc.org).

### **Knowledge**

Documentation for institutional customers, investigators, and end-users
is available on the [NERC
website](https://nerc.mghpcc.org/). In-depth documentation
is available from the NERC Github site, which is accessible from the
[NERC User Guide web
page](https://nerc.mghpcc.org/user-guides/).

## **III. Financial Model**

The cost recovery formula for each service is as follows:

![Financial Model](https://github.com/nerc-project/nerc-service-description/blob/main/images/financial-model.png)

-   **Equipment** is the cost of the computing equipment amortized over
    5 years (e.g., servers, network switches, cables, etc.) that creates
    the service provided by the defined offering. *Note: Equipment
    purchased by the Customer is not included in the cost of the tier of
    service and will need to be factored in separately.*

-   **Facilities** include space, power, and cooling costs associated
    with the service at a rack level.

-   **Personnel** includes the cost of NERC Administrators (4 FTEs) and
    is split among the offerings.

-   **Total annual service units (SUs)** are reduced to 24 hr x 360 days
    per year, as it deducts all planned maintenance events.

### **MGHPCC Member Institutions**

MGHPCC member organizations will be provided access to a full suite of
NERC services. Each institution must provide a point of contact as the
sponsor who is responsible for approving PI projects and agrees to
handle financial matters related to the use of NERC services for their
institution. While NERC services are available via self-service
provisioning, the institution must provide basic onboarding support to
researchers for creating accounts and requesting resources for projects
through the portal. Only limited technical support is provided to
institutions. We are happy to partner with facilitator(s) from these
institutions and train them. All billing will be handled by MGHPCC and
will be included as a line item on monthly invoices at an institutional
level or directly billed to the PI, depending on the institution's
preference. NERC will provide monthly reporting on usage by PI to
institutions.

### **Institutions External to the MGHPCC**

External organizations will be provided access to a full suite of NERC
services. Each institution must provide a point of contact as the
sponsor who is responsible for approving PI projects and agrees to
handle financial matters related to the use of NERC services for their
institution. While NERC services are available via self-service
provisioning, the institution must provide basic onboarding support to
researchers for creating accounts and requesting resources for projects
through the portal. Only limited technical support is provided to
external institutions. We are happy to partner with facilitator(s) from
these institutions and train them. All billing will be handled by the
Trustees of Boston University and monthly invoices will be sent at an
institutional level or directly billed to the PI, depending on the
institution's preference. NERC will provide monthly reporting on usage
by PI to institutions.

## **Version History**

| **VERSION** | **DATE**   | **AUTHOR**                      | **SUMMARY OF CHANGES**                                               |
| ----------- | ---------- | ------------------------------- | -------------------------------------------------------------------- |
| **V 1.0**   | 06/13/2022 | Krista Valladares               | N/A                                                                  |
| **V 1.1**   | 06/15/2022 | Scott Yockel                    | Updated GPU tier flavors and costs                                   |
| **V 1.2**   | 10/29/2022 | Krista Valladares               | Changed document title from Service Agreement to Service Offering    |
| **V 1.3**   | 03/31/2023 | Scott Yockel                    | Updated pricing for FY24                                             |
| **V 1.4**   | 07/21/2023 | Wayne Gilmore / Milson Munakami | Updates in pricing and content for referencing by institutional MOUs |
| **V 1.5**   | 08/13/2024 | Wayne Gilmore                   | Renamed RHODS and aligned with MOU language                          |
