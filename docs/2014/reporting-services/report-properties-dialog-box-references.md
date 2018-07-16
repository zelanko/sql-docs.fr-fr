---
title: Boîte de dialogue Propriétés du rapport références | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "10530"
- sql12.rtp.rptdesigner.reportproperties.references.f1
ms.assetid: 4639d368-9918-4bb1-9953-7a724ca78dea
caps.latest.revision: 39
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: abc6ea1f5322303f8a4429f226e44fd32c018962
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299719"
---
# <a name="report-properties-dialog-box-references"></a>Boîte de dialogue Propriétés du rapport, Références
  Sélectionnez **Références** dans la boîte de dialogue **Propriétés du rapport** pour ajouter ou supprimer des références aux assemblys personnalisés ou externes et aux instances de classes personnalisées qui sont utilisées par des expressions dans la définition de rapport.  
  
## <a name="options"></a>Options  
 **Ajouter ou supprimer des assemblys**  
 Répertorie les assemblys référencés par le rapport. L'assembly doit être disponible sur l'ordinateur où est installé l'outil que vous utilisez pour concevoir le rapport, ainsi que sur le serveur de rapports. Le nom de la référence doit correspondre le contenu de  **\<CodeModule >** exactement les balises dans le fichier de langage de définition de rapport (.rdl).  
  
 **Ajouter**  
 Cliquez pour ajouter un assembly. Cliquez sur le bouton de sélection (...) pour ouvrir la boîte de dialogue **Ouvrir** et sélectionner les assemblys nécessaires pour effectuer le traitement du rapport et l’évaluation de l’expression.  
  
 **Supprimer**  
 Pour supprimer une référence d’assembly de la liste, sélectionnez le nom de l’assembly, puis cliquez sur le bouton **Supprimer** .  
  
 **Ajouter ou supprimer des classes**  
 Répertorie les instances de classes utilisées par le rapport. Cette liste de classes est utilisée uniquement par des membres d'instances, et non par des membres statiques.  
  
 **Ajouter**  
 Cliquez pour ajouter une référence de classe. Cliquez sur le bouton de sélection (...) pour ouvrir la boîte de dialogue **Ouvrir** et sélectionnez les classes nécessaires pour effectuer le traitement du rapport et l’évaluation de l’expression.  
  
 **Supprimer**  
 Pour supprimer l’instance de classe, sélectionnez-la et cliquez sur le bouton **Supprimer** .  
  
 **Monter**  
 Pour les classes qui ont des dépendances, vous pouvez faire monter cette référence dans la liste.  
  
 **Descendre**  
 Pour les classes qui ont des dépendances, vous pouvez faire descendre cette référence dans la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Code personnalisé et références d’assembly dans les expressions du Concepteur de rapports &#40;SSRS&#41;](report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)   
 [Références à des collections de variables de rapport et de groupe &#40;Générateur de rapports et SSRS&#41;](report-design/built-in-collections-report-and-group-variables-references-report-builder.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)  
  
  
