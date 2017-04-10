---
title: "Integration Services (SSIS) Scale Out | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dcfbd1c5-c001-4fb7-b9ae-916e49ab6a96
caps.latest.revision: 6
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 6
---
# Integration Services (SSIS) Scale Out
[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Scale Out constitue un moyen très performant d’exécuter des packages en distribuant les exécutions sur plusieurs ordinateurs. Il vous permet d’envoyer une demande de plusieurs exécutions de packages dans SQL Server Management Studio. Les packages sont alors exécutés en parallèle, en mode « Scale Out ».  


## <a name="ssis-scale-out-master-and-scale-out-worker"></a>SSIS Scale Out Master et Scale Out Worker
[!INCLUDE[ssIS_md](../includes/ssis-md.md)] Scale Out se compose d’un [!INCLUDE[ssIS_md](../includes/ssis-md.md)] Scale Out Master et de plusieurs [!INCLUDE[ssIS_md](../includes/ssis-md.md)] Scale Out Workers. Le Scale Out Master est responsable de la gestion de Scale Out et reçoit les demandes d’exécution de package des utilisateurs. Les Scale Out Workers extraient les tâches d’exécution du Scale Out Master et effectuent le travail d’exécution de package. Pour plus d’informations, consultez [Scale Out Master](../integration-services/integration-services-ssis-scale-out-master.md), [Scale Out Worker](../integration-services/integration-services-ssis-scale-out-worker.md).


## <a name="how-to-set-up-scale-out"></a>Guide pratique pour configurer Scale Out
[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Scale Out peut s’exécuter sur un ordinateur, où un Scale Out Master et un Scale Out Worker sont configurés côte à côte. Scale Out peut également s’exécuter sur plusieurs ordinateurs, auquel cas chaque Scale Out Worker est sur un ordinateur différent.
- [Procédure pas à pas : Configurer Integration Services Scale Out](../integration-services/walkthrough-set-up-integration-services-scale-out.md)


## <a name="run-packages-in-scale-out"></a>Exécuter des packages dans Scale Out
Scale Out prend en charge l’exécution en parallèle de plusieurs packages dans le catalogue SSISDB. Pour plus d’informations, consultez [Exécuter des packages dans Scale Out](../integration-services/run-packages-in-integration-services-ssis-scale-out.md).

