---
title: Traitement d’opérations par lots à l'aide de DataAdapter
description: Décrit l’amélioration des performances des applications en réduisant le nombre d’allers-retours à SQL Server lors de l’application de mises à jour provenant du DataSet.
ms.date: 11/30/2020
dev_langs:
- csharp
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 1b720dff0678c68396fe7d8cf1f60f3ade70dd9d
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2020
ms.locfileid: "96772266"
---
# <a name="batch-operations-using-dataadapters"></a>Traitement d’opérations par lots à l'aide de DataAdapter

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

La prise en charge des lots dans ADO.NET permet à un objet <xref:System.Data.Common.DataAdapter> de grouper des opérations INSERT, UPDATE et DELETE à partir d'un objet <xref:System.Data.DataSet> ou d'un objet <xref:System.Data.DataTable> pour le serveur, au lieu d'envoyer les opérations successivement. La réduction du nombre d'allers-retours vers le serveur entraîne généralement des gains de performances importants. La mise à jour par lot est prise en charge pour le fournisseur de données Microsoft SqlClient pour SQL Server (<xref:Microsoft.Data.SqlClient>).

Lors de la mise à jour d'une base de données avec les modifications d'un objet <xref:System.Data.DataSet> dans les versions précédentes d'ADO.NET, la méthode `Update` d'un objet `DataAdapter` apportait des mises à jour à la base de données ligne après ligne. Comme elle effectuait une itération dans les lignes de l'objet <xref:System.Data.DataTable> spécifié, elle examinait chaque objet <xref:System.Data.DataRow> pour voir s'il avait été modifié. Si la ligne avait été modifiée, elle appelait `UpdateCommand`, `InsertCommand` ou `DeleteCommand` en fonction de la valeur de la propriété <xref:System.Data.DataRow.RowState%2A> de cette ligne. Chaque mise à jour de ligne impliquait un aller-retour sur le réseau vers la base de données.

Au niveau du Fournisseur de données Microsoft SqlClient pour SQL Server, le <xref:Microsoft.Data.SqlClient.SqlDataAdapter> expose une propriété <xref:Microsoft.Data.SqlClient.SqlDataAdapter.UpdateBatchSize%2A>. L'affection d'une valeur entière positive à la propriété `UpdateBatchSize` a pour effet d'envoyer les mises à jour de la base de données sous la forme de lots de la taille spécifiée. Par exemple, l'affectation de la valeur 10 à la propriété `UpdateBatchSize` groupe 10 instructions distinctes avant de les soumettre en tant que lot. Avec la valeur 0, l'objet `UpdateBatchSize` utilise la taille de lot la plus grande que le serveur peut gérer. La valeur 1 désactive les mises à jour par lots car les lignes sont envoyées les unes après les autres.

> [!NOTE]
> L'exécution d'un lot très volumineux peut réduire les performances. Vous devez donc tester le paramètre de taille de lot optimal avant d'implémenter votre application.

## <a name="use-the-updatebatchsize-property"></a>Utiliser la propriété UpdateBatchSize

Lorsque les mises à jour par lots sont activées, la valeur <xref:System.Data.IDbCommand.UpdatedRowSource%2A> ou `UpdateCommand` doit être affectée à la propriété `InsertCommand` de `DeleteCommand`, <xref:System.Data.UpdateRowSource.None> et <xref:System.Data.UpdateRowSource.OutputParameters> du DataAdapter. Lors de l'exécution d'une mise à jour par lots, les valeurs <xref:System.Data.IDbCommand.UpdatedRowSource%2A> ou <xref:System.Data.UpdateRowSource.FirstReturnedRecord> de la propriété <xref:System.Data.UpdateRowSource.Both> de la commande ne sont pas valides.
  
