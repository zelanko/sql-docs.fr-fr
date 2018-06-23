---
title: 'Tâche 8 : Création d’une règle de domaine Composite | Documents Microsoft'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff3b662-7876-4445-9bdd-96be35b3ca0c
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 18461e889e56f647b869d2b60cae49d662786160
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153161"
---
# <a name="task-8-creating-a-composite-domain-rule"></a>Tâche 8 : Création d'une règle de domaine composite
  Dans cette tâche, vous créez une règle pour le **Validation d’adresses** domaine composite. Vous définissez une règle interdomaines : si **Ville** est **Los Angeles**, **état** doit être **autorité de certification** où **Ville** et **état** sont deux domaines.  
  
1.  Dans le volet droit, basculez vers le **CD règles** onglet.  
  
2.  Cliquez sur **ajouter une nouvelle règle de domaine** à partir de la barre d’outils.  
  
3.  Type **règle état-Ville** pour **nom** et appuyez sur **entrée**.  
  
4.  Dans le **une règle de génération** volet, sélectionnez **Ville** dans la liste des domaines, puis sélectionnez la condition **valeur est égale à** et type **Los Angeles** pour le valeur.  
  
5.  Dans le **puis** volet, sélectionnez **état** dans la liste des domaines, puis sélectionnez **valeur est égale à**, type **autorité de certification** pour la valeur et appuyez sur **Onglet**.  
  
     ![Règle de domaine composite](../../2014/tutorials/media/et-creatingacompositedomainrule.jpg "règle de domaine Composite")  
  
6.  Cliquez sur **fermer** situé en bas de la page pour passer à la page principale du Client DQS. Vous allez publier la base de connaissances dans la leçon suivante. Notez que la base de connaissances est à l'état verrouillé (icône de verrou).  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 9 : Configuration d’un Service de données de référence](../../2014/tutorials/task-9-configuring-a-reference-data-service.md)  
  
  