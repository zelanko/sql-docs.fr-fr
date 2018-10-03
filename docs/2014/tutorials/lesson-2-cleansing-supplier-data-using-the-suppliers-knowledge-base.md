---
title: 'Leçon 2 : Nettoyage des données des fournisseurs à l’aide de la Base de connaissances fournisseurs | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 215c14de-fc3f-46de-a022-bf69b9ea2a96
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d957c5ddb394828ed29f169796bcb2bf19cea6a3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48162589"
---
# <a name="lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base"></a>Leçon 2 : Nettoyage des données des fournisseurs avec la base de connaissances Fournisseurs
  Dans cette leçon, vous nettoyez les données des fournisseurs dans un fichier Excel à l’aide de la **fournisseurs** vous avez créé dans la première leçon de base de connaissances. Nettoyage des données dans DQS comprend un **processus assisté par ordinateur** qui analyse la façon dont les données sont conformes à la base de connaissances dans une base de connaissances et un **processus interactif** qui vous permet de réviser et modifier résultats du processus assisté par ordinateur. La fonctionnalité de nettoyage des données identifie les données incorrectes dans votre source de données et les corrige, ou suggère des corrections. Elle normalise et enrichit également les données client en utilisant des valeurs de domaine, des valeurs menantes pour les synonymes, des règles de domaine, des relations à base de termes et des données de référence. Vous pouvez approuver ou refuser en mode interactif les modifications proposées par le processus assisté par ordinateur. Consultez [nettoyage des données](http://msdn.microsoft.com/library/gg524800.aspx) pour plus d’informations.  
  
 Le processus assisté par ordinateur utilise les valeurs de seuil suivantes, que vous pouvez configurer à l'aide de l'option Configuration dans la page principale du Client DQS.  
  
-   **Score minimal pour les suggestions :** le score minimal ou niveau de confiance qui est utilisé par DQS pour suggérer le remplacement d’une valeur.  
  
-   **Score minimal pour les corrections automatiques :** le score minimal ou niveau de confiance qui est utilisé par DQS pour corriger automatiquement une valeur.  
  
 Consultez [configurer les valeurs de seuil pour le nettoyage et correspondance](http://msdn.microsoft.com/library/hh510415.aspx) pour plus d’informations sur la façon de configurer ces paramètres.  
  
 Dans cette leçon, vous allez effectuer les tâches suivantes pour nettoyer les données d'entrée à l'aide de la base de connaissances Fournisseurs.  
  
1.  Créer un projet de qualité des données pour le nettoyage, sélectionner la base de connaissances Fournisseurs comme base de connaissances à utiliser pour analyser et nettoyer les données sources dans un fichier Excel, puis sélectionner l'activité de nettoyage.  
  
2.  Mapper les colonnes Excel que vous souhaitez nettoyer aux domaines/domaines composites DQS appropriés dans la base de connaissances.  
  
3.  Exécuter l'activité de nettoyage assistée par ordinateur. Le processus assisté par ordinateur affiche les informations de qualité des données dans le Data Quality Client utilisé pour nettoyer les données de façon interactive.  
  
4.  Affichez et gérez les résultats de l'activité de nettoyage. Vous pouvez examiner les valeurs qui le processus assisté par ordinateur identifie comme correctes, incorrectes mais corrigées, incorrectes avec une modification suggérée, ou non valides. Vous pouvez approuver ou refuser de façon interactive les modifications, ou corriger ou remplacer la suggestion du processus assisté par ordinateur, en utilisant le champ Corriger vers.  
  
5.  Exporter les résultats du nettoyage dans un fichier Excel.  
  
6.  Importer les valeurs du projet de nettoyage dans des domaines pour enrichir les connaissances de la base de connaissances avec de nouvelles règles, des valeurs, des corrections, etc.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 1 : Création d’un projet de qualité des données](../../2014/tutorials/task-1-creating-a-data-quality-project.md)  
  
  
