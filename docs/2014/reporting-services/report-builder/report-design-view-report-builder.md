---
title: Mode Création de rapport (Générateur de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "10440"
- "10426"
- "10439"
- "10434"
- "10438"
- "10436"
helpviewer_keywords:
- reports, creating
- user interface
- overview of Report Builder
ms.assetid: 1544472c-2803-448d-af52-e901cb457a00
caps.latest.revision: 20
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 64398eaa537e6413f5a55bedb0aa683143047aac
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043309"
---
# <a name="report-design-view-report-builder"></a>Vue Conception de rapport (Générateur de rapports)
  La fenêtre du Générateur de rapports vise à vous permettre d'organiser facilement vos ressources de rapport et à générer rapidement les rapports dont vous avez besoin. L'aire de conception se trouve au centre de la fenêtre, avec au-dessus le ruban, à gauche le volet Données du rapport, en dessous le volet Regroupement et à droite le volet Propriétés, ainsi que la bibliothèque de parties de rapports. L'aire de conception est l'espace où vous ajoutez et organisez vos éléments de rapport. Le ruban organise les éléments de menu traditionnels en catégories faciles à repérer et à utiliser. Les volets vous permettent d'ajouter, de sélectionner et d'organiser vos ressources de rapport et de modifier les propriétés des éléments de rapport.  
  
 ![ReportDesignView](../media/reportdesignview.gif "ReportDesignView")  
  
##  <a name="Ribbon"></a> Ruban  
 Le ruban a été conçu pour vous permettre de trouver rapidement les commandes dont vous avez besoin pour effectuer une tâche. Les commandes sont organisées en groupes logiques, qui sont rassemblées sous des onglets. Chaque onglet concerne un type d'activité, par exemple l'insertion d'éléments de rapport ou la mise en forme de texte.  
  
 En mode création de rapport, le ruban est constitué des onglets suivants : Dossier de base, Insérer et Affichage. Si vous ne parvenez pas à trouver une tâche sur le ruban, certains groupes du ruban sont associés à une boîte de dialogue que vous pouvez ouvrir en cliquant sur la flèche située dans la partie inférieure droite du groupe. Vous ne pouvez pas réduire ou supprimer le ruban, ni le remplacer par des barres d'outils et des menus.  
  
 En mode exécution, le ruban n’a qu’un seul onglet, **exécuter**.  
  
### <a name="home-tab"></a>Onglet Dossier de base  
 L'onglet Dossier de base regroupe des commandes couramment utilisées centrées sur l'apparence des éléments contenus dans votre rapport. Sous l'onglet Dossier de base, vous avez accès à des commandes relatives à l'exécution, aux polices, aux paragraphes, aux bordures, aux nombres et à la disposition. Lorsque vous cliquez sur un élément de l'onglet, l'élément sélectionné dans l'aire de conception change. Lorsque vous cliquez sur **exécuter**, le rapport est rendu en HTML afin que vous pouvez voir comment le contenu du rapport s’affiche lors de la publication, et vous voyez l’onglet exécuter remplace l’onglet Accueil. L'onglet Dossier de base est l'onglet qui s'affiche par défaut lorsque vous créez initialement un rapport.  
  
### <a name="insert-tab"></a>Onglet Insérer  
 L'onglet Insérer regroupe des commandes couramment utilisées pour ajouter des éléments de rapport au rapport. Sous l'onglet Insérer, vous pouvez ajouter un tableau, une matrice, un graphique ou une carte à l'aide d'Assistants. Vous pouvez également ajouter ces éléments sans Assistant et ajouter d'autres éléments de rapport (par exemple, des graphiques sparkline, indicateurs, zones de texte, images, rectangles, sous-rapports, en-têtes et pieds de page de rapport).  
  
 En cliquant sur **parties de rapports** sur l’insertion onglet s’ouvre à la bibliothèque de parties de rapport. Recherchez des parties de rapports enregistrées sur un serveur de rapports. Pour plus d’informations, consultez [Publication de parties de rapports &#40;Générateur de rapports et SSRS&#41;](../report-parts-report-builder-and-ssrs.md).  
  
 Après avoir inséré un élément, le Générateur de rapports bascule automatiquement vers l'onglet Dossier de base.  
  
### <a name="view-tab"></a>Onglet Affichage  
 L'onglet Affichage regroupe des commandes qui permettent de contrôler le contenu de la fenêtre du Générateur de rapports. Modifiez les options d'affichage de la règle et des volets Regroupement, Données du rapport et Propriétés.  
  
### <a name="run-tab"></a>Onglet Exécuter  
 Lorsque vous cliquez sur **exécuter** sous l’onglet Accueil, vous exécutez un aperçu du rapport dans la visionneuse HTML, et vous voyez l’onglet exécuter remplace l’onglet Accueil.  
  
 L'onglet Exécuter regroupe des commandes que vous pouvez utiliser une fois le rapport rendu. Vous pouvez imprimer le rapport, parcourir les pages du rapport, exporter le rapport dans un autre format de fichier, afficher l'Explorateur de documents ou les paramètres (si le rapport en possède), et rechercher des éléments dans le rapport. Pour plus d’informations, consultez [l’aperçu de votre rapport en Mode exécution](#RunMode).  
  
 Pour revenir en mode Création, de rapports à le **exécuter** , cliquez sur **conception**.  
  
  
##  <a name="RptDesignSurface"></a> Aire de conception de rapport  
 L'aire de conception de rapport du Générateur de rapports est la principale zone de travail pour concevoir vos rapports. Pour placer des éléments de rapport, tels que des régions de données, des sous-rapports, des zones de texte, des images, des rectangles et des lignes dans votre rapport, vous devez les ajouter en les faisant glisser du ruban ou de la bibliothèque de parties de rapports vers l'aire de conception. À partir de là, vous pouvez ajouter des groupes, des expressions, des paramètres, des filtres, des actions, une visibilité et une mise en forme à vos éléments de rapport.  
  
 Vous pouvez également modifier les éléments suivants :  
  
-   les propriétés de corps du rapport, telles que la bordure et la couleur de remplissage, en cliquant avec le bouton droit sur la zone blanche de l’aire de conception, en dehors de tout élément de rapport, puis en cliquant sur **Propriétés du corps**;  
  
-   les propriétés d’en-tête et de pied de page, telles que la bordure et la couleur de remplissage, en cliquant avec le bouton droit sur la zone blanche de l’aire de conception dans la zone d’en-tête ou de pied de page, en dehors de tout élément de rapport, puis en cliquant sur **Propriétés d’en-tête** ou **Propriétés du pied de page**;  
  
-   Les propriétés du rapport lui-même, telles que mise en page, en cliquant sur la zone bleue autour de l’aire de conception en cliquant sur **propriétés de rapport**.  
  
-   les propriétés des éléments de rapport en cliquant dessus avec le bouton droit, puis en cliquant sur **Propriétés**.  
  
> [!NOTE]  
>  Si vous faites glisser un champ du volet Données du rapport directement vers l'aire de conception de rapport au lieu de le placer dans une région de données telle qu'un tableau ou un graphique, lors de l'exécution du rapport, vous voyez s'afficher uniquement la première valeur des données dans ce champ.  
  
 Pour plus d’informations sur l’utilisation du clavier pour manipuler des éléments sur l’aire de conception, consultez [Raccourcis clavier &#40;Générateur de rapports&#41;](keyboard-shortcuts-report-builder.md).  
  
### <a name="design-surface-size-and-print-area"></a>Taille et zone d'impression de l'aire de conception  
 La taille de l'aire de conception peut être différente de la zone d'impression de taille de page que vous spécifiez pour imprimer le rapport. Le fait de modifier la taille de l'aire de conception ne modifie pas la zone d'impression de votre rapport. Quelle que soit la taille que vous définissez pour la zone d'impression de votre rapport, la taille globale de l'aire de conception ne change pas. Pour plus d’informations, consultez [Comportements de rendu &#40;Générateur de rapports et SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  Pour afficher la règle, sous l’onglet **Affichage**, cochez la case **Règle**.  
  
  
##  <a name="ReptDataPane"></a> The Report Data Pane  
 Depuis le volet Données du rapport, vous avez la possibilité de définir les données et les ressources de rapport dont vous avez besoin pour un rapport avant de concevoir la disposition de votre rapport. Vous pouvez, par exemple, y ajouter des sources de données, des datasets, des champs calculés, des paramètres de rapport et des images.  
  
 Après avoir ajouté des éléments dans le volet Données du rapport, faites glisser des champs vers des éléments de rapport dans l'aire de conception afin de déterminer où apparaissent les données dans le rapport.  
  
 Vous pouvez également faire glisser des champs prédéfinis du volet Données du rapport vers l'aire de conception de rapport. Une fois le rendu effectué, ces champs fournissent des informations sur les rapports, notamment le nom du rapport, le nombre total de pages qu'il contient et le numéro de la page affichée.  
  
 Certains éléments sont ajoutés automatiquement au volet Données du rapport lorsque vous effectuez un ajout dans l'aire de conception de rapport. Par exemple, si vous ajoutez une partie de rapport à partir de la bibliothèque de parties de rapports, et si la partie de rapport est une région de données, le dataset est ajouté automatiquement au volet Données du rapport. Pour plus d’informations, consultez [Parties de rapports et datasets dans le Générateur de rapports](../report-data/report-parts-and-datasets-in-report-builder.md). En outre, si vous incorporez une image dans votre rapport, elle est ajoutée au dossier Images dans le volet Données du rapport.  
  
> [!NOTE]  
>  Vous pouvez utiliser le bouton **Nouveau** pour ajouter un nouvel élément au volet Données du rapport. Vous pouvez ajouter au rapport plusieurs datasets issus d'une même source de données ou de différentes sources de données. Vous pouvez ajouter des datasets partagés à partir du serveur de rapports. Pour ajouter un nouveau dataset à partir de la même source de données, cliquez avec le bouton droit sur une source de données, puis cliquez sur **Ajouter un dataset**.  
  
 Pour plus d'informations sur les éléments du volet Données du rapport, consultez les rubriques suivantes :  
  
-   [Fonctions globales intégrées et les références des utilisateurs &#40;rapport Générateur et SSRS&#41;](../report-design/built-in-collections-built-in-globals-and-users-references-report-builder.md)  
  
-   [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)  
  
-   [Images &#40;rapport Générateur et SSRS&#41;](../report-design/images-report-builder-and-ssrs.md)  
  
-   [Connexions de données, sources de données et chaînes de connexion dans le Générateur de rapports](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
  
-   [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
-   [Collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
  
  
##  <a name="ReptPartGallery"></a> Bibliothèque de parties de rapports  
 La façon la plus simple de créer un rapport est de rechercher une partie de rapport existante, par exemple un tableau ou un graphique, sur le serveur de rapports ou un serveur de rapports intégré à un site SharePoint. Vous recherchez des parties de rapports à ajouter à votre rapport dans la bibliothèque de parties de rapports. Vous pouvez filtrer les parties de rapports en fonction de leur nom ou d'une partie de celui-ci, de leur créateur, de la personne qui a apporté la dernière modification ou du moment de cette dernière modification, de l'emplacement de stockage ou de leur type. Par exemple, vous pourriez rechercher tous les graphiques créés la semaine dernière par l'un de vos collègues.  
  
> [!NOTE]  
>  Vous devez être connecté à un serveur pour afficher la bibliothèque de parties de rapports.  
  
 Vous pouvez afficher les résultats de la recherche sous la forme de miniatures ou d'une liste et les trier par nom, par dates de création et de modification, et par créateur. Pour plus d’informations, consultez [Publication de parties de rapports &#40;Générateur de rapports et SSRS&#41;](../report-parts-report-builder-and-ssrs.md).  
  
  
##  <a name="PropertiesPane"></a> Le volet Propriétés (Générateur de rapports)  
 Chaque élément d'un rapport, notamment le corps du rapport lui-même, les régions de données, les images et les zones de texte, est associé à des propriétés. Par exemple, la propriété BorderColor d'une zone de texte affiche la valeur de couleur de la bordure de la zone de texte et la propriété PageSize du rapport affiche la taille de page du rapport.  
  
 Ces propriétés sont affichées dans le volet Propriétés. Les propriétés du volet varient en fonction de l'élément de rapport que vous sélectionnez.  
  
 Pour afficher le volet Propriétés, sous l'onglet Affichage, dans le groupe Afficher/Masquer, cliquez sur Propriétés.  
  
### <a name="changing-property-values"></a>Modification des valeurs de propriété  
 Dans le Générateur de rapports, vous pouvez modifier les propriétés des éléments de rapport de plusieurs façons :  
  
-   en cliquant sur des boutons et des listes dans le ruban ;  
  
-   en modifiant les paramètres dans les boîtes de dialogue ;  
  
-   en modifiant les valeurs de propriété dans le volet Propriétés.  
  
 Les propriétés les plus couramment utilisées sont disponibles dans les boîtes de dialogue et dans le ruban.  
  
 En fonction de la propriété, vous pouvez définir une valeur de propriété dans une liste déroulante, taper la valeur ou cliquer sur `<Expression>` pour créer une expression.  
  
### <a name="changing-the-properties-pane-view"></a>Modification de l'affichage du volet Propriétés  
 Par défaut, les propriétés affichées dans le volet Propriétés sont classées en grandes catégories, par exemple Action, Bordure, Remplissage, Police et Général. Un ensemble de propriétés est associé à chaque catégorie. Par exemple, les propriétés suivantes sont répertoriées dans la catégorie Police : Color, FontFamily, FontSize, FontStyle, FontWeight, LineHeight et TextDecoration. Si vous préférez, vous pouvez classer toutes les propriétés répertoriées dans le volet par ordre alphabétique. Les catégories sont ainsi supprimées et toutes les propriétés sont classées par ordre alphabétique, quelle que soit la catégorie.  
  
 Trois boutons figurent en haut du volet Propriétés : Catégorie, Alphabétiser et Pages de propriétés. Cliquez sur les boutons Catégorie et Alphabétiser pour basculer entre les affichages du volet Propriétés. Cliquez sur le bouton **Pages de propriétés** pour ouvrir la boîte de dialogue des propriétés pour un élément de rapport sélectionné.  
  
  
##  <a name="GroupPane"></a> Volet de regroupement (Générateur de rapports)  
 Les groupes sont utilisés pour hiérarchiser vos données de rapport de façon visuelle et pour calculer des totaux. Vous pouvez afficher les groupes de lignes et de colonnes d'une région de données sur l'aire de conception et également dans le volet de regroupement. Le volet de regroupement comprend deux volets : Groupes de lignes et Groupes de colonnes. Lorsque vous sélectionnez une région de données, le volet de regroupement affiche tous les groupes de cette région de données sous forme de liste hiérarchique : les groupes enfants apparaissent en retrait sous leurs groupes parents.  
  
 ![Volet de regroupement pour les groupes de lignes et de colonnes imbriqués](../media/rs-basictablixdesigngroupingpanedefaultview.gif "Volet de regroupement pour les groupes de lignes et de colonnes imbriqués")  
  
 Vous pouvez créer des groupes en faisant glisser des champs du volet Données du rapport et en les plaçant sur l'aire de conception ou dans le volet de regroupement. Dans le volet de regroupement, vous pouvez ajouter des groupes parents, enfants et adjacents, modifier les propriétés de groupe et supprimer des groupes.  
  
 Le volet de regroupement s'affiche par défaut, mais vous pouvez le fermer en désactivant la case à cocher Volet de regroupement sous l'onglet Affichage. Le volet de regroupement n'est pas disponible pour les régions de données Graphique et Jauge.  
  
 Pour plus d’informations, consultez [Volet de regroupement &#40;Générateur de rapports&#41;](../report-design/grouping-pane-report-builder.md) et [Fonctionnement des groupes &#40;Générateur de rapports et SSRS&#41;](../report-design/understanding-groups-report-builder-and-ssrs.md).  
  
  
##  <a name="RunMode"></a> Affichage de l'aperçu de votre rapport en mode exécution  
 En mode création de rapport, vous n'utilisez pas des données réelles, mais une représentation des données indiquées par le nom ou l'expression du champ. Lorsque vous voulez afficher les données réelles dans le contexte du rapport que vous avez conçu, vous pouvez exécuter le rapport afin d'afficher un aperçu des données de la base de données sous-jacente dans la mise en page du rapport. Vous pouvez passer du mode Création au mode Exécution de votre rapport pour ajuster sa conception et voir les résultats immédiatement. Pour afficher un aperçu de votre rapport, cliquez sur **exécuter** dans les **vues** groupe sur le ruban.  
  
 Quand vous cliquez sur **Exécuter**, le Générateur de rapports se connecte aux sources de données du rapport, met en cache les données sur votre ordinateur, combine les données et la disposition, puis effectue le rendu du rapport dans la Visionneuse HTML. Vous pouvez exécuter le rapport aussi souvent que vous le souhaitez au fil de sa conception. Lorsque vous êtes satisfait du rapport, vous pouvez l'enregistrer sur le serveur de rapports, où les autres utilisateurs dotés des autorisations appropriées peuvent le visualiser.  
  
### <a name="running-a-report-with-parameters"></a>Exécution d'un rapport avec des paramètres  
 Lorsque vous exécutez votre rapport, celui-ci est traité automatiquement. Si le rapport contient des paramètres, ils doivent tous avoir des valeurs par défaut pour que le rapport puisse s'exécuter automatiquement. Si un paramètre ne possède pas de valeur par défaut, vous devez choisir une valeur pour chaque paramètre lors de l’exécution du rapport, puis cliquer sur **Afficher le rapport** sous l’onglet Exécuter. Pour plus d’informations, consultez [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).  
  
### <a name="print-preview"></a>Aperçu avant impression  
 Lorsque vous affichez un aperçu du rapport en mode exécution, le rapport ressemble à un rapport généré en HTML. L'aperçu n'est pas en HTML, mais la présentation et la pagination du rapport sont similaires à un affichage HTML. Vous pouvez changer la vue pour afficher le rapport tel qu'il sera imprimé en activant le mode d'aperçu avant impression. Cliquez sur le bouton **Aperçu avant impression** sous l’onglet **Exécuter** . Le rapport s'affiche comme sur une véritable page. Ce que vous voyez ressemble au résultat que produisent les extensions de rendu Image et PDF. L’aperçu avant impression n’est pas une image ni un fichier PDF, mais la disposition et la pagination du rapport sont similaires à la sortie de ces formats.  
  
  
## <a name="see-also"></a>Voir aussi  
 [Recherche, affichage et gestion des rapports &#40;Générateur de rapports et SSRS&#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Générateur de rapports dans SQL Server 2014](report-builder-in-sql-server-2016.md)  
  
  