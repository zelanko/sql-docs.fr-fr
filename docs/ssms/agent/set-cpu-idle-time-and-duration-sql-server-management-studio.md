---
title: Définir le seuil et la durée d'inactivité de l'UC
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CPU [SQL Server], idle conditions
- time [SQL Server], CPU idle and duration
- duration of CPU idle [SQL Server]
- SQL Server Agent, CPU idle conditions
- idle time [SQL Server]
ms.assetid: 8647b465-d899-4cc7-9640-134a506d0a2e
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: bedb1d5e732caf92c8e42ea7fa89738dd20b1388
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75253251"
---
# <a name="set-cpu-idle-time-and-duration"></a>Définir le seuil et la durée d'inactivité de l'UC

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cette rubrique indique comment définir la condition d'inactivité de l'UC pour votre serveur dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] au moyen de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. La définition d'inactivité d'UC a une incidence sur la réponse aux événements de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Par exemple, supposons que vous définissez la condition d'inactivité de l'UC comme une utilisation UC moyenne tombant sous 10 % et restant à ce niveau pendant 10 minutes. Ensuite, si vous avez défini des travaux à exécuter lorsque l'UC du serveur atteint une condition d'inactivité, le travail démarre lorsque l'utilisation de l'UC tombe sous 10 % et reste à ce niveau pendant 10 minutes. S'il s'agit d'un travail qui a un impact significatif sur les performances de votre serveur, la définition de la condition d'inactivité de l'UC est importante.  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-set-cpu-idle-time-and-duration"></a>Pour définir le seuil et la durée d'inactivité de l'UC  
  
1.  Dans **l’Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]et développez-la.  
  
2.  Cliquez avec le bouton droit sur **Agent SQL Server**, cliquez sur **Propriétés**, puis sélectionnez la page **Avancé** .  
  
3.  Sous **Condition d'inactivité de l'UC**, procédez comme suit :  
  
    -   Activez la case à cocher **Définir la condition d'inactivité de l'UC**.  
  
    -   Spécifiez un pourcentage pour la zone **La moyenne d’utilisation de l’UC tombe en dessous de** (tous les UC). Cette intervention définit le niveau d'utilisation sous lequel l'UC doit tomber avant d'être considérée inactive.  
  
    -   Spécifiez un nombre de secondes pour la zone **Et reste sous ce niveau pendant** . Cette intervention définit la durée d'utilisation d'UC minimale au terme de laquelle l'UC est considérée inactive.  
  
