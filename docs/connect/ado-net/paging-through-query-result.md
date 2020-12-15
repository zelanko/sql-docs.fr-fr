---
title: Pagination sur un résultat de requête
description: Propose un exemple de visualisation des résultats d'une requête sous forme de pages de données.
ms.date: 11/30/2020
dev_langs:
- csharp
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 2de305e1069964f2d1a67b7f201578c7448d3e09
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2020
ms.locfileid: "96772185"
---
# <a name="paging-through-a-query-result"></a>Pagination sur un résultat de requête

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Ce mode d'affichage consiste à retourner les résultats d'une requête sous forme de sous-ensembles, plus petits, de données, aussi appelés pages. Cette façon de procéder est courante lorsqu'il s'agit de présenter à l'utilisateur un affichage des résultats par petits segments, plus faciles à gérer.

Le <xref:Microsoft.Data.SqlClient.SqlDataAdapter> propose une fonctionnalité permettant de retourner uniquement une page de données, via des surcharges de la méthode <xref:System.Data.Common.DbDataAdapter.Fill%2A>. Cependant, cette solution n’est pas le meilleur choix quand les résultats de la requête sont très volumineux car, si le **DataAdapter** remplit l’objet <xref:System.Data.DataTable> ou <xref:System.Data.DataSet> cible uniquement avec les enregistrements demandés, les ressources sollicitées restent les mêmes que pour retourner l’intégralité de la requête.

Pour retourner une page de données provenant d'une source de donnée sans solliciter les ressources requises pour retourner l'intégralité de la requête, spécifiez des critères supplémentaires pour votre requête afin de limiter le nombre de lignes retournées à celles qui sont requises.

Pour utiliser la méthode <xref:System.Data.Common.DbDataAdapter.Fill%2A> afin de retourner une page de données, spécifiez un paramètre **startRecord** pour le premier enregistrement de la page de données et un paramètre **maxRecords** indiquant le nombre d’enregistrements de la page de données.

## <a name="example"></a>Exemple

L’exemple de code suivant montre comment utiliser la méthode <xref:System.Data.Common.DbDataAdapter.Fill%2A> pour retourner la première page des résultats d’une requête, sachant que la page compte cinq enregistrements.

[!code-csharp[SqlDataAdapter_Paging#1](~/../sqlclient/doc/samples/SqlDataAdapter_Paging.cs#1)]

Dans l’exemple précédent, le **DataSet** ne contient que cinq enregistrements, mais la table **Orders** est retournée dans son intégralité. Pour remplir le **DataSet** avec ces cinq mêmes enregistrements, mais en ne retournant que cinq enregistrements, utilisez les clauses `TOP` et `WHERE` dans votre instruction SQL, comme dans l’exemple de code suivant.

[!code-csharp[SqlDataAdapter_Paging#2](~/../sqlclient/doc/samples/SqlDataAdapter_Paging.cs#2)]

> [!NOTE]
> Quand la pagination des résultats de la requête est effectuée de cette façon, vous devez conserver le `unique identifier` qui classe les lignes, afin de passer l’ID unique à la commande pour retourner la page d’enregistrements suivante, comme illustré dans l’exemple de code suivant.

[!code-csharp[SqlDataAdapter_Paging#4](~/../sqlclient/doc/samples/SqlDataAdapter_Paging.cs#4)]

Pour retourner la page `next page of records` en utilisant la surcharge de la méthode **Fill** qui prend les paramètres **startRecord** et **maxRecords**, incrémentez l’index de l’enregistrement actif en fonction de la taille de la page et remplissez la table.

> [!NOTE]
> Rappelez-vous que le serveur de base de données retourne l’intégralité des résultats de la requête, même si une seule page d’enregistrements est ajoutée au **DataSet**.

Dans l'exemple de code suivant, les lignes de la table sont vidées de leur contenu avant de recevoir la page de données suivante. Vous avez la possibilité de conserver dans un cache local un certain nombre de lignes retournées afin de limiter les sollicitations du serveur de base de données.

[!code-csharp[SqlDataAdapter_Paging#3](~/../sqlclient/doc/samples/SqlDataAdapter_Paging.cs#3)]

Pour retourner la page d'enregistrements suivante sans que le serveur de base de données ne retourne l'intégralité de la requête, spécifiez des critères restrictifs pour l'instruction SELECT. Parce que l'exemple précédent conservait le dernier enregistrement retourné, vous pouvez l'utiliser dans la clause WHERE afin de spécifier le point de départ de la requête, comme le montre l'exemple de code suivant.

[!code-csharp[SqlDataAdapter_Paging#5](~/../sqlclient/doc/samples/SqlDataAdapter_Paging.cs#5)]

## <a name="see-also"></a>Voir aussi

- [DataAdapters et DataReaders](dataadapters-datareaders.md)
- [Microsoft ADO.NET pour SQL Server](microsoft-ado-net-sql-server.md)
