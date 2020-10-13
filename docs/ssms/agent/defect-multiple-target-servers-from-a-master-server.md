---
description: Annuler l'inscription de plusieurs serveurs cibles dans un serveur maître
title: Annuler l'inscription de plusieurs serveurs cibles dans un serveur maître
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
- multiple target server defections
ms.assetid: 61a3713b-403a-4806-bfc4-66db72ca1156
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b784a2a6cee59cc2e1b192b5f9c32bd0ed6f421c
ms.sourcegitcommit: 610e3ebe21ac6575850a29641a32f275e71557e3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91784960"
---
# <a name="defect-multiple-target-servers-from-a-master-server"></a>Annuler l'inscription de plusieurs serveurs cibles dans un serveur maître

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Managed Instance](https://docs.microsoft.com/azure/azure-sql/managed-instance/sql-managed-instance-paas-overview), la plupart, mais pas toutes les fonctionnalités SQL Server Agent sont actuellement prises en charge. Pour plus d’informations, consultez [Azure SQL Managed Instance à partir de SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cette rubrique explique comment annuler l'inscription de plusieurs serveurs cibles sur une configuration d'administration multiserveur dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Exécutez la procédure suivante à partir du serveur maître :  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-defect-multiple-target-servers-from-a-master-server"></a>Pour annuler l'inscription de plusieurs serveurs cibles dans un serveur maître  
  
1.  Dans l' **Explorateur d'objets**, développez un serveur configuré en tant que serveur maître.  
  
2.  Cliquez avec le bouton droit sur **Agent SQL Server**, pointez sur **Administration multiserveur**, puis cliquez sur **Gérer les serveurs cibles**.  
  
3.  Cliquez sur **Publier les instructions**puis, dans la liste **Type d'instruction** , sélectionnez **Désinscrire**.  
  
4.  Sous **Destinataires**, activez l'une des options suivantes :  
  
    -   **Tous les serveurs cibles** pour annuler l'inscription de tous les serveurs cibles de ce serveur principal. Utilisez cette option si vous souhaitez désinstaller complètement la configuration de l'administration multiserveur active.  
  
    -   **Serveurs cibles sélectionnés**, puis cliquez sur la zone **Sélectionner** correspondante afin d'annuler l'inscription de certains serveurs cibles (mais pas tous) de ce serveur maître.  
  
## <a name="see-also"></a>Voir aussi  
[Créer un environnement multi-serveur](../../ssms/agent/create-a-multiserver-environment.md)  
[Administration automatisée à l'échelle d'une entreprise](../../ssms/agent/automated-administration-across-an-enterprise.md)  
[Annuler l’inscription d’un serveur cible dans un serveur maître](../../ssms/agent/defect-a-target-server-from-a-master-server.md)  
  
