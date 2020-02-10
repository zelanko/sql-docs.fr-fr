---
title: 'Tâche 4 (facultatif) : combinaison, correspondance et publication d’un nouveau jeu de données | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 13a13f03-b307-4555-8e33-6d98c459d994
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 2d27a5bcd87ffd84b33de229d955dc9494846a72
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65489269"
---
# <a name="task-4-optional-combining-matching-and-publishing-new-set-of-data"></a>Tâche 4 (Facultatif) : Combiner, mettre en correspondance et publier un nouvel ensemble de données
  Au fil du temps, vous souhaiterez ajouter des données au référentiel MDS. Avant d’ajouter des données, il peut être utile de comparer les nouvelles données aux données qui sont déjà gérées dans MDS, pour vous assurer que vous n’ajoutez pas de données dupliquées ou inexactes. Dans le complément Master Data Services pour Excel, vous pouvez combiner les données de deux feuilles de calcul et les comparer afin d'identifier et supprimer les doublons, avant de les publier dans MDS. La fonctionnalité de correspondance dans le complément MDS pour Excel utilise la fonctionnalité de correspondance de DQS pour identifier les correspondances de données. Dans cette tâche, vous allez combiner les données de deux feuilles de calcul dans une seule feuille, puis vous allez exercer l'activité de correspondance pour identifier et supprimer les doublons avant la publication dans MDS. Pour plus d’informations, consultez [correspondance de la qualité des données dans les rubriques complément MDS pour Excel](https://msdn.microsoft.com/library/hh548681.aspx) et [combiner les données](https://msdn.microsoft.com/library/hh548680.aspx) .  
  
1.  Lancez une nouvelle instance d' **Excel**. Cliquez sur **Démarrer**, pointez sur **exécuter**, tapez **Excel**, puis cliquez sur **OK**.  
  
2.  Basculez vers l’onglet **données** de référence en cliquant sur **données** de référence dans la barre de menus.  
  
3.  Cliquez sur **connexion** sur le ruban dans le groupe **se connecter et charger** pour vous connecter au **serveur MDS**. Vous avez configuré cette connexion précédemment dans cette leçon.  
  
     ![Excel - Afficher le bouton d'explorateur dans l'onglet des données de référence](../../2014/tutorials/media/et-combinematchandpublishnewsod-01.jpg "Excel - Afficher le bouton d'explorateur dans l'onglet des données de référence")  
  
4.  Le volet **Explorateur de données maître** doit s’afficher à droite. Si le Explorateur de données maître ne s’affiche pas, cliquez sur le bouton **afficher l’Explorateur** sur le ruban.  
  
5.  Dans la fenêtre **Explorateur de données principale** , sélectionnez **fournisseurs** dans la liste déroulante du **modèle**. Vous devez voir que le modèle a une entité : **Supplier**.  
  
     ![Excel - Fenêtre Explorateur de données de référence](../../2014/tutorials/media/et-combinematchandpublishnewsod-02.jpg "Excel - Fenêtre Explorateur de données de référence")  
  
6.  Double-cliquez sur **Supplier** dans la liste d’entités pour charger les membres d’entité dans la feuille de calcul Excel.  
  
7.  Cliquez sur **Feuil2** en bas pour basculer vers l’onglet **Feuil2** . Si vous ne voyez pas **Feuil2**, ajoutez une nouvelle feuille de calcul.  
  
8.  Ouvrez le fichier **Suppliers. xls** (le fichier d’entrée d’origine inclus dans les fichiers du didacticiel) et copiez toutes les lignes (trois) de la feuille de calcul **CombineAndCleanse** dans **Feuil2**.  
  
9. Revenez à la feuille du **fournisseur** dans le **livre 1 : Microsoft Excel** (pas le **nettoyage et le correspondance des fournisseurs** Excel) qui est connecté à **MDS**.  
  
10. Dans la barre de menus, cliquez sur **données** de référence.  
  
11. Cliquez sur **combiner des données** sur le ruban. La boîte de dialogue **combiner des données** s’affiche.  
  
12. Dans la boîte de dialogue **combiner des données** , cliquez sur le bouton en regard de la zone **de texte plage à combiner avec les données MDS** , comme indiqué dans l’image suivante.  
  
     ![Excel - Boîte de dialogue Combiner des données](../../2014/tutorials/media/et-combinematchandpublishnewsod-03.jpg "Excel - Boîte de dialogue Combiner des données")  
  
13. Vous devez maintenant voir la boîte de dialogue réduite. Maintenant, cliquez sur **Feuil2** pour basculer vers l’onglet **Feuil2** qui contient les nouvelles données de fournisseur avec 4 lignes (y compris une ligne d’en-tête).  
  
14. Dans **Feuil2**, sélectionnez **toutes les lignes, y compris la ligne d’en-tête** (même si elles semblent être déjà sélectionnées). Vous devez voir la **plage à combiner avec les données MDS** est automatiquement mise à jour.  
  
     ![Excel - Boîte de dialogue Combiner des données - Réduit](../../2014/tutorials/media/et-combinematchandpublishnewsod-04.jpg "Excel - Boîte de dialogue Combiner des données - Réduit")  
  
15. Revenez à l’onglet **fournisseurs** sans fermer la boîte de dialogue **combiner des données** .  
  
16. Cliquez sur le **bouton** en regard de la **zone de texte**. Vous devez maintenant voir la boîte de dialogue développée. Vous devez voir que tous les mappages entre les colonnes de l' **entité** MDS du **fournisseur** et les colonnes **Excel** sont renseignés automatiquement.  
  
     ![Excel - Boîte de dialogue Combiner des données comme étant rempli des données](../../2014/tutorials/media/et-combinematchandpublishnewsod-05.jpg "Excel - Boîte de dialogue Combiner des données comme étant rempli des données")  
  
17. Vérifiez que la colonne d’entité **code** est mappée à la colonne **RéfFournisseur** dans la feuille de calcul et que la colonne d’entité **Code postal** est mappée à la colonne **Code postal** de la feuille de calcul.  
  
18. Dans la boîte de dialogue **combiner des données** , cliquez sur **combiner**.  
  
19. Vérifiez que trois lignes de données sont ajoutées au bas de la feuille de calcul et qu'elles sont codées par couleur.  
  
     ![Excel - Nouveaux éléments après la combinaison](../../2014/tutorials/media/et-combinematchandpublishnewsod-06.jpg "Excel - Nouveaux éléments après la combinaison")  
  
20. Cliquez sur **données mathématiques** sur le ruban pour identifier les doublons. Cette fonction utilise la fonctionnalité de correspondance de DQS.  
  
21. Dans la boîte de dialogue **correspondance des données** , sélectionnez **Suppliers** pour la **base de connaissances DQS**.  
  
     ![Excel - Boîte de dialogue Mettre en correspondance les données](../../2014/tutorials/media/et-combinematchandpublishnewsod-07.jpg "Excel - Boîte de dialogue Mettre en correspondance les données")  
  
22. Mappez les colonnes de la feuille de calcul aux domaines, comme indiqué dans le tableau suivant.  
  
    |Colonne de feuille de calcul|Domain|  
    |----------------------|------------|  
    |Code (vous avez téléchargé l'ID du fournisseur en tant que code de l'entité du fournisseur dans MDS)|ID du fournisseur|  
    |Nom (vous avez téléchargé le nom du fournisseur en tant que nom de l'entité du fournisseur sur MDS)|Nom du fournisseur|  
    |ContactEmailAddress|ContactEmail|  
  
23. Sélectionnez **condition préalable** pour le mappage de colonne de **code** .  
  
24. Entrez **70%** comme **poids** pour le **nom du fournisseur** et **30%** comme **poids** de l' **e-mail du contact** , comme indiqué dans l’image.  
  
25. Cliquez sur **OK**.  
  
26. Le processus de correspondance doit identifier un doublon pour le fournisseur avec le **Code : S1**.  
  
     ![Excel - Résultats de correspondance](../../2014/tutorials/media/et-combinematchandpublishnewsod-08.jpg "Excel - Résultats de correspondance")  
  
27. Sélectionnez la **ligne dupliquée (orange)**, cliquez avec le bouton droit, puis cliquez sur **supprimer** pour supprimer la ligne.  
  
28. Supprimez la colonne **CLUSTER_ID** , car vous n’en avez plus besoin.  
  
29. Cliquez sur **publier** pour publier les deux nouveaux enregistrements avec les **codes S66** et **S57** pour MDS.  
  
30. Dans la boîte de dialogue **publier et annoter** , ajoutez une **annotation**, puis cliquez sur **publier**.  
  
31. Basculez vers l' **application Web Data Manager maître**.  
  
32. Sur la page d’hébergement, vérifiez que **fournisseurs** est sélectionné pour le **modèle**, puis cliquez sur **Explorateur**. Si vous avez déjà ouvert l' **Explorateur** , actualisez le navigateur Internet.  
  
33. **Triez** la liste par **code** et recherchez les enregistrements avec **S57** et **S66** en tant que codes. Vous pouvez également utiliser le bouton **filtre** de la barre d’outils pour rechercher un enregistrement spécifique dans la liste.  
  
34. Maintenant, fermez le fichier **Classeur1-fenêtre Microsoft Excel** sans enregistrer le fichier.  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 5 : Créer un attribut basé sur un domaine à partir d'Excel](../../2014/tutorials/task-5-creating-a-domain-based-attribute-from-excel.md)  
  
  
