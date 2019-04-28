---
title: Afficher les données de Session d’événement | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: ac742a01-2a95-42c7-b65e-ad565020dc49
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: befef498ab4cda12ce38a34678b78a2b5dcd278c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842883"
---
# <a name="view-event-session-data"></a>Afficher des données de session d'événements
  Cette rubrique décrit l'utilisation de l'interface utilisateur pour afficher et analyser les données d'événements étendus :  
  
-   Afficher les données cibles  
  
-   Utilisation des données  
  
## <a name="view-target-data"></a>Afficher les données cibles  
 Vous pouvez afficher les données collectées dans la cible spécifiée dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
### <a name="view-target-data"></a>Afficher les données cibles  
 Pour afficher les données cibles :  
  
1.  Dans l'Explorateur d'objets, développez **Gestion**, **Événements étendus**, **Sessions**, puis sélectionnez une session.  
  
2.  Cliquez avec le bouton droit sur le nom de la cible, puis cliquez sur **Afficher les données cibles** pour afficher les données cibles.  
  
     La fenêtre de données cibles apparaît dans la vue par défaut et affiche les données cibles.  
  
 Remarques sur l'affichage des données cibles :  
  
-   Les données cibles ne sont pas disponibles pour la cible ETW.  
  
-   Pour afficher les données ring_buffer au format XML, dans la fenêtre des données cibles, cliquez sur le lien **données cibles ring_buffer** . Le fichier ring_buffer.xml apparaît dans l'éditeur XML.  
  
-   Pour une cible event_file, affichez les données cibles du fichier (fichier .XEL) à l'aide de l'une des méthodes suivantes :  
  
    -   Utiliser un fichier -> Ouvrir dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
    -   Faites glisser le fichier dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
    -   Double-cliquez sur le fichier .XEL.  
  
    -   Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], cliquez avec le bouton droit sur une session d'événements étendus en cours d'exécution et sélectionnez Afficher les données cibles.  
  
    -   [fn_xe_file_target_read_file](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql)  
  
    -   Vous pouvez afficher plusieurs fois. Fichier XEL en sélectionnant **fusionner les fichiers d’événements étendus** à partir du fichier -> Ouvrir le menu.  
  
### <a name="watching-live-data"></a>Surveiller les données actives  
 Vous pouvez surveiller les données actives à mesure qu'elles sont capturées.  
  
-   Dans l'Explorateur d'objets, développez les nœuds **Gestion**, **Événements étendus**, puis **Sessions** .  
  
-   Cliquez avec le bouton droit sur le nom de session, puis cliquez sur **Surveiller les données actives** pour commencer à afficher les données de suivi.  
  
     Les colonnes d'affichage par défaut sont **Nom de l'événement** et **TimeStamp**.  
  
     Pour ajouter d'autres colonnes à la fenêtre de trace, cliquez sur le bouton **Choisir les colonnes** dans la barre d'outils Événements étendus. L'onglet **Détails** affiche tous les détails de l'événement sélectionné.  
  
     Les événements sont généralement affichés en environ 30 secondes. Si vous souhaitez modifier la période de latence, vous pouvez modifier l'option **Latence maximale de répartition** dans la page **Options avancées** de la boîte de dialogue **Nouvelle session** .  
  
### <a name="to-refresh-target-data"></a>Pour actualiser les données cibles  
 L'actualisation des données cibles n'est pas prise en charge pour les cibles event_files :  
  
1.  Pour actualiser les données cibles automatiquement, cliquez avec le bouton droit sur les données cibles, sélectionnez **Intervalle d'actualisation**, puis sélectionnez l'intervalle d'actualisation dans la liste d'intervalles.  
  
2.  Pour suspendre et reprendre l'actualisation automatique, cliquez avec le bouton droit sur les données cibles, puis sélectionnez **Suspendre** ou **Reprendre**.  
  
3.  Pour actualiser les données cibles manuellement, cliquez avec le bouton droit sur les données cibles, puis sélectionnez **Actualiser**.  
  
## <a name="working-with-data"></a>Utilisation des données  
 Vous pouvez utiliser les fonctionnalités d'analyse de l'interface utilisateur Événements étendus afin d'identifier les problèmes.  
  
### <a name="details-pane"></a>Volet d'informations  
 Le volet **Détails** affiche toutes les colonnes de l'événement sélectionné, notamment les champs et les actions. Vous pouvez ajouter une colonne à la table de données cible en cliquant avec le bouton droit sur une ligne dans le volet **Détails** et en sélectionnant **Afficher la colonne dans la table**.  
  
