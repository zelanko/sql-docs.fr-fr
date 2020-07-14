---
title: Changer le compte proxy pour la collecte de l’utilitaire sur SQL Server géré | Microsoft Docs
description: Découvrez comment utiliser SQL Server Management Studio pour modifier le compte proxy pour le jeu d’éléments de collecte de l’utilitaire sur une instance gérée de SQL Server.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ff37ba8b-a08c-4109-b6e2-5748c995a52c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 052f0e6c1e60c5753f879e325c7cfa0603ba4303
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85776045"
---
# <a name="change-proxy-account-for-utility-collection-on--managed-sql-server"></a>Changer le compte proxy pour la collecte de l’utilitaire sur SQL Server géré
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette rubrique explique comment modifier le compte proxy pour le jeu d'éléments de collecte de l'utilitaire sur une instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-change-the-proxy-account-for-the-utility-collection-set-on-a-managed-instance-of-sql-server"></a>Pour modifier le compte proxy pour le jeu d'éléments de collecte de l'utilitaire sur une instance gérée de SQL Server  
  
1.  Supprimez l'instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    -   Dans l’ **Explorateur de l’utilitaire** dans SSMS, cliquez sur le nœud **Instances gérées** .  
  
    -   Dans l’**Explorateur de l’utilitaire** en mode Liste, cliquez avec le bouton droit sur le nom de l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et sélectionnez **Supprimer une instance gérée…** . Pour plus d’informations, consultez [Supprimer une instance de SQL Server de l’utilitaire SQL Server](../../relational-databases/manage/remove-an-instance-of-sql-server-from-the-sql-server-utility.md).  
  
2.  Réinscrivez l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  

    -   Dans l’**Explorateur de l’utilitaire** dans SSMS, cliquez avec le bouton droit sur le nœud **Instances gérées** et sélectionnez **Ajouter une instance gérée…** .  
  
    -   Suivez les indications de l'Assistant jusqu'au bout, en spécifiant le nouveau compte proxy.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités et tâches de l'utilitaire SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Résolution des problèmes liés à l’utilitaire SQL Server](https://msdn.microsoft.com/library/f5f47c2a-38ea-40f8-9767-9bc138d14453)  
  
  
