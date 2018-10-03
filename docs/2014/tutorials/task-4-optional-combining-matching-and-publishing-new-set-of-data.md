---
title: 'Tâche 4 (facultatif) : combinaison, la correspondance et publier un nouvel ensemble de données | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 13a13f03-b307-4555-8e33-6d98c459d994
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2bfa1c59fb47a859bb680970617a81add871908e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48061749"
---
# <a name="task-4-optional-combining-matching-and-publishing-new-set-of-data"></a>Tâche 4 (Facultatif) : Combiner, mettre en correspondance et publier un nouvel ensemble de données
  Au fil du temps, vous souhaiterez ajouter des données au référentiel MDS. Avant d’ajouter des données, il peut être utile pour comparer les nouvelles données aux données qui sont déjà managées dans MDS, pour vous assurer que vous n’ajoutez pas de données dupliquées ou incorrectes. Dans le complément Master Data Services pour Excel, vous pouvez combiner les données de deux feuilles de calcul et les comparer afin d'identifier et supprimer les doublons, avant de les publier dans MDS. La fonctionnalité de correspondance dans le complément MDS pour Excel utilise la fonctionnalité de correspondance de DQS pour identifier les correspondances de données. Dans cette tâche, vous allez combiner les données de deux feuilles de calcul dans une seule feuille, puis vous allez exercer l'activité de correspondance pour identifier et supprimer les doublons avant la publication dans MDS. Consultez [correspondance de qualité de données dans le complément MDS pour Excel](http://msdn.microsoft.com/library/hh548681.aspx) et [combiner des données](http://msdn.microsoft.com/library/hh548680.aspx) rubriques pour plus d’informations.  
  
1.  Lancez une nouvelle instance de **Excel**. Cliquez sur **Démarrer**, pointez sur **exécuter**, type **Excel**, puis cliquez sur **OK**.  
  
2.  Basculez vers le **données maîtres** onglet en cliquant sur **données maîtres** sur la barre de menus.  
  
3.  Cliquez sur **Connect** sur le ruban dans le **se connecter et charger** groupe pour se connecter à la **serveur MDS**. Vous avez configuré cette connexion précédemment dans cette leçon.  
  
     ![Excel - afficher le bouton d’Explorateur de données de référence](../../2014/tutorials/media/et-combinematchandpublishnewsod-01.jpg "Excel - afficher le bouton d’Explorateur de données de référence")  
  
4.  Vous devez voir le **Explorateur de données Master** volet à droite. Si vous ne voyez pas l’Explorateur de données principale, cliquez sur **afficher l’Explorateur** bouton sur le ruban.  
  
5.  Dans le **Explorateur de données de référence** fenêtre, sélectionnez **fournisseurs** dans la liste déroulante pour le **modèle**. Vous devez voir que le modèle a une entité : **fournisseur**.  
  
     ![Excel - fenêtre de l’Explorateur de données Master](../../2014/tutorials/media/et-combinematchandpublishnewsod-02.jpg "Excel - fenêtre de l’Explorateur de données Master")  
  
6.  Double-cliquez sur **fournisseur** dans la liste des entités pour charger les membres d’entité dans la feuille de calcul Excel.  
  
7.  Cliquez sur **Sheet2** en bas pour basculer vers le **Sheet2** onglet. Si vous ne voyez pas **Sheet2**, ajouter une nouvelle feuille de calcul.  
  
8.  Ouvrez **Suppliers.xls** (le fichier d’origine d’entrée qui est inclus dans les fichiers des didacticiels) de fichiers et de copier toutes les lignes (trois) de la **CombineAndCleanse** feuille de calcul à **Sheet2**.  
  
9. Revenez à la **fournisseur** feuille dans le **Book 1-Microsoft Excel** (pas le **nettoyées et mises en correspondance la liste des fournisseurs** Excel) qui est connecté à **MDS**.  
  
10. Cliquez sur **données maîtres** sur la barre de menus.  
  
11. Cliquez sur **combiner des données** sur le ruban. Vous verrez la **combiner des données** boîte de dialogue.  
  
12. Dans le **combiner des données** boîte de dialogue, cliquez sur le bouton suivant pour **plage à combiner avec les données MDS** zone de texte, comme illustré dans l’image suivante.  
  
     ![Excel - boîte de dialogue données de combiner](../../2014/tutorials/media/et-combinematchandpublishnewsod-03.jpg "Excel - boîte de dialogue données de combiner")  
  
13. Vous devez maintenant voir la boîte de dialogue réduite. Maintenant, cliquez sur **Sheet2** pour basculer vers le **Sheet2** onglet qui contient les nouvelles données de fournisseur avec 4 lignes (ligne d’en-tête incluse).  
  
14. Dans le **Sheet2**, sélectionnez **toutes les lignes, y compris la ligne d’en-tête** (même si elles semblent être déjà sélectionnées). Vous devez voir le **plage à combiner avec les données MDS** est automatiquement mis à jour.  
  
     ![Excel - boîte de dialogue de données - réduit de combiner](../../2014/tutorials/media/et-combinematchandpublishnewsod-04.jpg "Excel - boîte de dialogue de données - réduit de combiner")  
  
15. Revenez à la **fournisseurs** onglet sans fermer la **combiner des données** boîte de dialogue.  
  
16. Cliquez sur le **bouton** à côté du **zone de texte**. Vous devez maintenant voir la boîte de dialogue développée. Vous devez voir tous les mappages entre les colonnes de la **fournisseur** MDS **entité** à **Excel** colonnes sont automatiquement remplies.  
  
     ![Excel - boîte de dialogue de données rempli avec des données de combiner](../../2014/tutorials/media/et-combinematchandpublishnewsod-05.jpg "Excel - boîte de dialogue de données rempli avec des données de combiner")  
  
17. Vérifiez que **Code** entité est mappée à la **SupplierID** colonne dans la feuille de calcul et **Code postal** entité est mappée à la **Code postal** colonne dans la feuille de calcul.  
  
18. Sur le **combiner des données** boîte de dialogue, cliquez sur **combiner**.  
  
19. Vérifiez que trois lignes de données sont ajoutées au bas de la feuille de calcul et qu'elles sont codées par couleur.  
  
     ![Excel - nouveaux éléments après la combinaison](../../2014/tutorials/media/et-combinematchandpublishnewsod-06.jpg "Excel - nouveaux éléments après la combinaison")  
  
20. Cliquez sur **données mathématiques** sur le ruban pour identifier les doublons. Cette fonction utilise la fonctionnalité de correspondance de DQS.  
  
21. Dans le **faire correspondre les données** boîte de dialogue, sélectionnez **fournisseurs** pour **Base de connaissances DQS**.  
  
     ![Excel - boîte de dialogue de données de correspondance](../../2014/tutorials/media/et-combinematchandpublishnewsod-07.jpg "Excel - boîte de dialogue de données de correspondance")  
  
22. Mappez les colonnes de la feuille de calcul aux domaines, comme indiqué dans le tableau suivant.  
  
    |Colonne de feuille de calcul|Domaine|  
    |----------------------|------------|  
    |Code (vous avez téléchargé l'ID du fournisseur en tant que code de l'entité du fournisseur dans MDS)|ID du fournisseur|  
    |Nom (vous avez téléchargé le nom du fournisseur en tant que nom de l'entité du fournisseur sur MDS)|Nom du fournisseur|  
    |ContactEmailAddress|ContactEmail|  
  
23. Sélectionnez **prérequis** pour le **Code** mappage de colonnes.  
  
24. Entrez **70 %** en tant que le **poids** pour **Supplier Name** et **30 %** en tant que le **poids** pour **Adresse E-mail de contact** comme indiqué dans l’image.  
  
25. Cliquez sur **OK**.  
  
26. Le processus de correspondance doit identifier un doublon pour le fournisseur avec **Code : S1**.  
  
     ![Excel - résultats de correspondance](../../2014/tutorials/media/et-combinematchandpublishnewsod-08.jpg "Excel - résultats de correspondance")  
  
27. Sélectionnez le **ligne dupliquée (orange)**, avec le bouton droit, puis cliquez sur **supprimer** pour supprimer la ligne.  
  
28. Supprimer le **CLUSTER_ID** colonne dans la mesure où il devenues inutiles.  
  
29. Cliquez sur **publier** pour publier les autres deux nouveaux enregistrements avec **Codes S66** et **S57** à MDS.  
  
30. Dans le **publier et annoter** boîte de dialogue zone, ajoutez un **annotation**, puis cliquez sur **publier**.  
  
31. Basculez vers le **application Web Master Data Manager**.  
  
32. Sur la page d’accueil, vérifiez que **fournisseurs** est sélectionné pour le **modèle**, puis cliquez sur **Explorer**. Si vous avez déjà la **Explorer** ouvert, actualisez le navigateur internet.  
  
33. **Tri** la liste par **Code** et recherchez les enregistrements avec **S57** et **S66** en tant que codes. Vous pouvez également utiliser le **filtre** la barre d’outils pour rechercher un enregistrement spécifique dans la liste.  
  
34. Maintenant, fermez **Book1 – Microsoft Excel** fenêtre sans enregistrer le fichier.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 5 : Création d’un attribut basé sur un domaine à partir d’Excel](../../2014/tutorials/task-5-creating-a-domain-based-attribute-from-excel.md)  
  
  
