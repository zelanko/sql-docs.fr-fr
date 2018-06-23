---
title: 'Tâche 7 : Création d’un domaine Composite | Documents Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ae778647-1df0-4952-9a69-0ef6177eea9c
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e88fa44fb4457a979dfa1236531ed8bfa61f88fb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144190"
---
# <a name="task-7-creating-a-composite-domain"></a>Tâche 7 : Création d'une règle de domaine composite
  Dans cette tâche, vous créez un domaine composite, **Validation d’adresses**, qui comprend **adresse ligne**, **Ville**, **état**et  **Code postal** domaines. Un domaine composite permet de définir une règle interdomaines qui implique plusieurs domaines. Un domaine composite présente d'autres avantages, notamment, il permet d'analyser une valeur de champ dans plusieurs domaines.  Par exemple, une valeur d'un champ Nom complet peut être analysée dans des domaines Prénom, Deuxième prénom et Nom de famille distincts. Dans ce didacticiel, vous allez uniquement définir une règle interdomaines. Consultez [gestion d’un domaine Composite](http://msdn.microsoft.com/library/hh510399.aspx) pour plus d’informations.  
  
1.  Dans le volet gauche, cliquez sur **créer un domaine composite** dans la barre d’outils.  
  
     ![Créer un bouton de barre d’outils du domaine Composite](../../2014/tutorials/media/et-creatingacompositedomain-01.jpg "créer un bouton de barre d’outils du domaine Composite")  
  
2.  Entrez **adresse** pour le **nom de domaine Composite**.  
  
     ![Le domaine Composite de Validation d’adresses](../../2014/tutorials/media/et-creatingacompositedomain-02.jpg "domaine Composite Validation d’adresses")  
  
3.  Sélectionner, dans la liste des domaines **adresse ligne**, **Ville**, **état**, et **Zip** et cliquez sur **flèche droite** pour les ajouter à la **domaines du domaine Composite** liste.  
  
4.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 8 : Création d’une règle de domaine Composite](../../2014/tutorials/task-8-creating-a-composite-domain-rule.md)  
  
  