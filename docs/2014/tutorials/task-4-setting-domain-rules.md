---
title: 'Tâche 4 : Définition des règles de domaine | Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3a7162ba-cf2f-481f-830d-bb6a02823827
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: f8816afcf44bdcb38f6513f61b3b88ce505dedc7
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56035310"
---
# <a name="task-4-setting-domain-rules"></a>Tâche 4 : Définition de règles de domaine
  Dans cette tâche, vous créez une règle pour le **adresse E-mail de Contact** afin de vérifier si l’adresse de messagerie se termine par **@adventure-works.com**. Consultez [création d’une règle de domaine](https://msdn.microsoft.com/library/hh510397.aspx) rubrique pour plus d’informations sur la page.  
  
1.  Cliquez sur **adresse E-mail de Contact** dans le **liste des domaines**.  
  
2.  Basculez vers le **règles de domaine** onglet dans le volet droit.  
  
     ![Ajoutez un nouveau bouton de barre d’outils de règle de domaine](../../2014/tutorials/media/et-settingdomainrules-01.jpg "ajouter un nouveau bouton de barre d’outils de règle de domaine")  
  
3.  Dans le volet droit, cliquez sur **ajouter une nouvelle règle de domaine** dans la barre d’outils (voir l’image) pour ajouter une règle.  
  
4.  Type **Validation par E-mail** pour le **nom de la règle** et appuyez sur **entrée**. Le **Active** case à cocher doit être activée par défaut. Ce contrôle vous permet de désactiver temporairement une règle.  
  
5.  Dans le **une règle de génération** volet, cliquez sur **flèche vers le bas**, puis sélectionnez **valeur se termine par**.  
  
6.  Type **@adventure-works.com** dans la zone de texte et appuyez sur **onglet**. Vous pouvez ajouter plus de conditions en cliquant sur **ajouter une nouvelle condition à la clause sélectionnée** bouton de barre d’outils dans le **une règle de génération** volet.  
  
     ![Règle de Validation de la messagerie](../../2014/tutorials/media/et-settingdomainrules-02.jpg "règle de Validation de la messagerie")  
  
7.  Cliquez sur **exécuter la règle de domaine sélectionné sur les données de test** dans la barre d’outils dans le volet droit pour tester la règle par rapport à des exemples de données.  
  
     ![Exécuter la règle de domaine sur le bouton de barre d’outils de données de Test](../../2014/tutorials/media/et-settingdomainrules-03.jpg "exécuter la règle de domaine sur le bouton de barre d’outils de données de Test")  
  
8.  Dans le **tester une règle de domaine** boîte de dialogue, cliquez sur **ajoute un nouveau terme de test pour la règle de domaine** dans la barre d’outils.  
  
     ![Tester la boîte de dialogue règle de domaine](../../2014/tutorials/media/et-settingdomainrules-04.jpg "tester la boîte de dialogue règle de domaine")  
  
9. Type **frank7@adventure-works.com** (une valeur valide) dans le **adresse E-mail de Contact** colonne.  
  
10. Répétez les étapes précédentes pour ajouter **joe2@adventure-work.com** (une valeur non valide sans nécessiter de ').  
  
11. Cliquez sur le bouton dernière (**tester la règle de domaine sur tous les termes**) dans la barre d’outils pour tester les données d’entrée par rapport à la règle.  
  
     ![Tester la règle de domaine sur le bouton de barre d’outils tous les termes du contrat](../../2014/tutorials/media/et-settingdomainrules-05.jpg "tester la règle de domaine sur le bouton de barre d’outils tous les termes du contrat")  
  
12. Notez que la première entrée est affichée comme un élément valide, et la seconde comme un élément non valide.  
  
     ![Tester les résultats des règles de domaine](../../2014/tutorials/media/et-settingdomainrules-06.jpg "tester les résultats des règles de domaine")  
  
13. Cliquez sur **fermer** pour fermer la **tester une règle de domaine** boîte de dialogue.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 5 : Définition du terme en fonction des relations](../../2014/tutorials/task-5-setting-term-based-relationships.md)  
  
  
