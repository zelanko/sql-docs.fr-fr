---
title: "Nouveaut&#233;s d’Integration Services dans SQL Server vNext | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e26d7884-e772-46fa-bfdc-38567fe976a1
caps.latest.revision: 4
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 3
---
# Nouveaut&#233;s d’Integration Services dans SQL Server vNext
Cette rubrique décrit les fonctionnalités qui ont été ajoutées ou mises à jour dans [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].

>   [!NOTE] SQL Server vNext inclut également les fonctionnalités de SQL Server 2016 et les fonctionnalités ajoutées dans les mises à jour de SQL Server 2016. Pour plus d’informations sur les nouvelles fonctionnalités SSIS dans SQL Server 2016, consultez [Nouveautés d’Integration Services dans SQL Server 2016](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md).

## <a name="new-in-ssis-in-sql-server-vnext-ctp-11"></a>Nouveautés SSIS dans SQL Server vNext CTP 1.1

Il n’y a pas de nouvelles fonctionnalités SSIS dans SQL Server vNext CTP 1.1.

## <a name="new-in-ssis-in-sql-server-vnext-ctp-10"></a>Nouveautés SSIS dans SQL Server vNext CTP 1.0

### <a name="scale-out-for-ssis"></a>Scale Out pour SSIS

La fonctionnalité Scale Out facilite grandement l’exécution de [!INCLUDE[ssIS_md](../includes/ssis-md.md)] sur plusieurs ordinateurs. 
   
Après l’installation du Scale Out Master et des Scale Out Workers, le package peut être distribué pour s’exécuter automatiquement sur différents Workers. Si l’exécution est arrêtée inopinément, une nouvelle tentative est effectuée automatiquement. De plus, vous pouvez gérer toutes les exécutions et Workers de manière centralisée à l’aide du Master.
   
Pour plus d’informations, consultez [Integration Services Scale Out](../integration-services/integration-services-ssis-scale-out.md).
   
### <a name="support-for-microsoft-dynamics-online-resources"></a>Prise en charge des ressources Microsoft Dynamics Online

Le Gestionnaire de connexions OData et de sources OData prennent désormais en charge la connexion aux flux OData de Microsoft Dynamics AX Online et Microsoft Dynamics CRM Online.
