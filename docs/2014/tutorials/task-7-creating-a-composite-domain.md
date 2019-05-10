---
title: 'Tâche 7 : Création d’un domaine Composite | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ae778647-1df0-4952-9a69-0ef6177eea9c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: bbc00117e10e48adbde37b9f0561610feff8f87e
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65488965"
---
# <a name="task-7-creating-a-composite-domain"></a>Tâche 7 : Création d’un domaine composite
  Dans cette tâche, vous créez un domaine composite, **Validation d’adresses**, qui comprend **ligne d’adresse**, **Ville**, **état**et  **Code postal** domaines. Un domaine composite permet de définir une règle interdomaines qui implique plusieurs domaines. Un domaine composite présente d'autres avantages, notamment, il permet d'analyser une valeur de champ dans plusieurs domaines.  Par exemple, une valeur d'un champ Nom complet peut être analysée dans des domaines Prénom, Deuxième prénom et Nom de famille distincts. Dans ce didacticiel, vous allez uniquement définir une règle interdomaines. Consultez [gestion d’un domaine Composite](https://msdn.microsoft.com/library/hh510399.aspx) pour plus d’informations.  
  
1.  Dans le volet gauche, cliquez sur **créer un domaine composite** dans la barre d’outils.  
  
     ![Créer un bouton de barre d’outils du domaine Composite](../../2014/tutorials/media/et-creatingacompositedomain-01.jpg "créer un bouton de barre d’outils du domaine Composite")  
  
2.  Entrez **Validation d’adresses** pour le **nom de domaine Composite**.  
  
     ![Domaine Composite Validation d’adresses](../../2014/tutorials/media/et-creatingacompositedomain-02.jpg "domaine Composite Validation d’adresses")  
  
3.  Dans la liste des domaines sélectionnez **ligne d’adresse**, **Ville**, **état**, et **Zip** et cliquez sur **flèche droite** pour les ajouter à la **domaines du domaine Composite** liste.  
  
4.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 8 : Création d’une règle de domaine Composite](../../2014/tutorials/task-8-creating-a-composite-domain-rule.md)  
  
  
