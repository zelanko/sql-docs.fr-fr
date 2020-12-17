---
title: Gestion d’événements DataAdapter
description: Décrit les événements DataAdapter et comment les utiliser.
ms.date: 11/30/2020
dev_langs:
- csharp
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: e3715f2060857bf6d5fabb37c049d6e9cff1ee40
ms.sourcegitcommit: 866554663ca3191748b6e4eb4d8d82fa58c4e426
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97559211"
---
# <a name="handle-dataadapter-events"></a>Gestion d’événements DataAdapter

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Le fournisseur de données Microsoft SqlClient pour SQL Server <xref:Microsoft.Data.SqlClient.SqlDataAdapter> expose trois événements que vous pouvez utiliser pour répondre aux modifications apportées aux données au niveau de la source de données. Le tableau ci-dessous répertorie les événements `DataAdapter`.

|Événement|Description|  
|-----------|-----------------|  
|`RowUpdating`|Une opération UPDATE, INSERT ou DELETE sur une ligne (par un appel à l'une des méthodes `Update`) est sur le point de commencer.|  
|`RowUpdated`|Une opération UPDATE, INSERT ou DELETE sur une ligne (par un appel à l'une des méthodes `Update`) est terminée.|  
|`FillError`|Une erreur est survenue pendant une opération `Fill`.|  

## <a name="rowupdating-and-rowupdated-events"></a>Événements RowUpdating et RowUpdated

`RowUpdating` est déclenché avant le traitement d'une mise à jour d'une ligne de l'objet <xref:System.Data.DataSet> au niveau de la source de données. `RowUpdated` est déclenché après le traitement d'une mise à jour d'une ligne de l'objet `DataSet` au niveau de la source de données. En conséquence, vous pouvez utiliser `RowUpdating` pour modifier le comportement de la mise à jour avant qu'elle ne survienne, pour fournir une gestion supplémentaire lors d'une mise à jour, pour conserver une référence à une ligne mise à jour, pour annuler la mise à jour en cours et la programmer pour un traitement par lots à traiter ultérieurement, etc. `RowUpdated` est utile pour réagir aux erreurs et aux exceptions qui surviennent pendant la mise à jour. Vous pouvez ajouter des **informations d’erreur** au `DataSet` ainsi qu’**logique de nouvelle tentative**, etc.

Les arguments <xref:System.Data.Common.RowUpdatingEventArgs> et <xref:System.Data.Common.RowUpdatedEventArgs> passés aux événements `RowUpdating` et `RowUpdated` comprennent les élément suivants : une propriété `Command` qui référence l’objet `Command` utilisé pour effectuer la mise à jour ; une propriété `Row` qui référence l’objet `DataRow` contenant les informations mises à jour ; une propriété `StatementType` pour le type de mise à jour effectuée ; le `TableMapping`, le cas échéant ; et le `Status` de l’opération.

Vous pouvez utiliser la propriété `Status` pour déterminer si une erreur est survenue pendant l'opération et éventuellement contrôler les actions sur les lignes actuelles et qui en résultent. Lorsque l'événement se produit, la propriété `Status` est égale à `Continue` ou `ErrorsOccurred`. Le tableau suivant présente les valeurs que vous pouvez affecter à la propriété `Status` afin de contrôler les actions ultérieures pendant la mise à jour.

|État|Description|  
|------------|-----------------|  
|`Continue`|Continuer l'opération de mise à jour.|  
|`ErrorsOccurred`|Abandonner l'opération de mise à jour et lever une exception.|  
|`SkipCurrentRow`|Ignorer la ligne actuelle et continuer l'opération de mise à jour.|  
|`SkipAllRemainingRows`|Abandonner l'opération de mise à jour mais ne pas lever d'exception.|  

L'affectation de la valeur `Status` à la propriété `ErrorsOccurred` entraîne la levée d'une exception. Vous pouvez contrôler l'exception levée en affectant la propriété `Errors` à l'exception souhaitée. L'utilisation de l'une des autres valeurs pour `Status` évite la levée d'une exception.

Vous pouvez aussi utiliser la propriété `ContinueUpdateOnError` pour gérer les erreurs des lignes mises à jour. Si `DataAdapter.ContinueUpdateOnError` a la valeur `true`, lorsqu'une mise à jour de ligne entraîne la levée d'une exception, le texte de celle-ci est placé dans les informations `RowError` de la ligne particulière et le traitement continue sans lever d'exception. Vous pouvez ainsi répondre aux erreurs lorsque `Update` est terminé, contrairement à l'événement `RowUpdated`, qui vous permet d'y répondre au moment de l'erreur.

L'exemple de code suivant montre comment ajouter et supprimer les gestionnaires d'événements. Le gestionnaire d'événements `RowUpdating` écrit un journal de tous les enregistrements supprimés avec un horodatage. Le gestionnaire d’événements `RowUpdated` ajoute les informations d’erreur à la propriété `RowError` de la ligne dans le `DataSet`, supprime l’exception et continue le traitement (reflétant le comportement de `ContinueUpdateOnError` = `true`).

[!code-csharp[SqlDataAdapter_Events#1](~/../sqlclient/doc/samples/SqlDataAdapter_Events.cs#1)]

## <a name="fillerror-event"></a>FillError (événement)

Le `DataAdapter` émet l'événement `FillError` en cas d'erreur pendant une opération `Fill`. Ce type d’erreur se produit généralement quand les données de la ligne ajoutée n’ont pas pu être converties en type .NET sans perte de précision.

En cas d'erreur pendant une opération `Fill`, la ligne actuelle n'est pas ajoutée au `DataTable`. L'événement `FillError` vous permet de résoudre l'erreur et d'ajouter la ligne, ou d'ignorer la ligne exclue et de poursuivre l'opération `Fill`.

Le <xref:System.Data.FillErrorEventArgs> passé à l'événement `FillError` peut contenir plusieurs propriétés qui vous permettent de répondre aux erreurs et de les résoudre. Le tableau suivant présente les propriétés de l'objet `FillErrorEventArgs`.

|Propriété|Description|  
|--------------|-----------------|  
|`Errors`|`Exception` survenue.|  
|`DataTable`|Objet `DataTable` en cours de remplissage au moment de l'erreur.|  
|`Values`|Tableau d'objets contenant les valeurs de la ligne qui était ajoutée au moment de l'erreur. Les références ordinales du tableau `Values` correspondent à celles des colonnes de la ligne ajoutée. Par exemple, `Values[0]` est la valeur qui a été ajoutée comme première colonne de la ligne.|  
|`Continue`|Vous permet de choisir la levée ou non d'une exception. L'affectation de la valeur `Continue` à la propriété `false` stoppe l'opération `Fill` en cours et une exception est levée. L'affectation de la valeur `Continue` à `true` poursuit l'opération `Fill` en dépit de l'erreur.|  

L'exemple de code suivant ajoute l'événement `FillError` du `DataAdapter` à un gestionnaire d'événements. Dans le code d’événement `FillError`, l’exemple détermine s’il y a une possibilité de perte de précision, donnant ainsi l’opportunité de répondre à l’exception.

[!code-csharp[SqlDataAdapter_Events#2](~/../sqlclient/doc/samples/SqlDataAdapter_Events.cs#2)]

## <a name="see-also"></a>Voir aussi

- [DataAdapters et DataReaders](dataadapters-datareaders.md)
- [Événements](/dotnet/standard/events/index)
- [Microsoft ADO.NET pour SQL Server](microsoft-ado-net-sql-server.md)
