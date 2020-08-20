---
description: Spécifier des valeurs par défaut pour les colonnes
title: Spécifier des valeurs par défaut pour les colonnes | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2020
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], defaults
- default values
ms.assetid: 64514aed-b846-407b-992e-cf813f9a1a91
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 361e98e19788f4d2c6aa921caf71e58552ee53a0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88488556"
---
# <a name="specify-default-values-for-columns"></a>Spécifier des valeurs par défaut pour les colonnes

[!INCLUDE [sqlserver2016-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa-pdw.md)]

Vous pouvez utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour spécifier une valeur par défaut qui sera entrée dans la colonne de table. Vous pouvez définir une valeur par défaut à l’aide de l’Explorateur d’objets de l’interface utilisateur ou en envoyant [!INCLUDE[tsql](../../includes/tsql-md.md)].

Si vous n’assignez aucune valeur par défaut à la colonne et que l’utilisateur laisse la colonne vide, alors :

- Si vous choisissez Oui pour Nul autorisé, la valeur NULL sera insérée dans la colonne.

- Si vous n'avez pas choisi Oui pour Nul autorisé, la colonne restera vide, mais l'utilisateur ne pourra pas enregistrer la ligne avant d'avoir fourni une valeur pour la colonne.

## <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions

Avant toute chose, tenez compte des limitations et restrictions suivantes :

- Si votre entrée dans le champ **Valeur par défaut** remplace une valeur par défaut liée (qui est affichée sans parenthèses), vous êtes invité à annuler la liaison de la valeur par défaut et à la remplacer par la nouvelle valeur par défaut.

- Pour entrer une chaîne de texte, placez la valeur entre des guillemets simples (') ; n'utilisez pas de guillemets doubles ("), car ils sont réservés pour les identificateurs entre guillemets.

- Pour entrer une valeur numérique par défaut, entrez le nombre sans guillemets autour.

- Pour entrer un objet/une fonction, entrez le nom de l'objet/fonction sans guillemets autour.

### <a name="security-permissions"></a><a name="Security"></a> Autorisations de sécurité

Les actions décrites dans cet article nécessitent l’autorisation ALTER sur la table.

## <a name="use-ssms-to-specify-a-default"></a><a name="SSMSProcedure"></a> Utiliser SSMS pour spécifier une valeur par défaut

Vous pouvez utiliser l’Explorateur d’objets pour spécifier une valeur par défaut pour une colonne de table.

### <a name="object-explorer"></a>Explorateur d’objets

1. Dans **l’Explorateur d’objets**, cliquez avec le bouton droit sur la table contenant les colonnes dont vous souhaitez modifier l’échelle et cliquez sur **Conception**.

2. Sélectionnez la colonne pour laquelle vous souhaitez spécifier une valeur par défaut.

3. Sous l'onglet **Propriétés des colonnes** , entrez la nouvelle valeur par défaut dans la propriété **Valeur ou liaison par défaut** .

   > [!NOTE]
   > Pour entrer une valeur par défaut numérique, entrez le nombre. Pour un objet ou une fonction, entrez son nom. Pour une valeur par défaut alphanumérique, entrez la valeur dans des guillemets simples.

4. Dans le menu **Fichier**, cliquez sur **Enregistrer** _nom de la table_.

## <a name="use-transact-sql-to-specify-a-default"></a><a name="TsqlProcedure"></a> Utiliser Transact-SQL pour spécifier une valeur par défaut

Plusieurs possibilités s’offrent à vous pour spécifier une valeur par défaut pour une colonne, en utilisant SSMS pour soumettre le T-SQL.

### <a name="alter-table-t-sql"></a>ALTER TABLE (T-SQL)

1. Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].

2. Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.

3. Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.

   ```sql
   CREATE TABLE dbo.doc_exz (column_a INT, column_b INT); -- Allows nulls.
   GO
   INSERT INTO dbo.doc_exz (column_a) VALUES (7);
   GO
   ALTER TABLE dbo.doc_exz
     ADD CONSTRAINT DF_Doc_Exz_Column_B
     DEFAULT 50 FOR column_b;
   GO
   ```

<!--
The following two T-SQL code examples were offered by 'nycdotnet' (Steve) via public PR 1660, Feb 2019.
-->

### <a name="create-table-t-sql"></a>CREATE TABLE (T-SQL)

```sql
    CREATE TABLE dbo.doc_exz (
      column_a INT,
      column_b INT DEFAULT 50);
```

### <a name="named-constraint-t-sql"></a>CONTRAINTE nommée (T-SQL)

```sql
    CREATE TABLE dbo.doc_exz (
      column_a INT,
      column_b INT CONSTRAINT DF_Doc_Exz_Column_B DEFAULT 50);
```

Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).
