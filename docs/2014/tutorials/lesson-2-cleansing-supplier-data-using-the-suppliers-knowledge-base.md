---
title: 'Leçon 2 : Nettoyage des données des fournisseurs à l’aide de la Base de connaissances fournisseurs | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 215c14de-fc3f-46de-a022-bf69b9ea2a96
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 42006c68a50497034817cfe8df6c9172ea0cdc3b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62931424"
---
# <a name="lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base"></a>Leçon 2 : Nettoyage des données des fournisseurs avec la base de connaissances Fournisseurs
  Dans cette leçon, vous nettoyez les données des fournisseurs dans un fichier Excel à l’aide de la **fournisseurs** vous avez créé dans la première leçon de base de connaissances. Nettoyage des données dans DQS comprend un **processus assisté par ordinateur** qui analyse la façon dont les données sont conformes à la base de connaissances dans une base de connaissances et un **processus interactif** qui vous permet de réviser et modifier résultats du processus assisté par ordinateur. La fonctionnalité de nettoyage des données identifie les données incorrectes dans votre source de données et les corrige, ou suggère des corrections. Elle normalise et enrichit également les données client en utilisant des valeurs de domaine, des valeurs menantes pour les synonymes, des règles de domaine, des relations à base de termes et des données de référence. Vous pouvez approuver ou refuser en mode interactif les modifications proposées par le processus assisté par ordinateur. Consultez [nettoyage des données](https://msdn.microsoft.com/library/gg524800.aspx) pour plus d’informations.  
  
 Le processus assisté par ordinateur utilise les valeurs de seuil suivantes, que vous pouvez configurer à l'aide de l'option Configuration dans la page principale du Client DQS.  
  
-   **Score minimal pour obtenir des suggestions :** Le score minimal ou un niveau de confiance qui est utilisé par DQS pour suggérer le remplacement d’une valeur.  
  
-   **Score minimal pour les corrections automatiques :** Le score minimal ou un niveau de confiance qui est utilisé par DQS pour corriger automatiquement une valeur.  
  
 Consultez [configurer les valeurs de seuil pour le nettoyage et correspondance](https://msdn.microsoft.com/library/hh510415.aspx) pour plus d’informations sur la façon de configurer ces paramètres.  
  
 Dans cette leçon, vous allez effectuer les tâches suivantes pour nettoyer les données d'entrée à l'aide de la base de connaissances Fournisseurs.  
  
1.  Créer un projet de qualité des données pour le nettoyage, sélectionner la base de connaissances Fournisseurs comme base de connaissances à utiliser pour analyser et nettoyer les données sources dans un fichier Excel, puis sélectionner l'activité de nettoyage.  
  
2.  Mapper les colonnes Excel que vous souhaitez nettoyer aux domaines/domaines composites DQS appropriés dans la base de connaissances.  
  
3.  Exécuter l'activité de nettoyage assistée par ordinateur. Le processus assisté par ordinateur affiche les informations de qualité des données dans le Data Quality Client utilisé pour nettoyer les données de façon interactive.  
  
4.  Affichez et gérez les résultats de l'activité de nettoyage. Vous pouvez examiner les valeurs qui le processus assisté par ordinateur identifie comme correctes, incorrectes mais corrigées, incorrectes avec une modification suggérée, ou non valides. Vous pouvez approuver ou refuser de façon interactive les modifications, ou corriger ou remplacer la suggestion du processus assisté par ordinateur, en utilisant le champ Corriger vers.  
  
5.  Exporter les résultats du nettoyage dans un fichier Excel.  
  
6.  Importer les valeurs du projet de nettoyage dans des domaines pour enrichir les connaissances de la base de connaissances avec les nouvelles règles, les valeurs, les corrections etc....  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 1 : Création d’un projet de qualité des données](../../2014/tutorials/task-1-creating-a-data-quality-project.md)  
  
  
