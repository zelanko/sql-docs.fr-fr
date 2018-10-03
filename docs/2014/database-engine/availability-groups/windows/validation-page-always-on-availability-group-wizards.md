---
title: Page validation (Assistants de groupe de disponibilité AlwaysOn) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.newagwizard.validation.f1
- sql12.swb.addreplicawizard.validation.f1
- sql12.swb.adddatabasewizard.validation.f1
helpviewer_keywords:
- ', listeners'
ms.assetid: c8971556-240c-491a-bc86-9cc72f71a3dd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6cf16c8afb363a1b7727b6da3a5f75bf966ab0d2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48152951"
---
# <a name="validation-page-alwayson-availability-group-wizards"></a>Page Validation (Assistants Groupe de disponibilité AlwaysOn)
  Cette rubrique d’aide décrit les options de la page **Validation** . Cette rubrique s'applique à l' [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)], à l' [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)]et à l' [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Utilisez cette page pour confirmer que votre environnement prend en charge tous les choix de configuration que vous avez apportés dans les pages précédentes de l'Assistant.  
  
##  <a name="PageOptions"></a> Options de la page Validation  
 **Résultats de la validation du groupe de disponibilité.**  
 Cette grille affiche les résultats de chaque étape de validation finalisée. Les colonnes de la grille sont les suivantes :  
  
 **Nom**  
 Affiche une expression qui décrit une étape spécifique.  
  
 **Result**  
 Affiche l'un des textes de lien hypertexte suivants. Pour plus d'informations sur le résultat d'une étape de validation donnée, cliquez sur le lien hypertexte.  
  
|Résultats|Description|  
|------------|-----------------|  
|**Erreur**|Indique que l'étape de validation a échoué. Cliquez sur le lien pour afficher le message d'erreur.|  
|**Ignoré**|Indique que l'étape de validation a été ignorée parce qu'elle n'était pas requise par vos sélections. Cliquez sur le lien pour afficher la raison pour laquelle une étape a été ignorée.|  
|**Réussi**|Indique que l'étape de validation s'est terminée avec succès|  
|**Avertissement**|Indique un problème potentiel avec la configuration du groupe de disponibilité.  Cliquez sur le lien pour afficher le message d'avertissement.|  
  
 **Réexécuter la validation**  
 Cliquez pour répéter les étapes de validation si vous apportez une modification à l'extérieur de l'Assistant en réponse à une erreur de validation.  
  

  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Utiliser la boîte de dialogue Nouveau groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Ajouter un réplica au groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Ajouter une base données au groupe de disponibilité &#40;SQL Server Management Studio&#41;](availability-group-add-database-to-group-wizard.md)  
  
 
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  
