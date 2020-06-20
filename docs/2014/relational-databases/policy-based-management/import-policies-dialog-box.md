---
title: Importer des stratégies, boîte de dialogue | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.importpolicy.f1
ms.assetid: 78ab5f6e-2f13-4788-937e-8892ef4e2345
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5820a49a51358a409e5f87ddca0b79c797a9eeab
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063865"
---
# <a name="import-policies-dialog-box"></a>Boîte de dialogue Importer des stratégies
  Utilisez cette boîte de dialogue pour importer une ou plusieurs stratégies (et leur condition référencée) enregistrées en tant que fichiers XML dans l'instance [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] active.  
  
## <a name="options"></a>Options  
 **Fichiers à importer**  
 Pour importer une stratégie à partir d’un fichier XML, tapez le nom et le chemin du fichier ou utilisez le bouton d’exploration ( **...** ).  
  
 **Remplacer les doublons avec les éléments importés**  
 Sélectionnez cette option pour remplacer toute stratégie ou condition existante du même nom si elle existe déjà sur cette instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Une condition avec une stratégie dépendante ne peut pas être remplacée, à moins que la stratégie dépendante ne soit également remplacée. Si cette option n'est pas sélectionnée, une condition existante qui utilise la même expression de condition ne provoquera pas d'erreur.  
  
 **État de la stratégie**  
 Sélectionnez l'état que vous souhaitez attribuer à la stratégie importée :  
  
-   **Conserver l'état de la stratégie lors de l'importation**  
  
-   **Activer toutes les stratégies lors de l'importation**  
  
-   **Désactiver toutes les stratégies lors de l'importation**  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer des serveurs à l'aide de la Gestion basée sur des stratégies](administer-servers-by-using-policy-based-management.md)   
 [Importer une stratégie de gestion basée sur des stratégies](import-a-policy-based-management-policy.md)   
 [Exporter une stratégie de gestion basée sur des stratégies](export-a-policy-based-management-policy.md)  
  
  