La procédure suivante illustre l'utilisation de la propriété `UpdateBatchSize`. La procédure prend deux arguments, un objet <xref:System.Data.DataSet> contenant des colonnes représentant les champs **ProductCategoryID** et **Name** dans la table **Production.ProductCategory**, et un entier représentant la taille du lot (nombre de lignes dans le lot). Le code crée un nouvel objet <xref:Microsoft.Data.SqlClient.SqlDataAdapter>, en définissant ses propriétés <xref:Microsoft.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:Microsoft.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> et <xref:Microsoft.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A>. Le code est basé sur l'hypothèse que l'objet <xref:System.Data.DataSet> comporte des lignes modifiées. Il définit la propriété `UpdateBatchSize` et effectue la mise à jour.

[!code-csharp[SqlDataAdapter_Batch#1](~/../sqlclient/doc/samples/SqlDataAdapter_Batch.cs#1)]

## <a name="handle-batch-update-related-events-and-errors"></a>Gérer les erreurs et événements liés à la mise à jour par lot

Le **DataAdapter** a deux événements liés aux mises à jour : **RowUpdating** et **RowUpdated**. Pour plus d’informations, consultez [Gérer les événements de DataAdapter](handle-dataadapter-events.md).

### <a name="event-behavior-changes-with-batch-updates"></a>Changements de comportement des événements avec les mises à jour par lot

Lorsque le traitement par lots est activé, plusieurs lignes sont mises à jour en une seule opération de base de données. Par conséquent, un seul événement `RowUpdated` se produit pour chaque lot, tandis que l'événement `RowUpdating` se produit pour chaque ligne traitée. Lorsque le traitement par lots est désactivé, les deux événements sont déclenchés avec un entrelacement de un à un où un événement `RowUpdating` et un événement `RowUpdated` se déclenchent pour une ligne, puis un événement `RowUpdating` et un événement `RowUpdated` se déclenchent pour la ligne suivante, jusqu'à ce que toutes les lignes aient été traitées.

### <a name="access-updated-rows"></a>Accéder aux lignes mises à jour

Lorsque le traitement par lots est désactivé, la ligne mise à jour est accessible à l'aide de la propriété <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> de la classe <xref:System.Data.Common.RowUpdatedEventArgs>.

Lorsque le traitement par lots est activé, un simple événement `RowUpdated` est généré pour plusieurs lignes. C'est pourquoi la valeur de la propriété `Row` pour chaque ligne est null. Des événements `RowUpdating` sont encore générés pour chaque ligne. La méthode <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> de la classe <xref:System.Data.Common.RowUpdatedEventArgs> permet d'accéder aux lignes traitées en copiant les références aux lignes dans un tableau. Si aucune ligne n'est traitée, `CopyToRows` lève une exception <xref:System.ArgumentNullException>. Utilisez la propriété <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> pour retourner le nombre de lignes traitées avant d'appeler la méthode <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A>.

### <a name="handle-data-errors"></a>Gérer les erreurs de données

L'exécution par lots a le même effet que l'exécution des instructions individuelles. Les instructions sont exécutées dans l'ordre où elles ont été ajoutées au lot. Les erreurs sont gérées de la même manière, que le mode de traitement par lots soit activé ou non. Chaque ligne est traitée séparément. Seules les lignes traitées avec succès dans la base de données sont mises à jour dans l'objet <xref:System.Data.DataRow> correspondant à l'objet <xref:System.Data.DataTable>.

> [!NOTE]
> Le serveur SQL Server du Fournisseur de données Microsoft SqlClient et le serveur de base de données back-end déterminent les constructions SQL prises en charge pour l’exécution par lot. Une exception peut être levée si une instruction non prise en charge est soumise pour exécution.

## <a name="see-also"></a>Voir aussi

- [DataAdapters et DataReaders](dataadapters-datareaders.md)
- [Mise à jour de sources de données avec des DataAdapter](update-data-sources-with-dataadapters.md)
- [Gestion d’événements DataAdapter](handle-dataadapter-events.md)
- [Microsoft ADO.NET pour SQL Server](microsoft-ado-net-sql-server.md)
