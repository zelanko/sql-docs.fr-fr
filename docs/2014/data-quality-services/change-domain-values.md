---
title: Modifier les valeurs de domaine | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.values.f1
ms.assetid: 8c90ab70-3aea-4eaf-a174-4159485c87d3
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: ea3b91f72b3fdd836d0b5cdb3e73122570bdbfcf
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56017230"
---
# <a name="change-domain-values"></a>Modifier les valeurs de domaine
  Cette rubrique décrit comment modifier et augmenter les métadonnées d'une base de connaissances dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Après avoir généré une connaissance par la découverte des connaissances, importé la connaissance dans la base de connaissances ou les domaines, ou basé une base de connaissances sur une autre base de connaissances, vous pouvez modifier de manière interactive les valeurs des données. La génération d'une base de connaissances non seulement bénéficie des processus assistés par ordinateur, mais vous permet aussi d'utiliser votre propre connaissance pour vérifier les valeurs des données et les modifier des manières suivantes :  
  
-   Ajoutez une valeur de domaine à la liste des valeurs, ou sélectionnez une valeur et supprimez-la de la liste.  
  
-   Modifiez l'état d'une valeur du domaine telle que définie par le processus de découverte DQS en correcte, erronée ou non valide.  
  
-   Entrez une valeur de remplacement pour une valeur qui est erronée ou non valide. Une valeur n'est pas valide si elle n'appartient pas au domaine, par exemple, si elle n'est pas conforme au type de données de domaine ou ne respecte pas une règle de domaine. Une valeur est erronée si elle appartient au domaine, mais présente une erreur de syntaxe.  
  
-   Définissez deux valeurs ou plus en tant que synonymes et modifiez la valeur de début telle que définie par le processus de découverte ; la valeur de début remplacera la valeur synonyme si la propriété **Utiliser des valeurs de début** a été définie lors de la création du domaine.  
  
-   Importez les valeurs de domaine d'un fichier Excel  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
 Pour modifier une valeur de domaine, vous devez avoir une base de connaissances et un domaine ouverts dans l'activité de gestion de l'arborescence du domaine.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Vous devez disposer du rôle dqs_kb_editor ou dqs_administrator sur la base de données DQS_MAIN pour modifier les valeurs de domaine.  
  
##  <a name="Change"></a> Modifier les valeurs de domaine  
 La table **Valeur** affiche la connaissance ajoutée à la base de connaissances pour un seul domaine. Vous pouvez sélectionner un domaine différent dans la liste des domaines à tout moment pour afficher les valeurs de ce domaine. Les colonnes du champ sont les suivantes :  
  
-   La colonne **Valeur** affiche toutes les valeurs que le processus de découverte a ajoutées au domaine sélectionné d'un champ dans l'exemple de données. Toute valeur qui est projetée comme erreur apparaîtra comme synonyme d'une valeur désignée comme correcte.  
  
-   La colonne **Type** affiche l'état de la valeur, comme déterminé par le processus de découverte. Une coche verte indique que la valeur est correcte ou corrigée ; une croix rouge indique que la valeur est erronée ; un triangle orange avec un point d'exclamation indique que la valeur n'est pas valide. Une valeur non valide ne répond pas aux exigences de données pour le domaine. Une valeur erronée peut être valide, mais n'est pas la valeur correcte pour des raisons de données.  
  
-   La colonne **Corriger vers** indique une valeur correcte dans laquelle la valeur d'origine, marquée comme erronée ou non valide, sera changée. DQS peut suggérer la valeur correcte comme résultat du processus de découverte.  
  
 Pour modifier les valeurs, procédez comme suit :  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Exécutez l’application Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l'écran d'accueil de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , ouvrez ou créez une base de connaissances. Sélectionnez **Gestion de l'arborescence du domaine** comme activité, puis cliquez sur **Ouvrir** ou **Créer**. Pour plus d’informations, consultez [Créer une base de connaissances](../../2014/data-quality-services/create-a-knowledge-base.md) ou [Ouvrir une base de connaissances](../../2014/data-quality-services/open-a-knowledge-base.md).  
  
    > [!NOTE]  
    >  La gestion de domaine est exécutée dans une page du client Data Quality Service qui contient cinq onglets pour les opérations distinctes de gestion de domaine. Ce n'est pas un processus piloté par l'Assistant ; toute opération de gestion peut être exécutée séparément.  
  
