---
title: 'Tâche 5 : définition des relations à base de termes | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6569d512-637d-4f7b-82e1-1e8582278b37
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5f10c82ef5e0b63e0b81b630ed0340545c876661
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85064740"
---
# <a name="task-5-setting-term-based-relationships"></a>Tâche 5 : Définition des relations basées sur des termes
  Au cours de cette tâche, vous allez définir quelques relations à base de termes pour les valeurs du domaine **nom du fournisseur** . Une relation à base de termes vous permet d’effectuer une correction sur un terme qui fait partie d’une valeur dans un domaine. Plusieurs valeurs qui sont identiques à l'exception de l'orthographe d'une partie commune peuvent ainsi être considérées comme synonymes identiques. Par exemple, **Inc.** peut être corrigé pour être **incorporé**. DQS utilise ces relations lors des processus de découverte des connaissances, de nettoyage, ou de mise en correspondance. Pour plus d’informations, consultez [créer des relations à base de termes](https://msdn.microsoft.com/library/hh510404.aspx) .  
  
1.  Sélectionnez **nom du fournisseur** dans la **liste domaine**.  
  
2.  Basculez vers l’onglet **relations à base de termes** dans le volet droit.  
  
3.  Cliquez sur le bouton **Ajouter une nouvelle relation** dans la barre d’outils pour ajouter une relation à la table.  
  
4.  Tapez **Co.** dans le champ **valeur** et **société** pour le champ **corriger vers** .  
  
5.  Répétez les deux étapes précédentes pour les valeurs suivantes :  
  
    |Valeur|Corriger vers|  
    |-----------|----------------|  
    |Corp.|Corporation|  
    |Inc.|Incorporated|  
  
     ![Relations à base de termes](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "Relations à base de termes")  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 6 : Définition des synonymes](../../2014/tutorials/task-6-setting-synonyms.md)  
  
  
