---
title: Modifier la vue des résultats de Trace | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 860a80dc-bac0-4ef0-bf7f-7a9b430d7aa3
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 780772f7703e4499c13eb9373ccad4252097b536
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66089438"
---
# <a name="modify-the-trace-results-view"></a>Modifier la vue des résultats de trace
  Cette rubrique explique comment modifier la vue des résultats de trace d'une session événements étendus dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] en effectuant les tâches suivantes.  
  
1.  [Ajouter ou supprimer des colonnes](#AddRemoveColumns)  
  
2.  [Créer, modifier ou supprimer des colonnes fusionnées](#ChangeColumns)  
  
3.  [Trier les résultats](#SortResults)  
  
4.  [Regrouper les résultats](#GroupResults)  
  
5.  [Agréger les résultats](#AggregateResults)  
  
6.  [Filtrer les résultats](#Filter)  
  
7.  [Rechercher du texte dans les colonnes](#Search)  
  
8.  [Modifier les paramètres d’affichage](#ChangeDisplay)  
  
##  <a name="AddRemoveColumns"></a> Ajouter ou supprimer des colonnes  
  
1.  Ouvrez un fichier .XEL pour consulter les résultats de trace.  
  
    > [!NOTE]  
    >  Vous pouvez également cliquer avec le bouton droit sur le nom de session, puis sélectionner **Surveiller les données actives**.  
  
2.  Dans la fenêtre des résultats de trace, cliquez avec le bouton droit sur l'en-tête de colonne, puis sélectionnez **Choisir les colonnes**.  
  
3.  Dans la boîte de dialogue **Choisir les colonnes** , dans la section **Colonnes disponibles** , sélectionnez les noms de colonnes à ajouter, puis cliquez sur la flèche droite.  
  
    > [!NOTE]  
    >  Par défaut, les colonnes sont organisées par nom. Pour afficher les colonnes par événement, cliquez sur **Organiser par événement**.  
  
     Pour supprimer des colonnes, dans la section **Colonnes sélectionnées** , sélectionnez les colonnes à supprimer, puis cliquez sur la flèche gauche.  
  
4.  Dans la section **Colonnes sélectionnées** , pour modifier l'affichage de l'ordre des colonnes, cliquez respectivement sur **Monter** ou sur **Descendre** . Vous ne pouvez pas déplacer plusieurs lignes.  
  
5.  Cliquez sur **OK**.  
  
##  <a name="ChangeColumns"></a> Créer, modifier ou supprimer des colonnes fusionnées  
  
#### <a name="to-create-merged-columns"></a>Pour créer des colonnes fusionnées  
  
1.  Ouvrez un fichier .XEL pour consulter les résultats de trace.  
  
    > [!NOTE]  
    >  Vous pouvez également cliquer avec le bouton droit sur le nom de session, puis sélectionner **Surveiller les données actives**.  
  
2.  Dans la fenêtre des résultats de trace, cliquez avec le bouton droit sur l'en-tête de colonne, puis sélectionnez **Choisir les colonnes**.  
  
3.  Dans la boîte de dialogue **Choisir les colonnes** , cliquez sur **Nouveau**.  
  
4.  Dans la boîte de dialogue **Nouvelle colonne fusionnée** , dans la zone **Nom de la colonne fusionnée** , entrez un nom pour les colonnes fusionnées.  
  
5.  Dans la zone **Colonnes d'origine à fusionner** , sélectionnez deux colonnes ou plus à fusionner dans la liste déroulante.  
  
    > [!NOTE]  
    >  Les événements étendus prennent en charge la fusion de cinq colonnes au maximum.  
  
6.  Cliquez sur **OK**.  
  
#### <a name="to-edit-merged-columns"></a>Pour modifier des colonnes fusionnées  
  
1.  Ouvrez un fichier .XEL pour consulter les résultats de trace.  
  
    > [!NOTE]  
    >  Vous pouvez également cliquer avec le bouton droit sur le nom de session, puis sélectionner **Surveiller les données actives**.  
  
2.  Dans la fenêtre des résultats de trace, cliquez avec le bouton droit sur l'en-tête de colonne, puis sélectionnez **Choisir les colonnes**.  
  
3.  Dans la boîte de dialogue **Choisir les colonnes** , cliquez sur **Modifier**.  
  
4.  Pour modifier le nom de la colonne fusionnée, dans la boîte de dialogue **Nouvelle colonne fusionnée** , dans la zone **Nom de la colonne fusionnée** , entrez un nouveau nom.  
  
     Pour changer les colonnes que vous voulez fusionner, dans la zone **Colonnes d'origine à fusionner** , sélectionnez les colonnes que vous voulez fusionner dans la liste déroulante, puis cliquez sur **OK**.  
  
#### <a name="to-delete-merged-columns"></a>Pour supprimer des colonnes fusionnées  
  
1.  Ouvrez un fichier .XEL pour consulter les résultats de trace.  
  
    > [!NOTE]  
    >  Vous pouvez également cliquer avec le bouton droit sur le nom de session, puis sélectionner **Surveiller les données actives**.  
  
2.  Dans la fenêtre des résultats de trace, cliquez avec le bouton droit sur l'en-tête de colonne, puis sélectionnez **Choisir les colonnes**.  
  
3.  Dans la boîte de dialogue **Choisir les colonnes** , sélectionnez le nom de la colonne fusionnée à supprimer, puis cliquez sur **Supprimer**.  
  
##  <a name="SortResults"></a> Trier les résultats  
  
#### <a name="to-sort-the-results-in-ascending-or-descending-order"></a>Pour trier les résultats dans l'ordre croissant ou décroissant  
  
-   Ouvrez un fichier .XEL pour consulter les résultats de trace.  
  
    > [!NOTE]  
    >  Vous pouvez également cliquer avec le bouton droit sur le nom de session, sélectionner **Surveiller les données actives**, puis cliquer sur le bouton **Arrêter le flux de données** dans la barre d'outils.  
  
-   Dans la fenêtre des résultats de trace, cliquez avec le bouton droit sur l'en-tête de colonne que vous souhaitez trier. Cliquez sur **Tri croissant** ou **Tri décroissant** pour trier la colonne dans l'ordre croissant décroissant respectivement.  
  
     Si vous avez regroupé des colonnes, le tri de la colonne ne concerne que les données du groupe.  
  
##  <a name="GroupResults"></a> Regrouper des résultats  
  
#### <a name="to-group-the-results-by-a-single-column"></a>Pour regrouper les résultats par une seule colonne  
  
1.  Ouvrez un fichier .XEL pour consulter les résultats de trace.  
  
    > [!NOTE]  
    >  Vous pouvez également cliquer avec le bouton droit sur le nom de session, sélectionner **Surveiller les données actives**, puis cliquer sur le bouton **Arrêter le flux de données** dans la barre d'outils des événements étendus.  
  
2.  Dans la fenêtre des résultats de trace, cliquez avec le bouton droit sur l'en-tête de colonne à regrouper, puis sélectionnez **Regrouper par cette colonne**.  
  
#### <a name="to-group-the-results-by-multiple-columns"></a>Pour regrouper les résultats par plusieurs colonnes  
  
1.  Ouvrez un fichier .XEL pour consulter les résultats de trace.  
  
    > [!NOTE]  
    >  Vous pouvez également cliquer avec le bouton droit sur le nom de session, sélectionner **Surveiller les données actives**, puis cliquer sur le bouton **Arrêter le flux de données** dans la barre d'outils.  
  
2.  Cliquez sur le bouton **Regroupement** dans la barre d'outils des événements étendus.  
  
3.  Dans la boîte de dialogue **Regroupement** , dans la zone **Colonnes disponibles** , sélectionnez les colonnes à regrouper, puis cliquez sur la flèche droite.  
  
     Pour modifier l'ordre de regroupement, dans la section **Colonnes groupées** , cliquez sur les flèches haut ou bas.  
  
     Pour supprimer des colonnes du regroupement, dans la zone **Colonnes groupées** , sélectionnez les colonnes à supprimer, puis cliquez sur la flèche gauche.  
  
4.  Cliquez sur **OK**.  
  
##  <a name="AggregateResults"></a> Agréger les résultats  
 Les événements étendus prennent en charge cinq fonctions d'agrégation :  
  
-   Sum  
  
-   Min  
  
-   Max  
  
-   Moyenne  
  
-   Count  
  
 Somme, Min, Max et Moyenne peuvent être utilisés avec les colonnes numériques disponibles. La fonction « count » correspond au nombre de valeurs non Null qui existent pour la colonne sélectionnée dans le groupe.  
  
#### <a name="to-aggregate-results"></a>Pour agréger les résultats  
  
1.  Ouvrez un fichier .XEL pour consulter les résultats de trace.  
  
    > [!NOTE]  
    >  Vous pouvez également cliquer avec le bouton droit sur le nom de session, sélectionner **Surveiller les données actives**, puis cliquer sur le bouton **Arrêter le flux de données** dans la barre d'outils.  
  
    > [!NOTE]  
    >  L'agrégation est effectuée sur un groupe ; vous devez donc regrouper les résultats avant de pouvoir exécuter l'agrégation.  
  
2.  Dans la barre d'outils des événements étendus, cliquez sur le bouton **Agréger** .  
  
     La boîte de dialogue **Agrégation** apparaît avec les colonnes disponibles pour l'agrégation.  
  
3.  Sous **Type d'agrégation**, sélectionnez la manière d'agréger la colonne correspondante dans la liste déroulante.  
  
4.  Dans la zone **Trier l'agrégation par** , sélectionnez la colonne d'après laquelle vous souhaitez trier les données dans la liste déroulante.  
  
5.  Sélectionnez l'option **Dans l'ordre croissant** afin de trier le résultat de l'agrégation dans l'ordre croissant.  
  
6.  Sélectionnez l'option **Dans l'ordre décroissant** afin de trier le résultat de l'agrégation dans l'ordre décroissant.  
  
7.  Cliquez sur **OK**.  
  
##  <a name="Filter"></a> Filtrer les résultats  
 Vous pouvez appliquer des filtres pour limiter les résultats de trace affichés dans la fenêtre de trace. Le filtre d'affichage comprend un filtre de temps et un filtre avancé. Vous utilisez le filtre de temps pour filtrer les résultats de trace par horodatage d'un événement, et le filtre avancé pour élaborer des conditions de filtre à l'aide des actions et des champs d'événement. Il existe une relation AND logique entre les filtres de temps et les filtres avancés.  
  
#### <a name="to-create-a-filter"></a>Pour créer un filtre  
  
1.  Ouvrez un fichier .XEL pour consulter les résultats de trace.  
  
    > [!NOTE]  
    >  Vous pouvez également cliquer avec le bouton droit sur le nom de session, puis sélectionner **Surveiller les données actives**.  
  
2.  Dans la fenêtre des résultats de trace, sélectionnez les résultats que vous souhaitez filtrer, puis dans la barre d'outils d'événements étendus, cliquez sur le bouton **Filtres** .  
  
3.  Dans la boîte de dialogue **Filtres** , sélectionnez **Définir le filtre de temps** afin de définir le filtre de temps en faisant glisser les barres de curseur pour définir la chronologie. Notez que lorsque vous déplacez les barres de curseur, la zone de temps affiche la valeur d'heure en conséquence. Vous pouvez également entrer l'heure dans les zones de temps, ou la sélectionner dans la liste déroulante. Notez que lorsque vous entrez l'heure, le curseur gauche de temps se déplace en conséquence.  
  
4.  Dans la section **Filtres supplémentaires** , appliquez vos critères de filtre, puis cliquez sur **Appliquer**. Lorsque votre filtre a été créé, cliquez sur **OK**.  
  
 Un cas spécial est celui où un champ d'événement porte le même nom qu'une action. Par exemple, le nom « session_id ». Il existe plusieurs événements qui incluent un champ session_id et vous pouvez également ajouter l'action session_id. Les deux informations sont collectées, mais la grille d'affichage du Générateur de profils d'événements étendus utilise la logique suivante.  
  
-   Une seule copie de la colonne (session_id dans ce cas) est affichée dans la grille.  
  
-   Si les champs et l'action existent dans les données, la valeur du champ est affichée.  
  
-   Si seul le champ ou l'action existe dans les données, le champ ou l'action est affiché.  
  
-   Si ni l'action ni le champ existent, NULL est affiché.  
  
##  <a name="Search"></a> Rechercher du texte dans les colonnes  
  
1.  Ouvrez un fichier .XEL pour consulter les résultats de trace.  
  
    > [!NOTE]  
    >  Vous pouvez également cliquer avec le bouton droit sur le nom de session, puis sélectionner **Surveiller les données actives**.  
  
2.  Dans la barre d'outils événements étendus, cliquez sur le bouton **Rechercher** .  
  
3.  Dans la boîte de dialogue **Rechercher dans les événements étendus** , dans la zone **Rechercher** , entrez le texte que vous souhaitez rechercher.  
  
     Vous pouvez sélectionner l'une de vos 20 dernières chaînes de recherche dans la liste déroulante.  
  
4.  Dans la zone **Regarder dans** , sélectionnez l'emplacement dans lequel rechercher le texte spécifié dans la liste déroulante. Utilisez les options suivantes pour la recherche :  
  
    -   **Colonnes de table**. Utilisez cette option pour rechercher toutes les colonnes visibles dans la fenêtre de trace.  
  
    -   **Détails**. Utilisez cette option pour rechercher toutes les colonnes (promues et non promues) dans la fenêtre de trace qui ont été sélectionnées avant d’ouvrir le **rechercher dans les événements étendus** boîte de dialogue.  
  
    -   **\<Nom de colonne d’événement >** . Utilisez cette option pour effectuer une recherche dans une colonne d'événement spécifique dans la liste déroulante.  
  
5.  Utilisez les options suivantes pour spécifier la façon dont vous souhaitez définir la recherche :  
  
    1.  **Respecter la casse**. Utilisez cette option pour afficher les résultats de la recherche pour le texte que vous avez entré dans la zone **Rechercher** et qui correspondent par le contenu et par la casse.  
  
    2.  **Mot entier**. Utilisez cette option pour n'afficher que les résultats de la recherche du texte que vous avez entré et qui correspondent à des mots entiers.  
  
    3.  **Rechercher vers le haut**. Utilisez cette option pour effectuer la recherche depuis l'emplacement du curseur jusqu'au début des résultats.  
  
    4.  **Utilisation**. Utilisez cette option pour interpréter les caractères spéciaux et les expressions régulières que vous avez entrés dans la zone **Rechercher** . Les caractères spéciaux incluent les caractères génériques (*) et (?) pour représenter un ou plusieurs caractères. Les expressions régulières sont des notations spéciales utilisées pour définir des modèles de texte recherché.  
  
6.  Cliquez sur **Suivant** pour rechercher le texte suivant que vous avez entré dans la zone **Rechercher** .  
  
##  <a name="ChangeDisplay"></a> Modifier les paramètres d’affichage  
 Vous pouvez enregistrer les informations sur la colonne (ordre des colonnes, colonne de fusion et largeur de colonne) et les informations de filtre d'un résultat de trace dans un fichier de paramètres d'affichage des événements étendus (fichier .viewsetting). Après avoir enregistré le fichier, vous pouvez l'appliquer à vos résultats de trace pour modifier la vue.  
  
#### <a name="to-change-the-display-settings"></a>Pour modifier les paramètres d'affichage  
  
1.  Ouvrez un fichier .XEL pour consulter les résultats de trace.  
  
    > [!NOTE]  
    >  Vous pouvez également cliquer avec le bouton droit sur le nom de session, puis sélectionner **Surveiller les données actives**.  
  
2.  Dans la fenêtre de résultats de trace, dans la barre d'outils ou dans le menu Événements étendus, sélectionnez **Paramètres d'affichage**.  
  
3.  Dans la liste déroulante, sélectionnez l'une des options suivantes :  
  
    -   **Enregistrer sous**. Enregistrez les informations de colonne et de filtre d'un résultat de trace dans un fichier .viewsetting.  
  
    -   **Ouvrir**. Ouvrez un fichier .viewsetting existant.  
  
    -   **Ouvrir un fichier récent**. Ouvrez un fichier .viewsetting enregistré récemment.  
  
  