3.  Dans la **Liste des domaines** de la page **Gestion de l'arborescence du domaine** , sélectionnez le domaine dans lequel vous souhaitez modifier des valeurs, ou créez un domaine. Si vous devez créer un domaine, consultez [Créer un domaine](../../2014/data-quality-services/create-a-domain.md). Cliquez sur l'onglet **Valeurs du domaine** .  
  
4.  Affichez les valeurs que vous devez modifier dans la table **Valeur** . Pour plus d'informations, consultez [How to Display the Appropriate Values](#Display) ci-dessous.  
  
5.  Pour modifier l’état d’une valeur, effectuez les étapes suivantes :  
  
    -   **Définir les valeurs du domaine sélectionné rectifiée**: Pour modifier état d’une valeur d’erreur ou non valide en correcte, sélectionnez la valeur, puis cliquez sur le **ensemble les valeurs du domaine sélectionné rectifiée** (coche) à partir de la flèche vers le bas dans la barre d’icônes ou de la liste déroulante Type. Si la valeur erronée ou non valide est regroupée avec une valeur correcte, supprimez cette valeur après l'opération.  
  
    -   **Définir les valeurs du domaine sélectionné en tant qu’erreurs**: Pour modifier état d’une valeur à partir de correcte ou non valide en erronée, sélectionnez la valeur, puis cliquez sur le **ensemble les valeurs du domaine sélectionné en tant qu’erreurs** icône (croix) à partir de la flèche vers le bas dans la barre d’icônes ou de la liste déroulante Type. Vous pouvez entrer une correction dans la colonne **Corriger vers** , ou la laisser vide.  
  
    -   **Définir les valeurs du domaine sélectionné comme non valide**: Pour modifier les état d’une valeur de correcte ou erronée en non valide, sélectionnez la valeur, puis cliquez sur le **ensemble les valeurs du domaine sélectionné comme non valide** icône (triangle) à partir de la flèche vers le bas dans la barre d’icônes ou de la liste déroulante Type. Vous pouvez entrer une correction dans la colonne **Corriger vers** , ou la laisser vide.  
  
    -   **Correct à**: Après avoir défini une valeur comme erronée ou non valide, entrez une nouvelle valeur dans le **corriger vers** colonne. DQS ajoute une nouvelle ligne pour la valeur de remplacement, l'indique comme correcte, puis regroupe les deux valeurs. La nouvelle valeur sera affichée comme valeur de début, avec la valeur de début en gras et la valeur erronée ou non valide mise en retrait.  
  
6.  Pour indiquer les valeurs en tant que groupe de synonymes, sélectionnez plusieurs valeurs correctes, puis procédez comme suit :  
  
    -   **Définir les valeurs du domaine sélectionné en tant que synonymes**: Pour définir les synonymes, sélectionnez plusieurs valeurs qui sont corrects, puis cliquez sur le **ensemble les valeurs du domaine sélectionné en tant que synonymes** icône. DQS regroupe les valeurs et désigne l'une des valeurs comme valeur de début par laquelle les autres seront remplacées. Notez que, si deux valeurs sont regroupées, mais que l'une du groupe est erronée ou non valide, les valeurs ne sont pas des synonymes.  
  
        > [!NOTE]  
        >  Si vous sélectionnez deux valeurs ou plus dans un groupe et une autre valeur en dehors du groupe, puis les définissez comme synonymes, vous obtiendrez un message d'erreur. Après fermeture du message d'erreur, les valeurs seront définies correctement en tant que synonymes.  
  
    -   **Supprimer la relation entre les synonymes sélectionnés**: Pour annuler la désignation de synonyme de deux ou plusieurs valeurs, sélectionnez les valeurs, puis cliquez sur le **supprimer la relation entre les synonymes sélectionnés** icône. Les valeurs doivent être regroupées et doivent toutes deux être correctes pour que le dégroupement des synonymes fonctionne.  
  
    -   **Définir la valeur du domaine sélectionné en tant que valeur de début de son groupe**: Pour modifier la valeur de début du groupe, sélectionnez une valeur dans le groupe qui n’est pas défini comme valeur de début, puis cliquez sur le **définir une valeur de domaine sélectionné en tant que valeur de début de son groupe** bouton. La valeur de début est ainsi définie comme remplacement de l'autre valeur. Cette opération fonctionne uniquement si vous avez défini deux ou plusieurs valeurs qui sont un groupe et que vous souhaitez modifier la valeur désignée par DQS par la valeur de début. Notez que la valeur de début est indiquée par une ligne bleue avec la valeur en gras.  
  
