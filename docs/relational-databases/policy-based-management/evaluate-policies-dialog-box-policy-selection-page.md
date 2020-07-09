---
title: Page « Sélection de la stratégie » de la boîte de dialogue « Évaluer les stratégies »
description: Décrit la page « Sélection de la stratégie » de la boîte de dialogue « Évaluer les stratégies » dans le cadre de la gestion basée sur des stratégies via SSMS (SQL Server Management Studio).
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql13.swb.dmf.runnow.f1
ms.assetid: 20075fbe-0b48-42c8-b747-690f1aa23dcf
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: f82a5b8760710f0d72554e1f0b5b083ccd58294c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85749421"
---
# <a name="evaluate-policies-dialog-box-policy-selection-page"></a>Boîte de dialogue Évaluer les stratégies, page Sélectionner la stratégie
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Utilisez cette boîte de dialogue pour évaluer les stratégies de la Gestion basée sur des stratégies. En sélectionnant la page **Résultats d'évaluation** , vous pouvez appliquer des stratégies aux éléments d'un jeu de cibles non conforme aux stratégies.  
  
## <a name="options"></a>Options  
 **Source**  
 Spécifie la source des stratégies. Pour modifier la source, cliquez sur le bouton Parcourir ( **...** ) pour ouvrir la boîte de dialogue **Sélectionner une source** .  
  
 **Fichiers**  
 Tapez le chemin d’un fichier qui contient une stratégie de Gestion basée sur des stratégies, ou utilisez le bouton Parcourir ( **...** ) pour sélectionner le fichier.  
  
 **Serveur**  
 Sélectionnez cette option pour vous connecter à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui contient la stratégie souhaitée.  
  
 **Stratégies : Stratégie**  
 Cliquez sur cette option pour ouvrir la boîte de dialogue de la stratégie spécifiée.  
  
 **Stratégies : Catégorie**  
 Indique la catégorie de la stratégie. Cette zone est en lecture seule.  
  
 **Stratégies : Facette**  
 Indique la facette implémentée par la stratégie. Cette zone est en lecture seule.  
  
 **Evaluate**  
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
  
  
