---
title: Mappages de DataAdapter, DataTable et DataColumn
description: Décrit comment configurer DataTableMappings et ColumnMappings pour un DataAdapter.
ms.date: 11/30/2020
dev_langs:
- csharp
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: e8b2f84fbbf888fc67cdb8f945d7f0c887c14eaa
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2020
ms.locfileid: "96772257"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>Mappages de DataAdapter, DataTable et DataColumn

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Un <xref:Microsoft.Data.SqlClient.SqlDataAdapter> contient une collection de zéro ou plusieurs objets <xref:System.Data.Common.DataTableMapping> dans sa propriété <xref:System.Data.Common.DataAdapter.TableMappings%2A>. Un **DataTableMapping** fournit un mappage principal entre les données retournées depuis une requête sur une source de données et un objet <xref:System.Data.DataTable>. Le nom du **DataTableMapping** peut être passé à la place du nom de la **DataTable** à la méthode <xref:System.Data.Common.DbDataAdapter.Fill%2A> du **DataAdapter**. L’exemple suivant crée un **DataTableMapping** nommé **AuthorsMapping** pour la table **Authors**.

```csharp
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");
```

Un **DataTableMapping** vous permet d’utiliser des noms de colonne d’une **DataTable** différents de ceux de la base de données. Le **DataAdapter** utilise le mappage pour faire correspondre les colonnes quand la table est mise à jour.

> [!NOTE]
> Si vous ne spécifiez pas un **TableName** ni un nom de **DataTableMapping** lors de l’appel de la méthode **Fill** ou **Update** du **DataAdapter**, le **DataAdapter** recherche un **DataTableMapping** nommé « Table ». Le **TableName** du **DataTable** est « Table » si ce **DataTableMapping** n’existe pas. Vous pouvez spécifier un **DataTableMapping** par défaut en créant un **DataTableMapping** avec le nom « Table ».

L’exemple de code suivant crée un **DataTableMapping** (de l’espace de noms <xref:System.Data.Common>) et en fait le mappage par défaut pour le **DataAdapter** spécifié en le nommant « Table ». L’exemple mappe ensuite les colonnes de la première table du résultat de la requête (la table **Customers** de la base de données **Northwind**) à un ensemble de noms plus conviviaux dans la table **Northwind Customers** du <xref:System.Data.DataSet>. Pour les colonnes qui ne sont pas mappées, le nom de la colonne de la source de données est utilisé.

[!code-csharp[SqlDataAdapter_TableMappings#1](~/../sqlclient/doc/samples/SqlDataAdapter_TableMappings.cs#1)]

Dans des situations plus avancées, vous pouvez décider que vous voulez que le même **DataAdapter** prenne en charge le chargement de différentes tables avec des mappages différents. Pour cela, ajoutez des objets **DataTableMapping** supplémentaires.

Quand une instance d’un **DataSet** et un nom de **DataTableMapping** sont passés à la méthode **Fill**, si un mappage de ce nom existe déjà, il est utilisé ; sinon une **DataTable** de ce nom est utilisée.

Les exemples suivants créent un **DataTableMapping** avec le nom **Customers** et **BizTalkSchema** comme nom de la **DataTable**. L’exemple mappe alors les lignes retournées par l’instruction SELECT à la **DataTable** **BizTalkSchema**.

[!code-csharp[SqlDataAdapter_TableMappings#2](~/../sqlclient/doc/samples/SqlDataAdapter_TableMappings.cs#2)]

> [!NOTE]
> Si un nom de colonne source n’est pas fourni pour un mappage de colonnes, les noms par défaut sont générés automatiquement. Le mappage de colonnes reçoit le nom incrémentiel par défaut **SourceColumn** *N*, en commençant par **SourceColumn1**, si un nom de colonne source n’est pas fourni pour un mappage de colonnes.

> [!NOTE]
> Si un nom de table source n’est pas fourni pour un mappage de tables, les noms par défaut sont générés automatiquement. Le mappage de tables reçoit le nom incrémentiel par défaut **SourceTable** *N*, en commençant par **SourceTable1**, si un nom de table source n’est pas fourni pour un mappage de tables.

> [!NOTE]
> Nous vous recommandons d’éviter la convention de nommage **SourceColumn** *N* pour un mappage de colonnes ou **SourceTable** *N* pour un mappage de tables, car le nom que vous fournissez peut être en conflit avec un nom de mappage de colonnes par défaut existant dans la **ColumnMappingCollection** ou avec un nom de mappage de tables dans la **DataTableMappingCollection**. Si le nom fourni existe déjà, une exception sera levée.

## <a name="handle-multiple-result-sets"></a>Gérer plusieurs jeux de résultats

Si votre **SelectCommand** retourne plusieurs tables, **Fill** génère automatiquement des noms de table avec des valeurs incrémentielles pour les tables dans le **DataSet**, en commençant par le nom de table spécifié et en continuant sous la forme **TableName** *N*, en commençant par **TableName1**. Vous pouvez utiliser les mappages de tables pour mapper le nom de table généré automatiquement à un nom que vous voulez spécifier pour la table dans le **DataSet**. Par exemple, pour une **SelectCommand** qui retourne deux tables, **Customers** et **Orders**, effectuez l’appel suivant à **Fill**.

```csharp
adapter.Fill(customersDataSet, "Customers");
```

Deux tables sont créées dans le **DataSet** : **Customers** et **Customers1**. Vous pouvez utiliser les mappages de tables pour faire en sorte que la deuxième table soit nommée **Orders** au lieu de **Customers1**. Pour cela, mappez la table source de **Customers1** à la table **Orders** du **DataSet**, comme le montre l’exemple suivant.

[!code-csharp[SqlDataAdapter_TableMappings#3](~/../sqlclient/doc/samples/SqlDataAdapter_TableMappings.cs#3)]

## <a name="see-also"></a>Voir aussi

- [DataAdapters et DataReaders](dataadapters-datareaders.md)
- [Récupération et modification de données dans ADO.NET](retrieving-modifying-data.md)
- [Microsoft ADO.NET pour SQL Server](microsoft-ado-net-sql-server.md)
