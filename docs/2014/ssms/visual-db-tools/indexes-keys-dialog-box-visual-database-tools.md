---
title: Index et des clés de la boîte de dialogue (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65539
- vdt.ppg.indexeskeys
ms.assetid: 9e4060ba-80c3-468f-bccb-e12e99f672c2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f0244530672e9db4a43f3dbe80f0c67cc86f8a67
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52806941"
---
# <a name="indexes-and-keys-dialog-box-visual-database-tools"></a>Index et clés, boîte de dialogue (Visual Database Tools)
  Utilisez cette boîte de dialogue pour créer ou modifier des index, des clés primaires et des clés uniques. Pour y accéder, ouvrez la définition de table pour la table possédant l’index ou la clé, cliquez avec le bouton droit sur la grille de définition de table et cliquez sur **Index/Clés**.  
  
> [!NOTE]  
>  Si la table est publiée pour réplication, vous devez apporter vos modifications au schéma à l’aide de l’instruction Transact-SQL [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) ou de SMO (SQL Server Management Objects). Lorsque les modifications sont apportées au diagramme à l’aide du Concepteur de tables ou du Concepteur de diagrammes de base de données, celui-ci tente d’abandonner la table et de la recréer. Toutefois, il est impossible d'abandonner les objets publiés, par conséquent les modifications du schéma échoueront.  
  
## <a name="options"></a>Options  
 **Clé ou index Primary/Unique sélectionné**  
 Répertorie les clés primaires ou uniques et les index existants. Sélectionnez un élément pour afficher ses propriétés dans la partie droite de la grille. Si la liste est vide, aucune propriété n'est définie pour la table.  
  
 **Ajouter**  
 Crée une nouvelle clé primaire ou unique ou un nouvel index.  
  
 **Supprimer**  
 Supprime la clé ou l’index sélectionné dans la liste **Clé ou index Primary/Unique sélectionné** .  
  
 **Catégorie Général**  
 Développée, elle affiche les propriétés **Colonnes**, **Est unique**et **Type**.  
  
 **Colonnes**  
 Répertorie les ordres de tri choisis pour les colonnes de la clé ou de l'index, et donne accès à une boîte de dialogue permettant de définir les ordres de tri. Pour afficher la boîte de dialogue, cliquez sur **Colonnes**, puis sur le bouton de sélection (...) qui apparaît à droite du champ de propriété.  
  
 **Est unique**  
 Indique si les données entrées dans cet index ou cette clé doivent être uniques. Cette option n'est pas disponible pour les index XML.  
  
 **Type**  
 Spécifie si l’élément sélectionné dans la liste **Clé ou index Primary/Unique sélectionné** est une clé unique, une clé primaire ou un index. Pour les clés primaires, ce champ est en lecture seule.  
  
 **Catégorie Identité**  
 Développée, elle affiche les champs de propriété de **Nom** et **Description**.  
  
 **Nom**  
 Indique le nom de la clé ou de l'index. Lorsqu'un nouvel index ou une nouvelle clé sont créés, ils obtiennent un nom par défaut basé sur la table affichée dans la fenêtre active du Concepteur de tables. Vous pouvez modifier le nom à tout moment.  
  
 **Description**  
 Fournit un endroit auquel décrire la clé ou l'index. Pour écrire une description plus détaillée, cliquez sur **Description**, puis sur le bouton de sélection **(...)** qui apparaît à droite du champ de propriété. Vous obtiendrez une zone d'écriture plus large.  
  
 **Catégorie Concepteur de tables**  
 Développée, elle affiche des informations pour **Créer comme Clustered**.  
  
 **Créer comme Clustered**  
 Rend la clé ou l'index cluster. Un seul index cluster est autorisé par table. Les données contenues dans la table sont stockées dans l'ordre de l'index cluster. Pour plus d’informations, consultez [Créer des index cluster](../../relational-databases/indexes/indexes.md) et [Créez des index non-cluster](../../relational-databases/indexes/create-nonclustered-indexes.md).  
  
 **Spécification de l'espace de données**  
 Développée, elle affiche des informations pour **(Type d’espace de données)**, **Nom du schéma de partition ou du groupe de fichiers**et **Liste des colonnes de partition**.  
  
 **(Type d’espace de données)**  
 Indique si cet index ou cette clé appartiennent à un groupe de fichiers ou à un schéma de partition.  
  
 **Nom du schéma de partition ou du groupe de fichiers**  
 Affiche le nom du groupe de fichiers ou du schéma de partition dans lequel il est stocké.  
  
 **Liste des colonnes de partition**  
 Affiche une liste avec la virgule comme séparateur des colonnes qui participent à la fonction de la colonne de partition. Non disponible si Groupe de fichiers est sélectionné dans le champ **(Type d’espace de données)** .  
  
 **Spécification du remplissage**  
 Développée, elle affiche des informations sur les options **Taux de remplissage** et **Index Pad**.  
  
 **Taux de remplissage**  
 Spécifie le pourcentage des pages de niveau feuille de l'index que le système peut remplir. Lorsqu'une page est pleine, le système doit fractionner les pages pour ajouter de nouvelles données, ce qui affaiblit les performances.  
  
-   La valeur 100 signifie que les pages seront entières et occuperont un espace de stockage minimal. Ce paramètre ne doit être utilisé que lorsqu'aucune modification ne sera apportée aux données, par exemple dans un tableau en lecture seule.  
  
-   Une valeur inférieure laisse davantage d'espace vide sur les ensembles de données, ce qui réduit le besoin de les fractionner à mesure que la taille des index augmente, mais nécessite plus d'espace de stockage.  
  
 **Index Pad**  
 Indique si, quand la taille des pages intermédiaires de cet index augmente, elles obtiennent le même pourcentage d’espace vide (remplissage) que celui qui est spécifié dans l’option **Taux de remplissage** .  
  
 **Ignorer les clés dupliquées**  
 Contrôle ce qui se produit lorsqu'une ligne dont la valeur de clé équivaut à la valeur d'une clé existante est insérée pendant une opération d'insertion en bloc. Si vous choisissez :  
  
-   **Oui** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] émet un avertissement, ignore la ligne entrante incriminée et tente d’insérer les lignes restantes.  
  
