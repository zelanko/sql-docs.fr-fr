---
title: Microsoft Data Shaping Service pour OLE DB (fournisseur de services ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], data shaping service for OLE DB
- data shaping service for OLE DB [ADO]
ms.assetid: 523009ce-e01b-4e2d-a7df-816d7688aff0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ddef2feab633627c9549b73787faa1d104d69c5e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67926811"
---
# <a name="microsoft-data-shaping-service-for-ole-db-overview"></a>Vue d’ensemble de Microsoft Data Shaping Service pour OLE DB
> [!IMPORTANT]
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, les applications doivent utiliser XML.

 Le fournisseur de services Microsoft Data Shaping Service pour OLE DB prend en charge la construction d’objets [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) hiérarchiques (mis en forme) à partir d’un fournisseur de données.

## <a name="provider-keyword"></a>Mot clé Provider
 Pour appeler le service de mise en forme des données pour OLE DB, spécifiez le mot clé et la valeur suivants dans la chaîne de connexion.

```vb
"Provider=MSDataShape"
```

## <a name="dynamic-properties"></a>Propriétés dynamiques
 Lorsque ce fournisseur de services est appelé, les propriétés dynamiques suivantes sont ajoutées à la collection de [Propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) de l’objet de[connexion](../../../ado/reference/ado-api/connection-object-ado.md) .

|Nom de la propriété dynamique|Description|
|---------------------------|-----------------|
|**Noms de reformes uniques**|Indique si les objets **Recordset** avec des valeurs dupliquées pour leurs propriétés **Remodel Name** sont autorisés. Si cette propriété dynamique a la **valeur true** et qu’un nouvel ensemble **d’enregistrements** est créé avec le même nom de reforme spécifié par l’utilisateur qu’un **jeu d’enregistrements**existant, le nom de la nouvelle forme de l’objet **Recordset** est modifié pour le rendre unique. Si cette propriété a la **valeur false** et qu’un nouvel ensemble **d’enregistrements** est créé avec le même nom de reforme spécifié par l’utilisateur que le **jeu d’enregistrements**existant, les deux objets **Recordset** auront le même nom de reforme. Par conséquent, aucun **Recordset** ne peut être remodelé tant que les deux jeux d’enregistrements existent.<br /><br /> La valeur par défaut de la propriété est **false**.|
|**Fournisseur de données**|Indique le nom du fournisseur qui fournira les lignes à mettre en forme. Cette valeur peut être NONE si un fournisseur ne sera pas utilisé pour fournir des lignes.|

 Vous pouvez également définir des propriétés dynamiques en écriture en spécifiant leurs noms en tant que Mots clés dans la chaîne de connexion. Par exemple, dans Microsoft Visual Basic, définissez la propriété dynamique **fournisseur de données** sur « MSDASQL » en spécifiant :

```vb
Dim cn as New ADODB.Connection
cn.Open "Provider=MSDataShape;Data Provider=MSDASQL"
```

 Vous pouvez également définir ou récupérer une propriété dynamique en spécifiant son nom en tant qu’index de la propriété [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) . Par exemple, l’exemple de code suivant obtient et imprime la valeur actuelle de la **fournisseur de données** propriété dynamique, puis définit une nouvelle valeur si CN. DataProvider a été défini sur « MSDataShape » (directement ou indirectement via la chaîne de connexion) et la connexion n’a pas été ouverte :

```vb
Debug.Print cn.Properties("Data Provider")
cn.Properties("Data Provider") = "MSDASQL"
```

> [!NOTE]
>  La propriété dynamique, **fournisseur de données**, peut être définie uniquement sur un objet de **connexion** non ouvert. Une fois la connexion ouverte, la propriété **fournisseur de données** devient en lecture seule.

 Pour plus d’informations sur la mise en forme des données, consultez mise en [forme des données](../../../ado/guide/data/data-shaping-overview.md).

## <a name="see-also"></a>Voir aussi
 [Annexe A : Fournisseurs](../../../ado/guide/appendixes/appendix-a-providers.md)
