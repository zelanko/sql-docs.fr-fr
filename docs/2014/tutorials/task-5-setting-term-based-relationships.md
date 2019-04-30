---
title: 'Tâche 5 : Définition du terme en fonction des relations | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6569d512-637d-4f7b-82e1-1e8582278b37
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 322c5a5afcd7c5d82982a86cb9398e66bb248c5d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63277248"
---
# <a name="task-5-setting-term-based-relationships"></a>Tâche 5 : Définition des relations basées sur des termes
  Dans cette tâche, vous définissez quelques relations de base de termes pour les valeurs pour le **Supplier Name** domaine. Une relation de base de termes vous permet d’apporter une correction pour un terme qui fait partie d’une valeur dans un domaine. Plusieurs valeurs qui sont identiques à l'exception de l'orthographe d'une partie commune peuvent ainsi être considérées comme synonymes identiques. Par exemple, **Inc.** peut être corrigé par **Incorporated**. DQS utilise ces relations lors des processus de découverte des connaissances, de nettoyage, ou de mise en correspondance. Consultez [en fonction du terme de créer des Relations](https://msdn.microsoft.com/library/hh510404.aspx) pour plus d’informations.  
  
1.  Sélectionnez **Supplier Name** dans le **liste des domaines**.  
  
2.  Basculez vers le **relations de base de termes** onglet dans le volet droit.  
  
3.  Cliquez sur **ajouter une nouvelle relation** la barre d’outils pour ajouter une relation à la table.  
  
4.  Type **Co.** pour le **valeur** champ et **entreprise** pour le **corriger vers** champ.  
  
5.  Répétez les deux étapes précédentes pour les valeurs suivantes :  
  
    |Value|Corriger vers|  
    |-----------|----------------|  
    |Corp.|Corporation|  
    |Inc.|Incorporated|  
  
     ![Relations de base de termes](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "Relations de base de termes")  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 6 : Définition des synonymes](../../2014/tutorials/task-6-setting-synonyms.md)  
  
  