7.  **Le vérificateur d’orthographe**: Si une valeur a un trait de soulignement ondulé rouge, le vérificateur d’orthographe suggère une correction de la valeur. Cliquez avec le bouton droit sur la valeur avec un trait de soulignement, puis sélectionnez une correction, le cas échéant. Le type de valeur devient (ou demeure) erroné et la correction est ajoutée à la colonne **Corriger vers** . Cliquez sur la flèche bas pour afficher les corrections proposées supplémentaires. Entrez une correction manuellement pour l'ajouter au dictionnaire du vérificateur d'orthographe et pouvoir la sélectionner comme correction. Pour plus d'informations, consultez [Use the DQS Speller](../../2014/data-quality-services/use-the-dqs-speller.md) et [Set Domain Properties](../../2014/data-quality-services/set-domain-properties.md).  
  
    > [!NOTE]  
    >  Pour utiliser le vérificateur d'orthographe, vous pouvez l'activer dans la page **Propriétés du domaine** ou, s'il est désactivé, dans la page **Propriétés du domaine** , vous pouvez cliquer sur l'icône **Activer/désactiver le vérificateur d'orthographe** dans la page **Valeurs du domaine** pour l'activer sur cette page.  
  
8.  **Ajouter une nouvelle valeur de domaine**: Cliquez pour ajouter une ligne à la fin de la table. Après avoir entré une valeur, la ligne sera replacée par ordre alphabétique et identifiée comme nouvelle entrée par un symbole précédent en étoile.  
  
9. **Importer des valeurs de domaine à partir d’Excel**: Pour ajouter de nouvelles valeurs à partir d’une feuille de calcul Excel, cliquez sur la flèche bas de la **importer des valeurs** icône, puis sélectionnez **importer des valeurs de domaine à partir d’Excel**. Entrez le nom de fichier, sélectionnez **Utiliser la première ligne comme en-tête** le cas échéant, puis cliquez sur **OK**. Pour plus d’informations, consultez [Importer des valeurs d’un fichier Excel dans un domaine](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md).  
  
10. **Importer des valeurs de projet**: Pour ajouter de nouvelles valeurs à partir d’un projet de qualité des données en cliquant sur la flèche bas de la **importer des valeurs** icône, puis en sélectionnant **importer des valeurs de projet**. Entrez le nom de fichier, sélectionnez **Utiliser la première ligne comme en-tête** le cas échéant, puis cliquez sur **OK**. Sélectionnez le projet à partir duquel vous voulez importer des valeurs, puis cliquez sur **OK**. Les valeurs importées seront affichées. Cliquez sur **Terminer**. Pour plus d'informations, consultez Importer les valeurs de projet dans un domaine.  
  
11. **Supprimer les valeurs du domaine sélectionné**: Pour supprimer une ou plusieurs valeurs existantes du domaine, sélectionnez les valeurs dans la table de valeurs, puis cliquez sur le **supprimer les valeurs du domaine sélectionné** icône. Comme une entrée DQS_NULL ne peut pas être supprimée, si vous choisissez plusieurs valeurs à supprimer et qu'une entrée DQS_NULL est l'une d'entre elles, l'opération échoue.  
  
12. Cliquez sur **Terminer** pour terminer l'activité de gestion de l'arborescence du domaine, comme décrit dans [End the Domain Management Activity](../../2014/data-quality-services/end-the-domain-management-activity.md).  
  
##  <a name="FollowUp"></a> Suivi : Après avoir modifié les valeurs du domaine  
 Après avoir modifié les valeurs de domaine, vous pouvez effectuer d'autres tâches de gestion des domaines sur le domaine, effectuer une découverte des connaissances pour ajouter des connaissances au domaine ou ajouter une stratégie de correspondance au domaine. Pour plus d’informations, consultez [Effectuer une découverte des connaissances](../../2014/data-quality-services/perform-knowledge-discovery.md), [Gestion d’un domaine](../../2014/data-quality-services/managing-a-domain.md) ou [Créer une stratégie de correspondance](../../2014/data-quality-services/create-a-matching-policy.md).  
  
