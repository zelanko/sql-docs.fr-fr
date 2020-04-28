---
title: Propriétés de SQL Server (onglet haute disponibilité AlwaysOn) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: d8630923-a600-4f1c-aca1-027453a3ec82
author: mikeraymsft
ms.author: mikeray
manager: craigg
ms.openlocfilehash: daf3ed025405b753116bba267ce6f4c50d350601
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62678473"
---
# <a name="sql-server-properties-alwayson-high-availability-tab"></a>Propriétés de SQL Server (onglet Haute disponibilité AlwaysOn)
  Utilisez l'onglet **Haute disponibilité AlwaysOn** de la boîte de dialogue **Propriétés de SQL Server** du Gestionnaire de configurations [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour activer ou désactiver la fonctionnalité Groupes de disponibilité AlwaysOn de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. L'activation de Groupes de disponibilité AlwaysOn est une condition préalable nécessaire pour une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour utiliser les groupes de disponibilité comme solution de haute disponibilité et de récupération d'urgence.  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> Conditions préalables  
 Pour être activée pour Groupes de disponibilité AlwaysOn, une instance de serveur doit respecter la configuration requise suivante :  
  
-   L'instance de serveur doit résider sur un nœud de Clustering de basculement Windows Server (WSFC).  
  
-   Pour appartenir au même groupe de disponibilité, les instances doivent être dans le même cluster WSFC. Un groupe de disponibilité ne peut pas s'étendre sur plusieurs clusters WSFC.  
  
-   L'instance du serveur doit exécuter une édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui prend en charge [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].  
  
-   Activez Groupes de disponibilité AlwaysOn pour une seule instance de serveur à la fois. Après avoir activé Groupes de disponibilité AlwaysOn, attendez le redémarrage du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant d'activer l'instance de serveur suivante.  
  
> [!NOTE]  
>  Pour plus d’informations sur la prise en charge des fonctionnalités et sur les conditions préalables, restrictions et recommandations supplémentaires pour [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], consultez la documentation en ligne de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
## <a name="dialog-options"></a>Options de boîte de dialogue  
 **Nom du cluster de basculement Windows**  
 Affiche le nom du cluster WSFC dans lequel l'ordinateur local est un nœud.  
  
 **Activation des groupes à haute disponibilité AlwaysOn**  
 Utilisez cette case à cocher pour activer ou désactiver Groupes de disponibilité AlwaysOn sur cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], comme suit :  
  
-   Si cette case à cocher est vide, Groupes de disponibilité AlwaysOn est désactivé. Pour activer Groupes de disponibilité AlwaysOn, activez cette case à cocher, cliquez sur **OK**et redémarrez manuellement le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Si cette case à cocher est déjà sélectionnée, Groupes de disponibilité AlwaysOn est activé. Pour désactiver Groupes de disponibilité AlwaysOn, désactivez la case à cocher et cliquez sur **OK**. Cela entraîne le redémarrage de l'instance de serveur.  
  
    > [!TIP]  
    >  Après avoir désactivé Groupes de disponibilité AlwaysOn, supprimez les réplicas de disponibilité locales de l'instance de serveur. Si vous supprimez la dernière réplica d'un groupe de disponibilité donné, supprimez également le groupe.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
  
> [!NOTE]  
>  Pour plus d'informations sur le suivi après la désactivation de Groupes de disponibilité AlwaysOn et la procédure à suivre pour créer et configurer des groupes de disponibilité, consultez la documentation en ligne de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
  
