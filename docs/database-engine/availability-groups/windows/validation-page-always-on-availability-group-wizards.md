---
title: "Page Validation (Assistants Groupe de disponibilité Always On) | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.addreplicawizard.validation.f1
- sql13.swb.adddatabasewizard.validation.f1
- sql13.swb.newagwizard.validation.f1
helpviewer_keywords:
- ', listeners'
ms.assetid: c8971556-240c-491a-bc86-9cc72f71a3dd
caps.latest.revision: 16
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 6f8c43c0c8a698fb38f67f7ba6ba0ad897692f00
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="validation-page-always-on-availability-group-wizards"></a>Page Validation (Assistants Groupe de disponibilité Always On)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  
    
  Cette rubrique d’aide décrit les options de la page **Validation** . Cette rubrique s'applique à l' [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)], à l' [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)]et à l' [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Utilisez cette page pour confirmer que votre environnement prend en charge tous les choix de configuration que vous avez apportés dans les pages précédentes de l'Assistant.  
  
##  <a name="PageOptions"></a> Options de la page Validation  
 **Résultats de la validation du groupe de disponibilité.**  
 Cette grille affiche les résultats de chaque étape de validation finalisée. Les colonnes de la grille sont les suivantes :  
  
 **Nom**  
 Affiche une expression qui décrit une étape spécifique.  
  
 **Résultat**  
 Affiche l'un des textes de lien hypertexte suivants. Pour plus d'informations sur le résultat d'une étape de validation donnée, cliquez sur le lien hypertexte.  
  
|Résultat|Description|  
|------------|-----------------|  
|**Erreur**|Indique que l'étape de validation a échoué. Cliquez sur le lien pour afficher le message d'erreur.|  
|**Ignoré**|Indique que l'étape de validation a été ignorée parce qu'elle n'était pas requise par vos sélections. Cliquez sur le lien pour afficher la raison pour laquelle une étape a été ignorée.|  
|**Réussi**|Indique que l'étape de validation s'est terminée avec succès|  
|**Avertissement**|Indique un problème potentiel avec la configuration du groupe de disponibilité.  Cliquez sur le lien pour afficher le message d'avertissement.|  
  
 **Réexécuter la validation**  
 Cliquez pour répéter les étapes de validation si vous apportez une modification à l'extérieur de l'Assistant en réponse à une erreur de validation.  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Utiliser la boîte de dialogue Nouveau groupe de disponibilité &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Ajouter un réplica au groupe de disponibilité &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Ajouter une base données au groupe de disponibilité &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/availability-group-add-database-to-group-wizard.md)  
  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  

