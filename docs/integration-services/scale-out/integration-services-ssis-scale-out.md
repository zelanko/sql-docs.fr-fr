---
title: SQL Server Integration Services (SSIS) Scale Out | Microsoft Docs
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dcfbd1c5-c001-4fb7-b9ae-916e49ab6a96
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 0277d312ce4dab14e7ba64529e3eb2251a0d2d02
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="integration-services-ssis-scale-out"></a>Integration Services (SSIS) Scale Out
[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out constitue un moyen très performant d’exécuter des packages en distribuant les exécutions sur plusieurs ordinateurs. Vous pouvez envoyer une demande de plusieurs exécutions de packages dans SQL Server Management Studio. Les packages sont alors exécutés en parallèle, en mode « Scale Out ».  

[!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out se compose d’un [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out Master et d’un ou plusieurs [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out Workers. Le Scale Out Master est responsable de la gestion de Scale Out et reçoit les demandes d’exécution de package des utilisateurs. Les Scale Out Workers extraient les tâches d’exécution du Scale Out Master et effectuent le travail d’exécution de package. Pour plus d’informations, consultez [Scale Out Master](integration-services-ssis-scale-out-master.md), [Scale Out Worker](integration-services-ssis-scale-out-worker.md).

[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out peut être configuré sur une machine, où un Scale Out Master et un Scale Out Worker sont configurés côte à côte. Scale Out peut également s’exécuter sur plusieurs ordinateurs, auquel cas chaque Scale Out Worker est sur un ordinateur différent.
- [Procédure pas à pas : Configurer Integration Services Scale Out](walkthrough-set-up-integration-services-scale-out.md)

Scale Out prend en charge l’exécution en parallèle de plusieurs packages dans le catalogue SSISDB. Pour plus d’informations, consultez [Exécuter des packages dans Scale Out](run-packages-in-integration-services-ssis-scale-out.md).
