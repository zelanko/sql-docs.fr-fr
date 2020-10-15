---
description: Paramétrer l'administration automatisée dans une entreprise
title: Paramétrer l'administration automatisée dans une entreprise
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- performance [SQL Server], automated administration
- tuning automated administration [SQL Server]
- monitoring performance [SQL Server], automated administration
ms.assetid: 671fed35-3859-4b0d-8f38-4dd07436857e
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6fbb2e883e77ed797fb367c3624429c2b1a4d720
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92038726"
---
# <a name="tune-automated-administration-across-an-enterprise"></a>Paramétrer l'administration automatisée dans une entreprise

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance), la plupart, mais pas toutes les fonctionnalités SQL Server Agent sont actuellement prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Managed Instance et SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

L'administration multiserveur avec Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent tire parti des fonctionnalités de paramétrage automatique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par conséquent, dans des conditions normales, il n'est pas nécessaire d'affiner le paramétrage des travaux. Toutefois, les charges réseau s'accroissent quand vous exécutez des travaux, quand vous générez des alertes et quand vous envoyez des notifications à des opérateurs. Vous pouvez paramétrer l'administration automatisée dans une entreprise afin de réduire au minimum le trafic réseau généré par ces activités.  

## <a name="see-also"></a>Voir aussi

[Surveillance des performances du moteur de flux de données](../../integration-services/performance/performance-counters.md)