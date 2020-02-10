---
title: 'Leçon 2 : nettoyage des données des fournisseurs à l’aide de la base de connaissances fournisseurs | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 215c14de-fc3f-46de-a022-bf69b9ea2a96
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: b99676a9f51bf76dc9db294365a5a628dd25fa2e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65488471"
---
# <a name="lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base"></a>Leçon 2 : Nettoyage des données des fournisseurs avec la base de connaissances Fournisseurs
  Dans cette leçon, vous allez nettoyer les données des fournisseurs dans un fichier Excel à l’aide de la base de connaissances **fournisseurs** que vous avez créée dans la première leçon. Le nettoyage de données dans DQS comprend un **processus assisté par ordinateur** qui analyse la conformité des données aux connaissances dans une base de connaissances et un **processus interactif** qui vous permet d’examiner et de modifier les résultats du processus assisté par ordinateur. La fonctionnalité de nettoyage des données identifie les données incorrectes dans votre source de données et les corrige, ou suggère des corrections. Elle normalise et enrichit également les données client en utilisant des valeurs de domaine, des valeurs menantes pour les synonymes, des règles de domaine, des relations à base de termes et des données de référence. Vous pouvez approuver ou refuser en mode interactif les modifications proposées par le processus assisté par ordinateur. Pour plus d’informations, consultez [nettoyage des données](https://msdn.microsoft.com/library/gg524800.aspx) .  
  
 Le processus assisté par ordinateur utilise les valeurs de seuil suivantes, que vous pouvez configurer à l'aide de l'option Configuration dans la page principale du Client DQS.  
  
-   **Score minimal pour les suggestions :** Score minimal ou niveau de confiance qui est utilisé par DQS pour suggérer le remplacement d’une valeur.  
  
-   **Score minimal pour les corrections automatiques :** Score minimal ou niveau de confiance qui est utilisé par DQS pour corriger automatiquement une valeur.  
  
 Pour plus d’informations sur la configuration de ces paramètres [, consultez Configurer les valeurs de seuil pour le nettoyage et la correspondance](https://msdn.microsoft.com/library/hh510415.aspx) .  
  
 Dans cette leçon, vous allez effectuer les tâches suivantes pour nettoyer les données d'entrée à l'aide de la base de connaissances Fournisseurs.  
  
1.  Créer un projet de qualité des données pour le nettoyage, sélectionner la base de connaissances Fournisseurs comme base de connaissances à utiliser pour analyser et nettoyer les données sources dans un fichier Excel, puis sélectionner l'activité de nettoyage.  
  
2.  Mapper les colonnes Excel que vous souhaitez nettoyer aux domaines/domaines composites DQS appropriés dans la base de connaissances.  
  
3.  Exécuter l'activité de nettoyage assistée par ordinateur. Le processus assisté par ordinateur affiche les informations de qualité des données dans le Data Quality Client utilisé pour nettoyer les données de façon interactive.  
  
4.  Affichez et gérez les résultats de l'activité de nettoyage. Vous pouvez examiner les valeurs qui le processus assisté par ordinateur identifie comme correctes, incorrectes mais corrigées, incorrectes avec une modification suggérée, ou non valides. Vous pouvez approuver ou refuser de façon interactive les modifications, ou corriger ou remplacer la suggestion du processus assisté par ordinateur, en utilisant le champ Corriger vers.  
  
5.  Exporter les résultats du nettoyage dans un fichier Excel.  
  
6.  Importez les valeurs du projet de nettoyage dans des domaines pour augmenter la connaissance dans la base de connaissances avec de nouvelles règles, valeurs, corrections, etc.  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 1 : Création d'un projet de qualité des données](../../2014/tutorials/task-1-creating-a-data-quality-project.md)  
  
  
