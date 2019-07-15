---
title: Paramétrer l’administration automatisée dans une entreprise | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- performance [SQL Server], automated administration
- tuning automated administration [SQL Server]
- monitoring performance [SQL Server], automated administration
ms.assetid: 671fed35-3859-4b0d-8f38-4dd07436857e
author: markingmyname
ms.author: maghan
manager: jroth
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 671b2e98cf9e9969af68612d75af97bb17984c99
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67681422"
---
# <a name="tune-automated-administration-across-an-enterprise"></a>Paramétrer l'administration automatisée dans une entreprise
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

L'administration multiserveur avec Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent tire parti des fonctionnalités de paramétrage automatique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par conséquent, dans des conditions normales, il n'est pas nécessaire d'affiner le paramétrage des travaux. Toutefois, les charges réseau s'accroissent quand vous exécutez des travaux, quand vous générez des alertes et quand vous envoyez des notifications à des opérateurs. Vous pouvez paramétrer l'administration automatisée dans une entreprise afin de réduire au minimum le trafic réseau généré par ces activités.  
  
## <a name="see-also"></a>Voir aussi  
[Surveillance des performances du moteur de flux de données](../../integration-services/performance/performance-counters.md)  
  
