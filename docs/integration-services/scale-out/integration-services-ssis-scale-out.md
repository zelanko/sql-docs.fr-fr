---
title: "SQL Server Integration Services (SSIS) de montée en charge | Documents Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dcfbd1c5-c001-4fb7-b9ae-916e49ab6a96
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ce7fb96901e8af4da74392fe0a0a85c6e2ec05a4
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="integration-services-ssis-scale-out"></a>Integration Services (SSIS) Scale Out
[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out constitue un moyen très performant d’exécuter des packages en distribuant les exécutions sur plusieurs ordinateurs. Vous pouvez soumettre une demande de plusieurs exécutions de packages dans SQL Server Management Studio. Les packages sont alors exécutés en parallèle, en mode « Scale Out ».  

[!INCLUDE[ssIS_md](../../includes/ssis-md.md)]Monter en charge se compose d’un [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] échelle Out maître et un ou plusieurs [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] montée en puissance des processus de travail. Le Scale Out Master est responsable de la gestion de Scale Out et reçoit les demandes d’exécution de package des utilisateurs. Les Scale Out Workers extraient les tâches d’exécution du Scale Out Master et effectuent le travail d’exécution de package. Pour plus d’informations, consultez [Scale Out Master](integration-services-ssis-scale-out-master.md), [Scale Out Worker](integration-services-ssis-scale-out-worker.md).

[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]Monter en charge peut être configuré sur un ordinateur, où une mise à l’échelle des principale et un montée en puissance des processus de travail sont définis côte à côte sur l’ordinateur. Scale Out peut également s’exécuter sur plusieurs ordinateurs, auquel cas chaque Scale Out Worker est sur un ordinateur différent.
- [Procédure pas à pas : Configurer Integration Services Scale Out](walkthrough-set-up-integration-services-scale-out.md)

Scale Out prend en charge l’exécution en parallèle de plusieurs packages dans le catalogue SSISDB. Pour plus d’informations, consultez [Exécuter des packages dans Scale Out](run-packages-in-integration-services-ssis-scale-out.md).