### <a name="create-modify-or-delete-merged-columns"></a>Créer, modifier ou supprimer des colonnes fusionnées  
 Une colonne fusionnée vous permet de combiner un ensemble de champs à afficher dans une colonne unique. La colonne fusionnée affiche les données du premier champ non NULL en fonction de l'ordre dans lequel ils sont ajoutés à la liste de champs. Cela s'apparente à ce que vous voyez dans le Générateur de profils de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , où une colonne spécifique peut afficher des données différentes selon l'événement (l'exemple le plus courant est le champ TextData dans le Générateur de profils de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ). Pour obtenir un exemple, vous pouvez fusionner les champs d'instruction et de batch_text des événements sql_statement_completed et sql_batch_completed, respectivement, dans un champ nommé myStatement. Lorsque vous affichez la colonne myStatement dans la table, elle affiche les données appropriées pour l'événement associé.  
  
 Vous pouvez créer, modifier ou supprimer des colonnes fusionnées :  
  
1.  Ouvrez un fichier .XEL pour consulter les résultats de trace. (Vous pouvez également cliquer avec le bouton droit sur le nom de session, puis sélectionner **Surveiller les données actives**.)  
  
2.  Dans la fenêtre des résultats de trace, cliquez avec le bouton droit sur l'en-tête de colonne, puis sélectionnez **Choisir les colonnes**.  
  
 Pour créer une colonne fusionnée, cliquez sur **Nouveau** dans la boîte de dialogue **Choisir les colonnes** .  Dans la boîte de dialogue **Nouvelle colonne fusionnée** , sélectionnez le nom de la colonne fusionnée et sélectionnez les colonnes d'origine à inclure dans la colonne fusionnée.  
  
 Pour modifier une colonne fusionnée, sélectionnez-en une dans la boîte de dialogue **Choisir les colonnes** et cliquez sur **Modifier**. Dans la boîte de dialogue **Modifier la colonne fusionnée** , renommez la colonne fusionnée ou modifiez les colonnes d'origine à inclure dans la colonne fusionnée.  
  
 Pour supprimer une colonne fusionnée, sélectionnez-en une dans la boîte de dialogue **Choisir les colonnes** et cliquez sur **Supprimer**.  
  
### <a name="filter-results"></a>Filtrer les résultats  
 Vous pouvez afficher les résultats de trace, puis appliquer des filtres pour restreindre le nombre de résultats de trace affichés dans la fenêtre de trace. Le filtre d'affichage comprend un filtre de temps et un filtre avancé. Vous utilisez le filtre de temps pour filtrer les résultats de trace par horodatage d'un événement, et le filtre avancé pour élaborer des conditions de filtre à l'aide des actions et des champs d'événement. Il existe une relation « et » entre les filtres de temps et les filtres avancés.  
  
 Pour créer un filtre :  
  
1.  Ouvrez un fichier .XEL pour consulter les résultats de trace. (Vous pouvez également cliquer avec le bouton droit sur le nom de session, puis sélectionner **Surveiller les données actives**.)  
  
2.  Dans la fenêtre des résultats de trace, sélectionnez les résultats que vous souhaitez filtrer, puis dans la barre d'outils **Événements étendus** , cliquez sur le bouton **Filtres**.  
  
3.  Dans la boîte de dialogue **Filtres** , sélectionnez **Définir le filtre de temps** et faites glisser les barres de curseur ou modifiez le temps dans la zone d'édition pour définir le filtre de temps.  
  
4.  Dans la section **Filtres supplémentaires** , appliquez vos critères de filtre, puis cliquez sur **Appliquer**.  
  
### <a name="sort-results"></a>Trier les résultats  
 Pour trier les résultats dans l'ordre croissant ou décroissant :  
  
