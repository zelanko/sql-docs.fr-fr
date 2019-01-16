---
title: Fournisseurs requis pour la mise en forme des données | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], data shaping
- data shaping [ADO], providers required
ms.assetid: d49d48d2-ac2d-4c11-895c-5a149b444620
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7edd3b3cacd097380b5d14ad55ed115ff93cf072
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2019
ms.locfileid: "54255704"
---
# <a name="required-providers-for-data-shaping"></a>Fournisseurs nécessaires pour la mise en forme des données
Mise en forme des données nécessite généralement deux fournisseurs. Le fournisseur de services, [Data Shaping Service pour OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md), fournit les données de mise en forme des fonctionnalités et un fournisseur de données, tels que le fournisseur OLE DB pour SQL Server, fournit les lignes de données pour remplir la forme [Recordset ](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 Le nom du fournisseur de services (MSDataShape) peut être spécifié comme valeur de la [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet [fournisseur](../../../ado/reference/ado-api/provider-property-ado.md) propriété ou le mot de clé de chaîne de connexion « fournisseur = MSDataShape ; ».  
  
 Le nom du fournisseur de données peut être spécifié comme valeur de la **fournisseur de données** propriété dynamique, qui est ajoutée à la **connexion** objet [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection par le Service de mise en forme des données pour OLE DB ou le mot de clé de chaîne de connexion «**fournisseur de données =**_fournisseur_».  
  
 Aucun fournisseur de données n’est requis si le **Recordset** n’est pas remplie (par exemple, comme dans un fabriqués **Recordset** où les colonnes sont créées avec le nouveau mot clé). Dans ce cas, spécifiez «**fournisseur de données =** none ; ».  
  
## <a name="example"></a>Exemple  
  
```  
Dim cnn As New ADODB.Connection  
cnn.Provider = "MSDataShape"  
cnn.Open "Data Provider=SQLOLEDB;Integrated Security=SSPI;Database=Northwind"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de mise en forme des données](../../../ado/guide/data/data-shaping-example.md)   
 [Grammaire de la mise en forme formelle](../../../ado/guide/data/formal-shape-grammar.md)   
 [Généralités sur les commandes SHAPE](../../../ado/guide/data/shape-commands-in-general.md)
