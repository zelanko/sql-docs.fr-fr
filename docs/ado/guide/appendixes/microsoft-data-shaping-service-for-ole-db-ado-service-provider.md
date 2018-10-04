---
title: Microsoft Data Shaping Service pour OLE DB (fournisseur de services ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], data shaping service for OLE DB
- data shaping service for OLE DB [ADO]
ms.assetid: 523009ce-e01b-4e2d-a7df-816d7688aff0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1e3dac6aefb8db2dbd1c651f0a2cf27b0f29559c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47735004"
---
# <a name="microsoft-data-shaping-service-for-ole-db-overview"></a>Microsoft Data Shaping Service pour une vue d’ensemble OLE DB
> [!IMPORTANT]
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, les applications doivent utiliser XML.

 Microsoft Data Shaping Service pour le fournisseur de services OLE DB prend en charge la construction de hiérarchiques (mis en forme) [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objets à partir d’un fournisseur de données.

## <a name="provider-keyword"></a>Mot clé de fournisseur
 Pour appeler le Service de mise en forme des données pour OLE DB, spécifiez le mot clé et la valeur suivante dans la chaîne de connexion.

```
"Provider=MSDataShape"
```

## <a name="dynamic-properties"></a>Propriétés dynamiques
 Lorsque ce fournisseur de services est appelé, les propriétés dynamiques suivantes sont ajoutées à la [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection de la[connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet.

|Nom de la propriété dynamique|Description|
|---------------------------|-----------------|
|**Noms de la mise en forme unique**|Indique si **Recordset** objets avec des valeurs dupliquées pour leurs **Reshape Name** les propriétés sont autorisées. Si cette propriété dynamique a **True** et un nouveau **Recordset** est créé avec le même nom de la mise en forme spécifiée par l’utilisateur comme existant **Recordset**, puis la nouvelle  **Jeu d’enregistrements** nom de la mise en forme de l’objet est modifié pour le rendre unique. Si cette propriété est **False** et un nouveau **Recordset** est créé avec le même nom de la mise en forme spécifiée par l’utilisateur qu’existant **Recordset**, à la fois **Recordset**  objets ont le même nom de la mise en forme. Par conséquent, aucune des deux **Recordset** puissent être REFORMÉES tant que les deux jeux d’enregistrements existe.<br /><br /> La valeur par défaut de la propriété est **False**.|
|**Fournisseur de données**|Indique le nom du fournisseur qui fournira les lignes à mettre en forme. Cette valeur peut être NONE si un fournisseur ne sera pas utilisé pour fournir des lignes.|

 Vous pouvez également définir des propriétés dynamiques en écriture en spécifiant leurs noms en tant que mots clés dans la chaîne de connexion. Par exemple, dans Microsoft Visual Basic, définissez la **fournisseur de données** propriété dynamique à « MSDASQL » en spécifiant :

```
Dim cn as New ADODB.Connection
cn.Open "Provider=MSDataShape;Data Provider=MSDASQL"
```

 Vous pouvez également définir ou extraire une propriété dynamique en spécifiant son nom comme index de la [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) propriété. Par exemple, l’exemple de code suivant obtient et imprime la valeur actuelle de la **fournisseur de données** propriété dynamique, puis définit une nouvelle valeur si cn. DataProvider a été défini sur « MSDataShape » (directement ou indirectement via la chaîne de connexion) et la connexion n’a pas été ouvert :

```
Debug.Print cn.Properties("Data Provider")
cn.Properties("Data Provider") = "MSDASQL"
```

> [!NOTE]
>  La propriété dynamique, **fournisseur de données**, peut être uniquement configurée sur un non ouvert **connexion** objet. Une fois que la connexion est ouverte, le **fournisseur de données** propriété devient en lecture seule.

 Pour plus d’informations sur la mise en forme des données, consultez [mise en forme des données](../../../ado/guide/data/data-shaping-overview.md).

## <a name="see-also"></a>Voir aussi
 [Annexe A : Fournisseurs](../../../ado/guide/appendixes/appendix-a-providers.md)
