---
title: 'Tâche 7 : création d’un domaine composite | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ae778647-1df0-4952-9a69-0ef6177eea9c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 42936d25e267bcad5ba8ae512750f9e12f041579
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85064717"
---
# <a name="task-7-creating-a-composite-domain"></a>Tâche 7 : Création d’un domaine composite
  Au cours de cette tâche, vous allez créer un domaine composite, **validation d’adresse**, qui comprend les domaines **adresse**, **ville**, **État**et **Code postal** . Un domaine composite permet de définir une règle interdomaines qui implique plusieurs domaines. Un domaine composite présente d'autres avantages, notamment, il permet d'analyser une valeur de champ dans plusieurs domaines.  Par exemple, une valeur d'un champ Nom complet peut être analysée dans des domaines Prénom, Deuxième prénom et Nom de famille distincts. Dans ce didacticiel, vous allez uniquement définir une règle interdomaines. Pour plus d’informations, consultez [gestion d’un domaine composite](https://msdn.microsoft.com/library/hh510399.aspx) .  
  
1.  Dans le volet gauche, cliquez sur le bouton **créer un domaine composite** dans la barre d’outils.  
  
     ![Bouton à la barre d'outils Créer un domaine composite](../../2014/tutorials/media/et-creatingacompositedomain-01.jpg "Bouton à la barre d'outils Créer un domaine composite")  
  
2.  Entrez la **validation d’adresse** pour le nom de **domaine composite**.  
  
     ![Domaine composite de validation d'adresses](../../2014/tutorials/media/et-creatingacompositedomain-02.jpg "Domaine composite de validation d'adresses")  
  
3.  Dans la liste domaine, sélectionnez **adresse**, **ville**, **État**et **Code postal** , puis cliquez sur la **flèche droite** pour les ajouter à la liste **domaines dans le domaine composite** .  
  
4.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 8 : Création d’une règle de domaine composite](../../2014/tutorials/task-8-creating-a-composite-domain-rule.md)  
  
  
