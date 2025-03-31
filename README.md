# The Transportation Data Exchange Initiative (TDEI) Deployment Project

Cities, organizations, and individuals currently lack detailed, accurate, and standardized data on the locations of footpaths, cycle paths, sidewalks, and crossings. Moreover, there is inconsistent information about the attributes of these pathways that affect walking, rolling, and non-motorized travel, as well as a limited understanding of how these paths are connected or disconnected.

The OpenSidewalks project aims to address this data deficiency by proposing a) **a robust data schema** (OpenSideWalks or OSW) and b) **a comprehensive data tools ecosystem** that support collection and maintenance of sidewalk data (which we call the TDEI). 

These resources are designed to give planners, policy makers, and community advocates the data they need to improve pedestrian infrastructure, particularly in historically underserved areas.

Current funding is provided by the [USDOT/JPO ITS4US](https://www.its.dot.gov/its4us/index.htm) program under the [University of Washington’s Transportation Data Exchange Initiative (TDEI)](https://transitequity.cs.washington.edu/) deployment project.

OpenSidewalks is led by the [Taskar Center for Accessible Technology (TCAT)](http://tcat.cs.washington.edu/) housed by the Paul G. Allen School for Computer Science and Engineering at the University of Washington. 

The University of Washington’s [eScience Institute](http://escience.washington.edu/) provided an opportunity for the OpenSidewalks project to develop as a part of their [Data Science for Social Good](https://uwescience.github.io/DSSG2016/) program that took place in the summer of 2016.

## A. The OpenSideWalks (OSW) Data Schema

A data specification to represent detailed, accurate, and standardized data on the locations of footpaths, cycle paths, sidewalks, and crossings. The specification includes attributes of these pathways that affect walking, rolling, and non-motorized travel, as well as a limited understanding of how these paths are connected or disconnected.

See https://github.com/OpenSidewalks/OpenSidewalks-Schema for more detail. 

## B. The TDEI System

![Screenshot of the TDEI System](/TDEI.png)  
_Figure 1: overview of the system_

Below are the repositories that make up the complete TDEI system:

* **Workspaces**. The monorepo for the entire **Workspaces** system including its frontend, backend API(s) and a dispatching reverse proxy, the **Rapid** editor, the **GTFS Pathways Editor**, the **OSW Tasking Manager** and some debug tooling. 
  - https://github.com/TaskarCenterAtUW/workspaces-stack
  - See https://github.com/TaskarCenterAtUW/workspaces-stack/blob/main/README.md for more information on the contents of this repository. 

* **GoInfoGame**. An iOS and Android version of GoInfoGame, a mobile app to contribute to a Workspace. 
  - iOS: https://github.com/TaskarCenterAtUW/GoInfoGame-iOS
  - Android: https://github.com/TaskarCenterAtUW/GoInfoGame-Android 

* **Walkshed Analysis**. A tool to quantify and analyze access to/from a point with detailed statistics on accessible community resources, accessibility barriers and other measures. 
  - https://github.com/AccessMap/accessmap-walksheds 

* **AccessMap Multimodal**. A trip planner that allows users to express sidewalk preferences and receive suitable paths via mapped infrastructure. 
  - https://github.com/AccessMap/accessmap 

* **Audiom**. A third-party developed application integrated with TDEI as part of the USDOT funded work.
  - https://www.audiom.net/

* TDEI Core and TDEI Query. 
  - TDEI Core and Query frontend. https://github.com/TaskarCenterAtUW/TDEI-user-management-front-end
  - Backend APIs:
    - TDEI user management APIs. The frontend requires this component to be running. https://github.com/TaskarCenterAtUW/TDEI-user-management-ts
    - TDEI data management APIs. The frontend requires this component to be running. https://github.com/TaskarCenterAtUW/TDEI-gateway 
    - Query backend APIs. The frontend requires this component to be running. https://github.com/TaskarCenterAtUW/TDEI-osw-datasvc-ts
  - Queue Jobs. The Query backend uses these components to pass messages over an Azure message queue and/or in response to messages on the queue as jobs. Some job runners are composed of both a library (*-lib-*) that contains reusable functions of that library, as well as a job runner which pulls messages from the queue, uses the library’s logic, and pushes the results back to the queue.  
    - Queue message data transfer objects used by all queue-related components of TDEI. 
      - https://github.com/TaskarCenterAtUW/TDEI-event-messages 
    - GTFS Pathways validator job. Passes input to Mobility Data validator. 
      - https://github.com/TaskarCenterAtUW/TDEI-python-gtfs-pathways-validation
    - GTFS Flex validator job. Passes input to Mobility Data validator.
      - https://github.com/TaskarCenterAtUW/TDEI-python-gtfs-flex-validation
    - Mobility Data GTFS Validator job. Submits dataset to the Mobility Data Canonical validator.
      - https://github.com/TaskarCenterAtUW/TDEI-mobilitydata-canonical-validator
    - Quality metric job
      - https://github.com/TaskarCenterAtUW/TDEI-python-osw-quality-metric
    - OSW Validator job:
      - https://github.com/TaskarCenterAtUW/TDEI-python-osw-validation
      - https://github.com/TaskarCenterAtUW/TDEI-python-lib-osw-validation
    - Extract-Transform-Load (ETL) job: 
      - https://github.com/TaskarCenterAtUW/TDEI-extract-load-service
    - Confidence score metric–stub-only right now:
      - https://github.com/TaskarCenterAtUW/TDEI-python-osw-confidence-metric
      - https://github.com/TaskarCenterAtUW/TDEI-python-lib-confidence-metric
    - DEM inclination tagging job:
      - https://github.com/TaskarCenterAtUW/TDEI-python-osw-incline
      - https://github.com/TaskarCenterAtUW/TDEI-python-lib-osw-inclination
    - OSM to OSW and vice-versa conversion job:
      - https://github.com/TaskarCenterAtUW/TDEI-python-osw-formatter
      - https://github.com/TaskarCenterAtUW/TDEI-python-lib-osw-formatter 

* **System Documentation and Developer Tools**. Supporting tooling and documentation that may be useful for setup and maintenance. 
  - https://github.com/TaskarCenterAtUW/TDEI-tools
  - https://github.com/TaskarCenterAtUW/TDEI-quality-dashboard 
