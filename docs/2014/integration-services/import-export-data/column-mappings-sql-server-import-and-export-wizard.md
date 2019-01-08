---
title: Mappage de colonnes (Assistant Importation et Exportation SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.columnmapandtransform.f1
ms.assetid: eadc54a6-f936-4ffc-91d7-fbfd2bdcab93
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 221fdaaeae61b3005fbbe0088ce4270fd4b6c2b5
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52782671"
---
# <a name="column-mappings-sql-server-import-and-export-wizard"></a>Mappage de colonnes (Assistant Importation et exportation SQL Server)
  Utilisez le **mappages de colonnes** boîte de dialogue pour modifier les paramètres de transformation.  
  
> [!NOTE]  
>  Vous n'êtes pas obligé de copier toutes les colonnes d'une table lorsque vous sélectionnez l'option de copie de table. Sélectionnez  **\<ignorer >** dans le **Destination** colonne de cette boîte de dialogue pour les colonnes que vous souhaitez ignorer.  
  
 Pour en savoir plus sur cet Assistant, consultez [Assistant Importation et Exportation SQL Server](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Pour en savoir plus sur les options de démarrage de l’Assistant, ainsi que les autorisations requises pour exécuter l’Assistant avec succès, consultez [exécuter le SQL Server Assistant Importation et exportation](start-the-sql-server-import-and-export-wizard.md).  
  
 La fonction de l'Assistant Importation et Exportation SQL Server est de copier des données d'une source vers une destination. L'Assistant peut également créer une base de données de destination et des tables de destination à votre intention. Toutefois, si vous devez copier plusieurs tables ou bases de données, ou autres types d'objets de bases de données, vous devez plutôt utiliser l'Assistant Copie de base de données. Pour plus d'informations, consultez [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Options  
 **Source**  
 Identifie la table, la vue ou la requête source sélectionnée.  
  
 **Destination**  
 Identifie la table, la vue ou la requête de destination sélectionnée.  
  
 **Créer la table/le fichier de destination**  
 Indiquez si la table de destination doit être créée si elle n'existe pas.  
  
 **Supprimer des lignes dans la table/le fichier de destination**  
 Indiquez si les données d'une table existante doivent être effacées avant d'en charger de nouvelles.  
  
 **Ajouter des lignes à la table/au fichier de destination**  
 Indiquez si les nouvelles données doivent être ajoutées à la suite des données déjà présentes dans une table existante.  
  
 **Modifier SQL**  
 Utilisez l’instruction par défaut dans le **instruction SQL Create Table** boîte de dialogue zone ou modifiez-la en fonction de vos besoins. Si vous la modifiez, vous devez également effectuer les modifications associées au mappage de table.  
  
 **Supprimer et recréer la table de destination**  
 Choisissez cette option pour remplacer la table de destination. Cette option est disponible uniquement lorsque vous faites appel à l'Assistant pour créer la table de destination. La table de destination est uniquement supprimée et recréée si vous enregistrez le package créé par l'Assistant, puis exécutez de nouveau le package.  
  
 **Activer l’insertion d’identité**  
 Permet d'insérer des valeurs d'identité des données source dans une colonne d'identité de la table de destination. Par défaut, la colonne d'identité de destination ne permet pas cela.  
  
 **Mappages**  
 Affiche la manière dont chaque colonne dans la source de données est mappée à une colonne dans la destination.  
  
 Cette liste présente les colonnes suivantes :  
  
 **Source**  
 Affiche chaque colonne source pour laquelle vous voulez définir des paramètres de transformation.  
  
 **Destination**  
 Spécifiez si vous voulez ignorer une colonne pendant la copie. Vous pouvez copier uniquement un sous-ensemble de colonnes en sélectionnant  **\<ignorer >** dans cette colonne pour les colonnes que vous souhaitez ignorer. Avant de mapper les colonnes, vous devez ignorer toutes les colonnes qui ne seront pas mappées.  
  
 **Type**  
 Sélectionnez un type de données pour la colonne.  
  
 **Nullable**  
 Spécifiez si une colonne peut contenir une valeur NULL.  
  
 **Taille**  
 Spécifiez le nombre de caractères dans la colonne.  
  
 **Précision**  
 Spécifiez la précision des données affichées en indiquant le nombre de chiffres.  
  
 **Échelle**  
 Spécifiez l'échelle des données affichées en indiquant le nombre de décimales.  
  
  
