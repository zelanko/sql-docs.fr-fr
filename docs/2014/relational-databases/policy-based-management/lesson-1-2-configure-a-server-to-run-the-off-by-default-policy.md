---
title: Configurer un serveur pour exécuter la stratégie Désactivé par défaut | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 41c3022d-ab13-443e-ac64-ba1d64584f79
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 82cf55e1fa3fa9bda5a625ef89335a9f81ed5505
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63057533"
---
# <a name="configure-a-server-to-run-the-off-by-default-policy"></a>Configurer un serveur pour exécuter la stratégie Désactivé par défaut
  Vous disposez désormais d'une stratégie nommée Désactivé par défaut. Dans cette tâche, vous allez vérifier si votre serveur est conforme aux spécifications de cette stratégie.  
  
### <a name="to-run-the-off-by-default-policy"></a>Pour exécuter la stratégie Désactivé par défaut  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], pointez sur **Stratégies**, puis cliquez sur **Évaluer**.  
  
2.  Dans la boîte de dialogue **Évaluer les stratégies** , vous pouvez sélectionner des stratégies à partir d’une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou d’un fichier. Pour cette étape, laissez le paramètre **Source** défini à votre instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
3.  Dans la section **Stratégies** , sélectionnez la stratégie **Désactivé par défaut** .  
  
4.  Pour voir si le serveur est conforme à la stratégie, cliquez sur **Évaluer**.  
  
5.  Dans la zone **Résultats** , vous verrez un cercle vert avec une coche si le [!INCLUDE[ssDE](../../includes/ssde-md.md)] est conforme à la stratégie. Vous verrez un cercle rouge avec un X si le [!INCLUDE[ssDE](../../includes/ssde-md.md)] n'est pas conforme à la stratégie.  
  
6.  Dans la zone **Détails sur les cibles** , des informations supplémentaires apparaîtront dans la colonne **Message** si une erreur se produit. Dans la colonne **Message** , cliquez sur **Afficher** pour voir un rapport contenant les résultats de la vérification de chaque propriété de facette.  
  
7.  La description de stratégie est affichée en bas de la page et la section **Aide supplémentaire** affiche le lien hypertexte que vous avez configuré pour la stratégie. Cliquez sur le lien hypertexte pour ouvrir la page Web que vous avez spécifiée lors de la création de la stratégie.  
  
8.  Fermez le navigateur, puis fermez la boîte de dialogue **Vue détaillée des résultats** .  
  
9. Si le serveur n’est pas conforme et que vous souhaitez désactiver la messagerie de base de données, cliquez sur **Appliquer** dans la page **Résultats d’évaluation** .  
  
10. Fermez les boîtes de dialogue **Vue détaillée des résultats** et **Évaluer les stratégies** .  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 2 : Créer et appliquer une stratégie de standards de nommage](lesson-2-create-and-apply-a-naming-standards-policy.md)  
  
  
