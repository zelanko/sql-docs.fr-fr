---
title: Références (Générateur de rapports), boîte de dialogue Propriétés de rapport | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10082"
ms.assetid: 3414c857-8ea6-4fc4-a6d5-b4883c039efa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ef34d756629b2e281d02ff4c808b1a7862624886
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59967945"
---
# <a name="report-properties-dialog-box-references-report-builder"></a>Boîte de dialogue Propriétés du rapport, Références (Générateur de rapports)
  Sélectionnez **Références** dans la boîte de dialogue **Propriétés du rapport** pour ajouter ou supprimer des références aux assemblys personnalisés ou externes et aux instances de classes personnalisées qui sont utilisées par des expressions dans la définition de rapport. Les assemblys personnalisés ne sont pas pris en charge en mode local dans le Générateur de rapports. Pour créer des rapports qui utilisent des assemblys personnalisés, utilisez le Concepteur de rapports dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
## <a name="options"></a>Options  
 **Ajouter ou supprimer des assemblys**  
 Répertorie les assemblys référencés par le rapport. L'assembly doit être disponible sur l'ordinateur où est installé l'outil que vous utilisez pour concevoir le rapport, ainsi que sur le serveur de rapports. Le nom de la référence doit correspondre le contenu de  **\<CodeModule >** exactement les balises dans le fichier de langage de définition de rapport (.rdl).  
  
 **Ajouter**  
 Cliquez pour ajouter un assembly. Cliquez sur le bouton points de suspension (...) pour ouvrir la **ouvrir** boîte de dialogue et sélectionner les assemblys nécessaires pour terminer l’évaluation de traitement et d’expression de rapport.  
  
 **Supprimer**  
 Pour supprimer une référence d’assembly de la liste, sélectionnez le nom de l’assembly, puis cliquez sur le bouton **Supprimer** .  
  
 **Ajouter ou supprimer des classes**  
 Répertorie les instances de classes utilisées par le rapport. Cette liste de classes est utilisée uniquement par des membres d'instances, et non par des membres statiques.  
  
 **Ajouter**  
 Cliquez pour ajouter une référence de classe. Cliquez sur le bouton points de suspension (...) pour ouvrir la **ouvrir** boîte de dialogue et sélectionner les classes nécessaires pour terminer l’évaluation de traitement et d’expression de rapport.  
  
 **Supprimer**  
 Pour supprimer l’instance de classe, sélectionnez-la et cliquez sur le bouton **Supprimer** .  
  
 **Monter**  
 Pour les classes qui ont des dépendances, vous pouvez faire monter cette référence dans la liste.  
  
 **Descendre**  
 Pour les classes qui ont des dépendances, vous pouvez faire descendre cette référence dans la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide du Générateur de rapports pour les boîtes de dialogue, les volets et les Assistants](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)  
  
  