1.  Ouvrez un fichier .XEL pour consulter les résultats de trace. (Vous pouvez également cliquer avec le bouton droit sur le nom de session, sélectionner **Surveiller les données actives**, puis cliquer sur le bouton **Arrêter le flux de données** dans la barre d'outils.)  
  
2.  Dans la fenêtre des résultats de trace, cliquez avec le bouton droit sur l'en-tête de colonne à trier et cliquez sur **Tri croissant** ou **Tri décroissant**.  
  
 Vous pouvez également cliquer sur l'en-tête de colonne pour inverser l'ordre de tri.  
  
 Si vous avez regroupé des colonnes, le tri de la colonne ne concerne que les données du groupe.  
  
### <a name="group-results"></a>Regrouper les résultats  
 Les résultats groupés sont équivalents aux fonctionnalités de la clause `GROUP BY` dans [!INCLUDE[tsql](../includes/tsql-md.md)]. La table de données cible affiche les données regroupées et vous permet de développer/réduire les données.  
  
 Vous devez regrouper les données avant de pouvoir les agréger. Par exemple, vous pouvez regrouper sur la base de la valeur de query_hash, effectuer un tri décroissant en fonction de la durée, obtenir la durée moyenne de chaque groupe, puis effectuer un tri décroissant sur l'agrégation.  Cela génère une liste qui affiche les instructions uniques de la plus longue à la plus courte durée moyenne. Lorsque vous développez le groupe supérieur, vous pouvez voir les différentes exécutions de cette requête spécifique triées de la plus longue à la plus courte.  
  
 Vous pouvez grouper des résultats par une seule colonne ou par plusieurs colonnes.  
  
 Ouvrez un fichier .XEL pour consulter les résultats de trace. (Vous pouvez également cliquer avec le bouton droit sur le nom de session, sélectionner **Surveiller les données actives**, puis cliquer sur le bouton **Arrêter le flux de données** dans la barre d'outils.)  
  
 Pour grouper les résultats par une seule colonne, cliquez avec le bouton droit sur l'en-tête de colonne dans la fenêtre des résultats de trace et cliquez sur **Regrouper par cette colonne**. Pour annuler le regroupement, sélectionnez l'une des lignes et cliquez sur **Supprimer tous les regroupements**.  
  
 Pour regrouper les résultats par plusieurs colonnes, cliquez sur le bouton **Regroupement** dans la barre d'outils **Événements étendus** . Dans la zone **Colonnes disponibles** de la boîte de dialogue **Regroupement** , sélectionnez les colonnes à regrouper, puis déplacez-les dans la zone **Colonnes groupées** . Pour modifier l'ordre, dans la zone **Colonnes groupées** , cliquez sur les flèches haut ou bas.  
  
### <a name="aggregate-results"></a>Agréger les résultats  
 Vous pouvez afficher les résultats de trace, puis poursuivre l'analyse de vos données d'événement en agrégeant des colonnes dans les résultats. Les événements étendus prennent en charge cinq fonctions d'agrégation :  
  
-   sum  
  
-   min  
  
-   max  
  
-   average  
  
-   count  
  
 Les fonctions « sum », « min », « max » et « average » peuvent être utilisées uniquement avec les colonnes numériques. La fonction « count » correspond au nombre de valeurs non Null qui existent pour la colonne sélectionnée dans le groupe.  
  
 L'agrégation est effectuée sur un groupe ; vous devez donc regrouper les résultats avant de pouvoir exécuter l'agrégation. Pour agréger les résultats :  
  
1.  Ouvrez un fichier .XEL pour consulter les résultats de trace. (Vous pouvez également cliquer avec le bouton droit sur le nom de session, sélectionner **Surveiller les données actives**, puis cliquer sur le bouton **Arrêter le flux de données** dans la barre d'outils.)  
  
2.  Dans la barre d'outils **Événements étendus** , cliquez sur le bouton **Agrégation** . La boîte de dialogue Agrégation apparaît avec les colonnes disponibles pour l'agrégation.  
  
3.  Dans la colonne **Type d'agrégation** , sélectionnez le type d'agrégation.  
  
4.  Dans la zone **Trier l'agrégation par** , sélectionnez la colonne de tri. Sélectionnez ensuite l'ordre croissant ou décroissant.  
  
### <a name="search-for-text-in-columns"></a>Rechercher du texte dans des colonnes  
 Vous pouvez rechercher un texte dans les colonnes :  
  
1.  Ouvrez un fichier .XEL pour consulter les résultats de trace. (Vous pouvez également cliquer avec le bouton droit sur le nom de session, puis sélectionner **Surveiller les données actives**.)  
  
2.  Dans la barre d'outils **Événements étendus** , cliquez sur **Rechercher** .  
  
3.  Dans la boîte de dialogue **Rechercher dans les événements étendus** , dans la zone **Rechercher** , entrez le texte de la recherche. Vous pouvez sélectionner l'une de vos 20 dernières chaînes de recherche dans la liste déroulante.  
  
4.  Dans la zone **Regarder dans** , sélectionnez l'emplacement où vous souhaitez rechercher le texte spécifié. Utilisez les options suivantes pour la recherche :  
  
    -   Colonnes de table. Utilisez cette option pour rechercher toutes les colonnes visibles dans la fenêtre de trace.  
  
    -   Détails. Utilisez cette option pour rechercher toutes les colonnes (promues et non promues) dans la fenêtre de trace qui ont été sélectionnées avant d’ouvrir le **rechercher dans les événements étendus** boîte de dialogue.  
  
    -   *Event_column_name*. Utilisez cette option pour effectuer une recherche dans une colonne d'événement spécifique dans la liste déroulante.  
  
5.  Utilisez les options suivantes pour spécifier la façon dont vous souhaitez définir la recherche :  
  
    -   Respecter la casse. Utilisez cette option pour afficher les résultats de la recherche pour le texte que vous avez entré dans la zone Rechercher et qui correspondent par le contenu et par la casse.  
  
    -   Mot entier. Utilisez cette option pour n'afficher que les résultats de la recherche du texte que vous avez entré et qui correspondent à des mots entiers.  
  
    -   Rechercher vers le haut. Utilisez cette option pour effectuer la recherche depuis l'emplacement du curseur jusqu'au début des résultats.  
  
    -   Utilisation. Utilisez cette option pour interpréter les caractères spéciaux et les expressions régulières que vous avez entrés dans la zone Rechercher. Les caractères spéciaux incluent les caractères génériques (*) et (?) pour représenter un ou plusieurs caractères. Les expressions régulières sont des notations spéciales utilisées pour définir des modèles de texte recherché.  
  
    -   Cliquez sur **Suivant** pour rechercher le texte suivant que vous avez entré dans la zone **Rechercher** .  
  
### <a name="bookmarks"></a>Signets  
 Pour retourner facilement à une ligne, vous pouvez insérer un signet dans une ou plusieurs lignes dans les données cibles. Cliquez avec le bouton droit sur une ligne pour modifier le signet. Utilisez les boutons Précédent et Suivant dans la barre d'outils **Événements étendus** pour accéder aux lignes contenant un signet.  
  
### <a name="change-display-settings"></a>Modifier les paramètres d'affichage  
 Vous pouvez enregistrer les informations sur la colonne (ordre des colonnes, colonne de fusion et largeur de colonne) et les informations de filtre d'un résultat de trace dans un fichier de paramètres d'affichage des événements étendus (fichier .viewsetting). Après avoir enregistré le fichier, vous pouvez l'appliquer à vos résultats de trace pour modifier la vue.  
  
 Pour modifier les paramètres d'affichage :  
  
1.  Ouvrez un fichier .XEL pour consulter les résultats de trace. (Vous pouvez également cliquer avec le bouton droit sur le nom de session, puis sélectionner **Surveiller les données actives**.)  
  
2.  Dans la barre d'outils **Événements étendus** , sélectionnez **Paramètres d'affichage**. Dans la liste déroulante, sélectionnez l'une des options suivantes :  
  
    -   Enregistrer sous. Enregistrez les informations de colonne et de filtre d'un résultat de trace dans un fichier .viewsetting.  
  
    -   Ouvrir. Ouvrez un fichier .viewsetting existant.  
  
    -   Ouvrir un fichier récent. Ouvrez un fichier .viewsetting enregistré récemment.  
  
### <a name="copy-or-export-trace-results"></a>Copier ou exporter les résultats de trace  
 Vous pouvez copier des cellules, des lignes et des détails dans les lignes sélectionnées de vos résultats de trace. Vous pouvez également exporter les résultats de trace comme suit :  
  
-   Fichier .XEL  
  
-   table  
  
-   Fichier .CSV  
  
 Pour copier les résultats de trace, sélectionnez une cellule ou une ou plusieurs lignes, cliquez avec le bouton droit sur **Copier** , puis sélectionnez **Cellule**, **Ligne**ou **Détails**. Les événements étendus prennent en charge la copie jusqu'à un maximum de 1 000 lignes.  
  
 Vous pouvez exporter les résultats de trace dans un fichier .XEL, une table ou un fichier .CSV en sélectionnant **Exporter vers** dans l'option de menu **Événements étendus** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
### <a name="view-a-deadlock-graph-and-query-plans"></a>Afficher un graphique d'interblocage et les plans de requête  
 Vous pouvez afficher le graphique du blocage pour **xml_deadlock_report** dans le volet Détails afin de résoudre les blocages. Vous pouvez également afficher des graphiques de plan de requête pour les événements suivants :  
  
-   query_post_compilation_showplan  
  
-   query_pre_execution_showplan  
  
-   query_post_execution_showplan  
  
 Pour afficher le graphique de blocage :  
  
-   Dans l'Explorateur d'objets, développez les nœuds **Gestion**, **Événements étendus**, puis **Sessions** .  
  
-   Cliquez avec le bouton droit sur la session qui contient l'événement de blocage configuré à afficher, puis sélectionnez **Surveiller les données actives**.  
  
-   Sélectionnez l'événement de blocage et affichez le graphique dans l'onglet **Blocage** du volet d'informations.  
  
 Pour afficher les graphiques de plan de requête :  
  
1.  Dans l'Explorateur d'objets, développez les nœuds **Gestion**, **Événements étendus**, puis **Sessions** .  
  
2.  Cliquez avec le bouton droit sur la session qui contient le graphique du plan de requête que vous souhaitez afficher (par exemple, query_post_compilation_showplan), puis sélectionnez **Surveiller les données actives**.  
  
3.  Sélectionnez l'événement du graphique de plan de requête (par exemple, query_post_compilation_showplan) et affichez le graphique dans l'onglet **Plan de requête** du le volet d'informations.  
  
  