-   **Non** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] affiche un message d’erreur et restaure l’intégralité de l’opération d’insertion en bloc.  
  
 **Colonnes incluses**  
 Affiche une liste avec la virgule comme séparateur des noms de toutes les colonnes constituant la clé d'index. Les colonnes de sous-clés ne peuvent être spécifiées que pour des index non-cluster. Cette propriété est masquée pour les index XML.  
  
 **Est désactivé**  
 Indique si cet index est désactivé. Il s’agit d’une propriété en lecture seule. Cette propriété n’a la valeur **Oui** que si l’index a été désactivé hors de Visual Database Tools.  
  
 **Est une clé de texte intégral**  
 Spécifie si cet index est une clé de texte intégral. Pour plus d'informations sur les clés de texte intégral, consultez la documentation en ligne de SQL Server. Cette propriété est masquée pour les index XML.  
  
 **Verrouillage de page autorisé**  
 Spécifier si le verrouillage au niveau des pages est autorisé dans cet index. L'autorisation ou non du verrouillage au niveau de la page affecte les performances de la base de données. Il est recommandé de choisir le paramètre **Oui**.  
  
 **Recalculer les statistiques**  
 Spécifie si le [!INCLUDE[ssDE](../../includes/ssde-md.md)] sous-jacent calcule de nouvelles statistiques une fois l'index créé. Le recalcul des statistiques ralentit la génération d'index, mais améliorera très probablement les performances des requêtes.  
  
 **Verrouillage de ligne autorisé**  
 Spécifier si le verrouillage au niveau des lignes est autorisé dans cet index. L'autorisation ou non du verrouillage au niveau de la ligne affecte les performances de la base de données. Il est recommandé de choisir le paramètre **Oui**.  
  
## <a name="see-also"></a>Voir aussi  
 [Contraintes uniques et les contraintes Check](../../relational-databases/tables/unique-constraints-and-check-constraints.md)   
 [Contraintes de clé primaire et de clé étrangère](../../relational-databases/tables/primary-and-foreign-key-constraints.md)  
  
  
