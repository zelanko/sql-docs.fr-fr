---
title: Service de curseur Microsoft pour OLE DB (composant du Service ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], cursor service for OLE DB
- cursor service for OLE DB [ADO]
ms.assetid: 420d0989-7cfb-4c66-a7b5-f4199d13165d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 500a3e38599b0041b036eb148f837afc67260849
ms.sourcegitcommit: 96b2355d54dfad259826e88bdff91cc9344e16f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51350503"
---
# <a name="microsoft-cursor-service-for-ole-db-overview"></a>Service de curseur Microsoft pour une vue d’ensemble OLE DB
Le Service de curseur Microsoft pour OLE DB complète les fonctions de prise en charge de curseur des fournisseurs de données. Par conséquent, l’utilisateur la perçoit relativement uniforme des fonctionnalités à partir de tous les fournisseurs de données.

 Le Service de curseur rend les propriétés dynamiques disponibles et améliore le comportement de certaines méthodes. Par exemple, le [optimiser](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) propriété dynamique permet la création d’index temporaires afin de faciliter certaines opérations, telles que la [trouver](../../../ado/reference/ado-api/find-method-ado.md) (méthode).

 Le Service de curseur permet la prise en charge de la mise à jour du lot dans tous les cas. Elle simule également des types de curseurs plus performante, tels que les curseurs dynamiques, lorsqu’un fournisseur de données peut fournir uniquement les curseurs moins performant, tels que les curseurs statiques.

