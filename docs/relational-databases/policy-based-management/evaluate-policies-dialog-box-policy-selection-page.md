---
title: "Boîte de dialogue Évaluer les stratégies, page Sélection de la stratégie | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.dmf.runnow.f1
ms.assetid: 20075fbe-0b48-42c8-b747-690f1aa23dcf
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 54f93115b0663a033fda00e85a2128a58a3db063
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="evaluate-policies-dialog-box-policy-selection-page"></a>Boîte de dialogue Évaluer les stratégies, page Sélectionner la stratégie
  Utilisez cette boîte de dialogue pour évaluer les stratégies de la Gestion basée sur des stratégies. En sélectionnant la page **Résultats d'évaluation** , vous pouvez appliquer des stratégies aux éléments d'un jeu de cibles non conforme aux stratégies.  
  
## <a name="options"></a>Options  
 **Source**  
 Spécifie la source des stratégies. Pour modifier la source, cliquez sur le bouton Parcourir (**...**) pour ouvrir la boîte de dialogue **Sélectionner une source** .  
  
 **Fichiers**  
 Tapez le chemin d’un fichier qui contient une stratégie de Gestion basée sur des stratégies, ou utilisez le bouton Parcourir (**...**) pour sélectionner le fichier.  
  
 **Server**  
 Sélectionnez cette option pour vous connecter à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui contient la stratégie souhaitée.  
  
 **Stratégies : Stratégie**  
 Cliquez sur cette option pour ouvrir la boîte de dialogue de la stratégie spécifiée.  
  
 **Stratégies : Catégorie**  
 Indique la catégorie de la stratégie. Cette zone est en lecture seule.  
  
 **Stratégies : Facette**  
 Indique la facette implémentée par la stratégie. Cette zone est en lecture seule.  
  
 **Évaluer**  
 Exécute la stratégie en mode d'évaluation. Cela génère un rapport de conformité pour le jeu de cibles mais n'applique pas la conformité future et ne reconfigure pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="possible-errors"></a>Erreurs possibles  
  
-   **Aucune cible n'a été trouvée**  
  
     Le jeu de cibles peut être vide pour l'une des raisons suivantes :  
  
    -   Il n'y a aucune cible sur l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du type spécifié par la stratégie.  
  
    -   La restriction de serveur exclut peut-être l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui contient la cible.  
  
    -   Si la stratégie est sur un objet dans une base de données (par exemple une table, une vue ou un utilisateur), la base de données n'est peut-être pas abonnée à la catégorie de la stratégie.  
  
    -   Le filtre de jeu de cibles exclut peut-être toutes les cibles sur cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Le type du serveur cible est différent du type du serveur sur lequel la stratégie est évaluée. Par exemple, dans le [!INCLUDE[ssDE](../../includes/ssde-md.md)], si vous essayez d'évaluer une stratégie qui a été créée pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous recevez un jeu de cibles vide.  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer des serveurs à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Boîte de dialogue Évaluer les stratégies, page Résultats d'évaluation](../../relational-databases/policy-based-management/evaluate-policies-dialog-box-evaluation-results-page.md)  
  
  
