---
title: Accès aux lignes d’un jeu d’enregistrements hiérarchique | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: 25f1d2a1-6d5e-4457-aa07-5db5c75dee18
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e73b2ca96cc5e7eb7683b72aa19fd59a318b8596
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67926356"
---
# <a name="accessing-rows-in-a-hierarchical-recordset-example"></a>Accès aux lignes d’un jeu d’enregistrements hiérarchique (exemple)
L’exemple suivant montre les étapes nécessaires pour accéder aux lignes d’un [jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md)hiérarchique :

1.  Les objets **Recordset** des tables **Authors** et **titleauthor** sont liés par l’ID de l’auteur.

2.  La boucle externe affiche le prénom et le nom, l’État et l’identification de chaque auteur.

3.  Le **Recordset** ajouté pour chaque ligne est extrait de la collection de [champs](../../../ado/reference/ado-api/fields-collection-ado.md) et affecté à *rstTitleAuthor*.

4.  La boucle interne affiche quatre champs de chaque ligne dans le **Recordset**ajouté.

 La propriété [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) a la valeur **false** à des fins d’illustration, afin que vous puissiez voir le chapitre changer explicitement dans chaque itération de la boucle externe. Pour améliorer l’efficacité de l’exemple de code, vous pouvez déplacer l’affectation à l’étape 3 avant la première ligne de l’étape 2, afin que l’assignation ne soit exécutée qu’une seule fois. Affectez ensuite la valeur **true**à la propriété [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) , afin que *rstTitleAuthor* passe implicitement et automatiquement au chapitre correspondant chaque fois que *RST* passe à une nouvelle ligne.

## <a name="example"></a>Exemple

```
Sub datashape()
   Dim cnn As New ADODB.Connection
   Dim rst As New ADODB.Recordset
   Dim rstTitleAuthor As New ADODB.Recordset

   cnn.Provider = "MSDataShape"
   cnn.Open    "Data Provider=MSDASQL;" & _
               "Data Source=SRV;Integrated Security=SSPI;Database=Pubs"
' STEP 1
   rst.StayInSync = FALSE
   rst.Open    "SHAPE  {select * from authors} "  & _
               "APPEND ({select * from titleauthor} " & _
               "RELATE au_id TO au_id) AS chapTitleAuthor", _
               cnn
' STEP 2
   While Not rst.EOF
      Debug.Print    rst("au_fname"), rst("au_lname"), _
                     rst("state"), rst("au_id")
' STEP 3
      Set rstTitleAuthor = rst("chapTitleAuthor").Value
' STEP 4
      While Not rstTitleAuthor.EOF
         Debug.Print rstTitleAuthor(0), rstTitleAuthor(1), _
                     rstTitleAuthor(2), rstTitleAuthor(3)
         rstTitleAuthor.MoveNext
      Wend
      rst.MoveNext
   Wend
End Sub
```

## <a name="see-also"></a>Voir aussi
 [Vue d’ensemble](../../../ado/guide/data/data-shaping-overview.md) de la mise en forme des données collection de champs d' [objets de champ](../../../ado/reference/ado-api/field-object.md) [(ADO)](../../../ado/reference/ado-api/fields-collection-ado.md) [grammaire de forme formelle](../../../ado/guide/data/formal-shape-grammar.md) [Microsoft Data Shaping Service pour OLE DB (ADO Service Provider)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) [objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [fournisseurs requis pour](../../../ado/guide/data/required-providers-for-data-shaping.md) la mise en forme des données commande de la forme [Ajouter](../../../ado/guide/data/shape-append-clause.md) une clause [dans](../../../ado/guide/data/shape-commands-in-general.md) la [clause COMPUTE Shape](../../../ado/guide/data/shape-compute-clause.md) [Visual Basic pour applications Functions](../../../ado/guide/data/visual-basic-for-applications-functions.md)
