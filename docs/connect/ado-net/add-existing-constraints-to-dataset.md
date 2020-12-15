---
title: Ajout de contraintes existantes à un DataSet
description: Décrit comment ajouter des contraintes existantes à un DataSet.
ms.date: 11/30/2020
dev_langs:
- csharp
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 9471f62c36604cb01ea78f558ac3bfbcb7f4bc01
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2020
ms.locfileid: "96772272"
---
# <a name="add-existing-constraints-to-a-dataset"></a>Ajout de contraintes existantes à un DataSet

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

La méthode <xref:System.Data.Common.DbDataAdapter.Fill%2A>du <xref:Microsoft.Data.SqlClient.SqlDataAdapter> remplit un objet <xref:System.Data.DataSet> seulement avec les colonnes et les lignes de la table d’une source de données ; bien que les contraintes soient généralement définies par la source de données, la méthode **Fill** n’ajoute pas ces informations de schéma au **DataSet** par défaut.

Pour remplir un **DataSet** avec les informations de contrainte de clé primaire existantes provenant d’une source de données, vous pouvez appeler la méthode <xref:System.Data.Common.DbDataAdapter.FillSchema%2A> du **DataAdapter** ou définir <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> du **DataAdapter** sur **AddWithKey** avant d’appeler **Fill**. Ceci va garantir que les contraintes de clé primaire dans le **DataSet** reflètent celles de la source de données.

> [!NOTE]
> Les informations de contrainte de clé étrangère ne sont pas incluses et doivent être créées explicitement.

L’ajout d’informations de schéma à un **DataSet** avant de le remplir avec les données garantit que les contraintes de clé primaire sont incluses avec les objets <xref:System.Data.DataTable> du **DataSet**. En conséquence, quand des appels supplémentaires sont effectués pour remplir le **DataSet**, les informations de colonne de clé primaire sont utilisées pour faire correspondre les nouvelles lignes de la source de données avec les lignes actuelles de chaque **DataTable** ; les données actuelles des tables sont remplacées par celles de la source de données. Sans les informations de schéma, les nouvelles lignes de la source de données sont ajoutées au **DataSet**, ce qui a pour résultat des lignes en doublon.

> [!NOTE]
> Si une colonne d’une source de données est identifiée comme étant auto-incrémentée, la méthode <xref:System.Data.Common.DbDataAdapter.FillSchema%2A> ou la méthode <xref:System.Data.Common.DbDataAdapter.Fill%2A> avec une <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> d’**AddWithKey** crée une **DataColumn** avec une propriété **AutoIncrement** définie sur `true`. Il vous faudra cependant définir vous-même les valeurs **AutoIncrementStep** et **AutoIncrementSeed**.

> [!NOTE]
> L’utilisation de **FillSchema** ou la définition de **MissingSchemaAction** sur **AddWithKey**  nécessite un traitement supplémentaire au niveau de la source de données pour déterminer les informations des colonnes de clé primaire. Ce traitement supplémentaire peut gêner la performance. Si vous connaissez les informations de clé primaire au moment du design, il est recommandé de spécifier explicitement la ou les colonnes de clé primaire afin d'atteindre une performance optimale.

L’exemple de code suivant montre comment ajouter des informations de schéma à un **DataSet** en utilisant <xref:System.Data.Common.DbDataAdapter.FillSchema%2A> :

[!code-csharp[SqlDataAdapter_FillDataSet#1](~/../sqlclient/doc/samples/SqlDataAdapter_FillDataSet.cs#1)]

L’exemple de code suivant montre comment ajouter des informations de schéma à un **DataSet** en utilisant la propriété <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> et la méthode <xref:System.Data.Common.DbDataAdapter.Fill%2A> :

[!code-csharp[SqlDataAdapter_FillDataSet#2](~/../sqlclient/doc/samples/SqlDataAdapter_FillDataSet.cs#2)]

## <a name="handling-multiple-result-sets"></a>Gestion de plusieurs jeux de résultats

Si le **DataAdapter** trouve plusieurs jeux de résultats retournés depuis la <xref:Microsoft.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, il va créer plusieurs tables dans le **DataSet**. Les tables recevront un nom incrémentiel par défaut commençant à zéro **Table** *N*, en commençant par **Table** au lieu de « Table0 ». Les tables recevront un nom incrémentiel commençant à zéro **TableName** *N* en commençant par **TableName** au lieu de « TableName0 » si un nom de table est passé comme argument à la méthode <xref:System.Data.Common.DbDataAdapter.FillSchema%2A>.

## <a name="see-also"></a>Voir aussi

- [DataAdapters et DataReaders](dataadapters-datareaders.md)
- [Récupération et modification de données dans ADO.NET](retrieving-modifying-data.md)
- [Microsoft ADO.NET pour SQL Server](microsoft-ado-net-sql-server.md)