##  <a name="Meaning"></a> Signification des valeurs correctes, erronées et non valides  
 Chaque valeur de la table **Valeur** de la page **Valeurs du domaine** se voit affecter un paramètre **Type** égal à **Correcte**, **Erronée**ou **Non valide**. Le type de la valeur est généré initialement par l'activité de découverte des connaissances, et vous pouvez le modifier à votre convenance. Le type final, basé sur la découverte et les modifications interactives, est généré par l'activité de nettoyage. Ces valeurs ont les significations suivantes :  
  
-   **Corriger :** Il s’agit d’une valeur qui appartient au domaine et ne dispose pas des erreurs de syntaxe. Par exemple, « Chicago » dans le champ « Ville » est une valeur correcte.  
  
-   **Erreur :** Il s’agit d’une valeur qui appartient au domaine, mais qui est une valeur incorrecte. Par exemple, « Shicago » au lieu de « Chicago » dans « Ville » est une erreur. DQS indique une valeur comme erronée s'il détecte une erreur de syntaxe et une correction associée dans le processus de découverte. Les erreurs de syntaxe incluent les fautes d'orthographe.  
  
-   **Non valide :** Il s’agit d’une valeur qui n’appartient pas au domaine et n’a pas de correction. Par exemple, la valeur « 12345 » dans un champ « Ville » n’est pas valide. DQS indique une valeur comme non valide quand elle ne respecte pas une règle de domaine.  
  
 Vous pouvez modifier manuellement le type d'une valeur en l'une des deux autres valeurs. DQS n'applique pas la sémantique de validation et d'erreur sur les opérations manuelles. Vous pouvez écrire une correction pour une valeur valide sans modifier son état. Vous pouvez désigner une valeur comme non valide même si elle respecte une règle de domaine. Vous pouvez désigner une valeur comme erronée même si le processus de découverte n'indique pas d'erreur de syntaxe. Vous pouvez également supprimer une correction d'une valeur erronée, marquée comme correcte, sans modifier son état.  
  
 Lorsque vous effectuez un nettoyage des données interactif dans la page **Gérer et afficher les résultats** de l'activité **Nettoyage** , les valeurs non valides et erronées sont incluses dans l'onglet **Non valide** de la page **Gérer et afficher les résultats** .  
  
##  <a name="Display"></a> How to Display the Appropriate Values  
 Vous pouvez modifier l'affichage comme suit :  
  
-   **Filtre** : filtrez les résultats souhaités dans la table, selon leur état, en sélectionnant celui-ci dans la liste déroulante **Filtre** .  
  
-   **Rechercher** : recherchez les données que vous souhaitez vérifier ou modifier en entrant une ou plusieurs lettres à rechercher dans la zone de texte **Rechercher** . Ces lettres apparaîtront en surbrillance chaque fois qu'elles seront présentes dans une valeur affichée.  
  
-   Cliquez sur **Afficher seulement les nouvelles valeurs** pour restreindre les valeurs affichées dans la table uniquement aux valeurs qui ont été découvertes dans la session active, pas dans les sessions précédentes.  
  
-   Cliquez sur le bouton **Développer tout** pour afficher toutes les valeurs d'un groupe de synonymes lorsque l'état actuel est réduit.  
  
-   Cliquez sur le bouton **Réduire tout** pour masquer toutes les valeurs sauf la valeur de début d'un groupe de synonymes lorsque l'état actuel est développé.  
  
-   Cliquez sur le bouton **Afficher/Masquer le panneau d'historique des modifications de valeurs du domaine** pour afficher un message d'aperçu en bas de la table de valeurs qui affiche les modifications apportées récemment à la collection des valeurs du domaine.  
  
##  <a name="Null"></a> Comment gérer les équivalents des valeurs Null  
 Chaque table des valeurs dans l'onglet **Valeurs du domaine** inclut une valeur DQS_NULL. Une valeur Null dans une source de données apparaît comme SQL_NULL dans la table des valeurs. Vous pouvez définir un ou plusieurs équivalents de valeurs Null comme synonymes de DQS_NULL. Dans ce cas, l'ensemble des valeurs Null et équivalents de valeurs Null est traité comme DQS_NULL.  
  
  
