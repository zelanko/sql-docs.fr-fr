---
description: Fabrication de recordsets hiérarchiques
title: Fabrication de jeux d’enregistrements hiérarchiques | Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: e1bf51c8d7d6db2ac898787c3a649a0ecb0610cb
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806843"
---
# <a name="fabricating-hierarchical-recordsets"></a>Fabrication de recordsets hiérarchiques
L’exemple suivant montre comment créer un jeu d’enregistrements hiérarchique sans source de données sous-jacente à l’aide de la syntaxe de mise en forme des données pour définir des colonnes pour les **jeux d’enregistrements**parents, enfants et petits-enfants.  
  
 Pour fabriquer un **jeu d’enregistrements**hiérarchique, vous devez spécifier [Microsoft Data Shaping Service pour OLE DB (fournisseur de services ADO)](../appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (MSDataShape) et vous pouvez spécifier une fournisseur de données valeur None dans le paramètre de chaîne de connexion de la méthode [Open](../../reference/ado-api/open-method-ado-connection.md) de l’objet [Connection](../../reference/ado-api/connection-object-ado.md) . Pour plus d’informations, consultez [fournisseurs requis pour la mise en forme des données](./required-providers-for-data-shaping.md).  
  
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
  
 Dès que le **jeu d’enregistrements** a été créé, il peut être rempli, manipulé ou rendu persistant dans un fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux lignes d’un jeu d’enregistrements hiérarchique](./accessing-rows-in-a-hierarchical-recordset.md)   
 [Grammaire de forme formelle](./formal-shape-grammar.md)   
 [Fournisseurs requis pour la mise en forme des données](./required-providers-for-data-shaping.md)   
 [Clause APPEND de la forme](./shape-append-clause.md)   
 [Généralités sur les commandes SHAPE](./shape-commands-in-general.md)