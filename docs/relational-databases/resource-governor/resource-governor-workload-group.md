---
title: Groupe de charge de travail du gouverneur de ressources | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, workload group
- workload groups [SQL Server]
- workload groups [SQL Server], overview
ms.assetid: a84c3c3f-55b6-4a30-9c42-13f082d9281e
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 4f15d4e443f0ffd6df700bff67ed6ba7514e0c90
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68126880"
---
# <a name="resource-governor-workload-group"></a>Groupe de charge de travail de Resource Governor
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Dans le gouverneur de ressources [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , un groupe de charge de travail sert de conteneur aux demandes de session qui ont des critères de classification similaires. Une charge de travail autorise l'analyse globale des sessions et définit les stratégies pour les sessions. Chaque groupe de charge de travail figure dans un pool de ressources, qui représente un sous-ensemble des ressources physiques d'une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Lorsqu'une session est démarrée, le classifieur du gouverneur de ressources affecte la session à un groupe de charge de travail spécifique, et la session doit s'exécuter à l'aide des stratégies assignées au groupe de charge de travail et aux ressources définies pour le pool de ressources.  
  
## <a name="workload-group-concepts"></a>Concepts autour des groupes de charge de travail  
 Un groupe de charge de travail sert de conteneur pour les demandes de session qui sont semblables selon les critères de classification appliqués à chaque demande. Un groupe de charges de travail permet l'analyse globale de la consommation des ressources et l'application d'une stratégie uniforme à toutes les demandes dans le groupe. Un groupe définit les stratégies pour ses membres.  
  
> [!NOTE]  
>  Les groupes de charges de travail définis par l'utilisateur peuvent être déplacés d'un pool de ressources à un autre.  
  
 Le gouverneur de ressources prédéfinit deux groupes de charges de travail : le groupe interne et le groupe par défaut. Un utilisateur ne peut pas modifier des éléments classés comme un groupe interne, mais il peut les surveiller. Les demandes sont classées dans le groupe par défaut si les conditions suivantes sont réunies :  
  
-   il n'existe pas de critères pour classer une demande ;  
  
-   une tentative pour classer la demande dans un groupe inexistant a été effectuée ;  
  
-   un échec de classification général s'est produit.  
  
 Le gouverneur de ressources fournit aussi des instructions DDL pour créer, changer et supprimer des groupes de charge de travail.  
  
## <a name="workload-group-tasks"></a>Tâches de groupe de charge de travail  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Décrit comment créer un groupe de charge de travail.|[Créer un groupe de charge de travail](../../relational-databases/resource-governor/create-a-workload-group.md)|  
|Décrit comment modifier les paramètres de groupe de charge de travail.|[Modifier les paramètres de groupe de charge de travail](../../relational-databases/resource-governor/change-workload-group-settings.md)|  
|Décrit comment supprimer un groupe de charge de travail.|[Supprimer un groupe de charge de travail](../../relational-databases/resource-governor/delete-a-workload-group.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [Activer Resource Governor](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [Pool de ressources de Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Fonction classifieur de Resource Governor](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [Configurer le gouverneur de ressources à l'aide d'un modèle](../../relational-databases/resource-governor/configure-resource-governor-using-a-template.md)   
 [Afficher les propriétés du gouverneur de ressources](../../relational-databases/resource-governor/view-resource-governor-properties.md)  
  
  
