---
title: 'Tâche 8 : création d’une règle de domaine composite | Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: cff3b662-7876-4445-9bdd-96be35b3ca0c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 7e40ec982a9b2c43c3d55ec60179ac9a0b80e8a1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65489624"
---
# <a name="task-8-creating-a-composite-domain-rule"></a>Tâche 8 : Création d'une règle de domaine composite
  Dans cette tâche, vous allez créer une règle pour le domaine composite **validation d’adresse** . Vous définissez une règle inter-domaines : si la **ville** est **Los Angeles**, l' **État** doit être **ca** , où **ville** et **État** sont deux domaines.  
  
1.  Dans le volet droit, basculez vers l’onglet **règles du CD** .  
  
2.  Cliquez sur **Ajouter une nouvelle règle de domaine** dans la barre d’outils.  
  
3.  Tapez **règle d’état de ville** pour **nom** , puis appuyez sur **entrée**.  
  
4.  Dans le volet **créer une règle** , sélectionnez **City** dans la liste des domaines, puis sélectionnez la **valeur condition est égale à** et tapez **Los Angeles** comme valeur.  
  
5.  Dans le volet **Then** , sélectionnez **State** dans la liste de domaines, puis sélectionnez la **valeur est égale à**, tapez **ca** pour la valeur et appuyez sur **Tab**.  
  
     ![Règle du domaine composite](../../2014/tutorials/media/et-creatingacompositedomainrule.jpg "Règle du domaine composite")  
  
6.  Cliquez sur le bouton **Fermer** en bas de la page pour basculer vers la page principale du client DQS. Vous allez publier la base de connaissances dans la leçon suivante. Notez que la base de connaissances est à l'état verrouillé (icône de verrou).  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 9 : Configuration d'un service de données de référence](../../2014/tutorials/task-9-configuring-a-reference-data-service.md)  
  
  