## <a name="keyword"></a>Mot clé
 Pour appeler ce composant de service, définissez la [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) ou [connexion](../../../ado/reference/ado-api/connection-object-ado.md) l’objet [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété **adUseClient**.

```vb
connection.CursorLocation=adUseClient
recordset.CursorLocation=adUseClient
```

## <a name="dynamic-properties"></a>Propriétés dynamiques
 Lorsque le Service de curseur pour OLE DB est appelé, les propriétés dynamiques suivantes sont ajoutées à la **Recordset** l’objet [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection. La liste complète des **connexion** et **Recordset** propriétés dynamiques de l’objet est répertorié dans le [Index des propriétés dynamiques ADO](../../../ado/reference/ado-api/ado-dynamic-property-index.md). Les noms de propriété OLE DB associés, le cas échéant, sont inclus dans les parenthèses après le nom de la propriété ADO.

 Modifications apportées à certaines propriétés dynamiques ne sont pas visibles à la source de données sous-jacente, après que le Service de curseur a été appelé. Par exemple, si le *commande délai d’expiration* propriété sur un **Recordset** ne seront pas visibles par le fournisseur de données sous-jacent.

```vb

Recordset1.CursorLocation = adUseClient     'invokes cursor service
Recordset1.Open "authors", _
    "Provider=SQLOLEDB;Data Source=DBServer;User Id=MyUserID;" & _
    "Password=MyPassword;Initial Catalog=pubs;",,adCmdTable
Recordset1.Properties.Item("Command Time out") = 50
' 'Command Time out' property on DBServer is still default (30).

```

 Si votre application requiert le Service de curseur, mais vous devez définir des propriétés dynamiques sur le fournisseur sous-jacent, définissez les propriétés avant d’appeler le Service de curseur. Paramètres de propriété d’objet commande sont toujours transmis au fournisseur de données sous-jacent, quel que soit l’emplacement du curseur. Par conséquent, vous pouvez également utiliser un objet de commande pour définir les propriétés à tout moment.

> [!NOTE]
>  La propriété dynamique DBPROP_SERVERDATAONINSERT n’est pas pris en charge par le service de curseur, même si elle est prise en charge par le fournisseur de données sous-jacent.

|Nom de la propriété|Description|
|-------------------|-----------------|
|Recalcul automatique (DBPROP_ADC_AUTORECALC)|Pour les jeux d’enregistrements créés avec le Service de mise en forme des données, cette valeur indique la fréquence à laquelle les colonnes calculées et agrégées sont calculées. La valeur par défaut (valeur = 1) consiste à recalculer chaque fois que le Service de mise en forme de données détermine que les valeurs ont changé. Si la valeur est 0, les colonnes calculées ou d’agrégats sont calculées uniquement lorsque la hiérarchie est initialement créée.|
|Taille de lot (DBPROP_ADC_BATCHSIZE)|Indique le nombre d’instructions de mise à jour qui peuvent être regroupées avant d’être envoyés au magasin de données. Les instructions plus dans un lot, les moins d’allers-retours vers les données stocker.|
|Mettre en cache les lignes enfants (DBPROP_ADC_CACHECHILDROWS)|Pour les jeux d’enregistrements créé avec le Service de mise en forme des données, cette valeur indique si les jeux d’enregistrements enfants est stockés dans un cache pour une utilisation ultérieure.|
|Version du moteur de curseur (DBPROP_ADC_CEVER)|Indique la version du Service de curseur utilisée.|
|Maintenir l’état de modification (DBPROP_ADC_MAINTAINCHANGESTATUS)|Indique le texte de la commande utilisée pour une une ou plusieurs lignes dans une jointure de plusieurs tables en cours de resynchronisation.|
|[Optimiser](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)|Indique si un index doit être créé. Lorsque la valeur **True**, autorise la création temporaire d’index pour améliorer l’exécution de certaines opérations.|
|[Modifier la forme nom](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md)|Indique le nom de la **Recordset**. Peut être référencé dans actuel ou la suivante, commandes de mise en forme des données.|
|[Resync, commande](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md)|Indique une chaîne de commande personnalisée qui est utilisée par le [Resync](../../../ado/reference/ado-api/resync-method.md) méthode lorsque le [Unique Table](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) propriété est en vigueur.|
|[Catalogue unique](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|Indique le nom de la base de données contenant la table référencée dans la **Unique Table** propriété.|
|[Schéma unique](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|Indique le nom du propriétaire de la table référencée dans la **Unique Table** propriété.|
|[Table unique](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|Indique le nom de l’unique table dans un **Recordset** créé à partir de plusieurs tables qui peuvent être modifiés par les insertions, des mises à jour ou des suppressions.|
|Critères de mise à jour (DBPROP_ADC_UPDATECRITERIA)|Indique les champs dans le **où** clause sont utilisés pour gérer les conflits qui se produisent pendant une mise à jour.|
|[Mettre à jour de la resynchronisation](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) (DBPROP_ADC_UPDATERESYNC)|Indique si le **Resync** méthode est implicitement appelée après la [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) (méthode) (et son comportement), lorsque le **Unique Table** propriété est en vigueur.|

 Vous pouvez également définir ou extraire une propriété dynamique en spécifiant son nom comme index de la **propriétés** collection. Par exemple, obtenir et imprimer la valeur actuelle de la [optimiser](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) propriété dynamique, puis définissez une nouvelle valeur, comme suit :

```vb
Debug.Print rs.Properties("Optimize")
rs.Properties("Optimize") = True
```

## <a name="built-in-property-behavior"></a>Comportement de la propriété intégrée
 Le Service de curseur pour OLE DB affecte également le comportement de certaines propriétés intégrées.

|Nom de la propriété|Description|
|-------------------|-----------------|
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|Complète les types de curseurs disponibles pour un **Recordset**.|
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|Complète les types de verrous disponibles pour un **Recordset**. Permet des mises à jour de commandes.|
|[Sort](../../../ado/reference/ado-api/sort-property.md)|Spécifie le champ un ou plusieurs noms qui le **Recordset** est triée et si chaque champ est trié dans l’ordre croissant ou décroissant.|

## <a name="method-behavior"></a>Comportement de la méthode
 Le Service de curseur pour OLE DB Active ou affecte le comportement de la [champ](../../../ado/reference/ado-api/field-object.md) l’objet [Append](../../../ado/reference/ado-api/append-method-ado.md) méthode ; et le **Recordset** l’objet [ouvrir](../../../ado/reference/ado-api/open-method-ado-recordset.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), et [enregistrer](../../../ado/reference/ado-api/save-method.md) méthodes.
