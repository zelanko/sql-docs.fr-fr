---
title: Fabrication de Recordsets hiérarchiques | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset fabrication [ADO]
- hierarchical Recordsets [ADO]
- fabricating hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: a584e642-a4a3-418e-bc20-3aff81a5625a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 17cf661e092e253e206b595dec5d807a35b895fb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63161453"
---
# <a name="fabricating-hierarchical-recordsets"></a>Fabrication de recordsets hiérarchiques
L’exemple suivant montre comment créer un objet Recordset hiérarchique sans source de données sous-jacente en utilisant les données de mise en forme pour définir les colonnes pour le parent, enfants et petits-enfants **Recordsets**.  
  
 Pour créer une liste hiérarchique **Recordset**, vous devez spécifier le [Microsoft Data Shaping Service pour OLE DB (fournisseur de services ADO)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (MSDataShape), et vous pouvez spécifier une valeur de fournisseur de données None dans le paramètre de chaîne de connexion de la [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) méthode de la [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet. Pour plus d’informations, consultez [fournisseur de mise en forme des données](../../../ado/guide/data/required-providers-for-data-shaping.md).  
  
```  
Dim cn As New ADODB.Connection  
Dim rsCustomers As New ADODB.Recordset  
  
cn.Open "Provider=MSDataShape;Data Provider=NONE;"  
  
strShape = _  
"SHAPE APPEND NEW adInteger AS CustID," & _  
            " NEW adChar(25) AS FirstName," & _  
            " NEW adChar(25) AS LastName," & _  
            " NEW adChar(12) AS SSN," & _  
            " NEW adChar(50) AS Address," & _  
         " ((SHAPE APPEND NEW adChar(80) AS VIN_NO," & _  
                        " NEW adInteger AS CustID," & _  
                        " NEW adChar(20) AS BodyColor, " & _  
                     " ((SHAPE APPEND NEW adChar(80) AS VIN_NO," & _  
                                    " NEW adChar(20) AS Make, " & _  
                                    " NEW adChar(20) AS Model," & _  
                                    " NEW adChar(4) AS Year) " & _  
                        " AS VINS RELATE VIN_NO TO VIN_NO))" & _  
            " AS Vehicles RELATE CustID TO CustID) "  
  
rsCustomers.Open strShape, cn, adOpenStatic, adLockOptimistic, -1  
```  
  
 Dès que le **Recordset** a été créé, il peut être rempli, manipulé ou conservé dans un fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux lignes dans un Recordset hiérarchique](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Grammaire de la mise en forme formelle](../../../ado/guide/data/formal-shape-grammar.md)   
 [Fournisseurs requis pour la mise en forme des données](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Clause APPEND de forme](../../../ado/guide/data/shape-append-clause.md)   
 [Généralités sur les commandes SHAPE](../../../ado/guide/data/shape-commands-in-general.md)
