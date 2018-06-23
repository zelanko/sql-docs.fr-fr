---
title: 'Tâche 5 : Définition du terme en fonction des relations | Documents Microsoft'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6569d512-637d-4f7b-82e1-1e8582278b37
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b8450d3e77de578810bb57c35aafad6f90c8f19c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36037925"
---
# <a name="task-5-setting-term-based-relationships"></a>Tâche 5 : Définition des relations basées sur des termes
  Dans cette tâche, vous définissez quelques relations à base de termes pour les valeurs de la **Supplier Name** domaine. Une relation de base de termes vous permet d’apporter une correction sur un terme qui fait partie d’une valeur dans un domaine. Plusieurs valeurs qui sont identiques à l'exception de l'orthographe d'une partie commune peuvent ainsi être considérées comme synonymes identiques. Par exemple, **Inc.** peut être corrigé par **Incorporated**. DQS utilise ces relations lors des processus de découverte des connaissances, de nettoyage, ou de mise en correspondance. Consultez [base de termes de créer des Relations](http://msdn.microsoft.com/library/hh510404.aspx) pour plus d’informations.  
  
1.  Sélectionnez **Supplier Name** dans les **liste des domaines**.  
  
2.  Basculez vers le **relations de base de termes** onglet dans le volet droit.  
  
3.  Cliquez sur **ajouter une nouvelle relation** dans la barre d’outils pour ajouter une relation à la table.  
  
4.  Type **Co.** pour le **valeur** champ et **société** pour le **corriger vers** champ.  
  
5.  Répétez les deux étapes précédentes pour les valeurs suivantes :  
  
    |Valeur|Corriger vers|  
    |-----------|----------------|  
    |Corp.|Corporation|  
    |Inc.|Incorporated|  
  
     ![Relations de base de termes](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "Relations de base de termes")  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 6 : Définition des synonymes](../../2014/tutorials/task-6-setting-synonyms.md)  
  
  