---
title: 'Tâche 4 : définition des règles de domaine | Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3a7162ba-cf2f-481f-830d-bb6a02823827
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0104fe6b64ff2ecc1a37bb1da9691e34d7913f21
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061086"
---
# <a name="task-4-setting-domain-rules"></a>Tâche 4 : Définition de règles de domaine
  Dans cette tâche, vous allez créer une règle pour le domaine de **messagerie du contact** afin de vérifier si l’adresse de messagerie se termine par ** \@ Adventure-Works.com**. Pour plus d’informations sur la page, consultez la rubrique [création d’une règle de domaine](https://msdn.microsoft.com/library/hh510397.aspx) .  
  
1.  Cliquez sur **adresse de messagerie du contact** dans la **liste domaine**.  
  
2.  Basculez vers l’onglet **règles de domaine** dans le volet droit.  
  
     ![Bouton de la barre d'outils Ajouter une nouvelle règle de domaine](../../2014/tutorials/media/et-settingdomainrules-01.jpg "Bouton de la barre d'outils Ajouter une nouvelle règle de domaine")  
  
3.  Dans le volet droit, cliquez sur le bouton **Ajouter une nouvelle règle de domaine** dans la barre d’outils (Voir l’image) pour ajouter une règle.  
  
4.  Tapez **validation** de l’adresse de messagerie pour le nom de la **règle** et appuyez sur **entrée**. La case à cocher **active** doit être activée par défaut. Ce contrôle vous permet de désactiver temporairement une règle.  
  
5.  Dans le volet **créer une règle** , cliquez sur **flèche bas**, puis sélectionnez la **valeur se termine par**.  
  
6.  Tapez ** \@ Adventure-Works.com** dans la zone de texte et appuyez sur la touche **Tab**. Vous pouvez ajouter d’autres conditions en cliquant sur le bouton **Ajouter une nouvelle condition à la clause sélectionnée** dans le volet **créer une règle** .  
  
     ![Règle de validation du courrier électronique](../../2014/tutorials/media/et-settingdomainrules-02.jpg "Règle de validation du courrier électronique")  
  
7.  Cliquez sur le bouton **exécuter la règle de domaine sélectionnée sur les données de test** dans la barre d’outils du volet droit pour tester la règle par rapport aux exemples de données.  
  
     ![Bouton de la barre d'outils Exécuter la règle de domaine sur des données de test](../../2014/tutorials/media/et-settingdomainrules-03.jpg "Bouton de la barre d'outils Exécuter la règle de domaine sur des données de test")  
  
8.  Dans la boîte de dialogue **tester la règle de domaine** , cliquez sur **ajoute un nouveau terme de test pour le bouton règle de domaine** dans la barre d’outils.  
  
     ![Boîte de dialogue Tester une règle de domaine](../../2014/tutorials/media/et-settingdomainrules-04.jpg "Boîte de dialogue Tester une règle de domaine")  
  
9. Tapez **frank7 \@ Adventure-Works.com** (une valeur valide) dans la colonne **adresse de messagerie du contact** .  
  
10. Répétez les deux étapes précédentes pour ajouter **joe2 \@ Adventure-Work.com** (une valeur non valide, sans').  
  
11. Cliquez sur le dernier bouton (**tester la règle de domaine sur tous les termes**) de la barre d’outils pour tester les données d’entrée par rapport à la règle.  
  
     ![Bouton de la barre d'outils Tester la règle de domaine sur tous les termes](../../2014/tutorials/media/et-settingdomainrules-05.jpg "Bouton de la barre d'outils Tester la règle de domaine sur tous les termes")  
  
12. Notez que la première entrée est affichée comme un élément valide, et la seconde comme un élément non valide.  
  
     ![Résultats du test de la règle de domaine](../../2014/tutorials/media/et-settingdomainrules-06.jpg "Résultats du test de la règle de domaine")  
  
13. Cliquez sur **Fermer** pour fermer la boîte de dialogue **tester la règle de domaine** .  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 5 : Définition des relations basées sur des termes](../../2014/tutorials/task-5-setting-term-based-relationships.md)  
  
  
