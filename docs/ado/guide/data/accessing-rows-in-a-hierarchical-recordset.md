---
title: "Accès aux lignes d’un objet Recordset hiérarchique | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: 25f1d2a1-6d5e-4457-aa07-5db5c75dee18
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 351650e6445c0d8f85751349d243bc8870fd8c2f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="accessing-rows-in-a-hierarchical-recordset-example"></a>L’accès aux lignes dans un jeu d’enregistrements hiérarchique (par exemple)
L’exemple suivant montre les étapes nécessaires pour accéder aux lignes dans une liste hiérarchique [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md):

1.  **Jeu d’enregistrements** des objets de la **auteurs** et **titleauthor** les tables sont liées par ID d’auteur.

2.  La boucle externe affiche le nom et prénom de chaque auteur, l’état et identification.

3.  Ajouté **Recordset** pour chaque ligne est récupérée à partir de la [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection et assigné à *affectation*.

4.  La boucle interne affiche quatre champs de chaque ligne dans le **Recordset**.

 Le [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) est définie sur **false** à des fins d’illustration, afin que vous puissiez voir le chapitre changer de manière explicite dans chaque itération de la boucle externe. Pour rendre l’exemple de code plus efficace, vous pouvez déplacer l’affectation à l’étape 3 avant la première ligne à l’étape 2, afin que l’affectation est exécutée une seule fois. Puis définissez la [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) propriété **true**, de sorte que *affectation* implicitement et automatiquement modifiera le chapitre correspondant à chaque fois que *rst* se déplace vers une nouvelle ligne.

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
 [Vue d’ensemble de la mise en forme des données](../../../ado/guide/data/data-shaping-overview.md) [champ objet](../../../ado/reference/ado-api/field-object.md) [(ADO) de Collection de champs](../../../ado/reference/ado-api/fields-collection-ado.md) [formels forme grammaire](../../../ado/guide/data/formal-shape-grammar.md) [mise en forme de Service pour les données de Microsoft OLE DB (fournisseur de services ADO)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) [l’objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [fournisseurs requis pour la mise en forme des données](../../../ado/guide/data/required-providers-for-data-shaping.md) [forme Clause APPEND](../../../ado/guide/data/shape-append-clause.md) [En général les commandes shape](../../../ado/guide/data/shape-commands-in-general.md) [Clause COMPUTE de forme](../../../ado/guide/data/shape-compute-clause.md) [Visual Basic pour Applications functions](../../../ado/guide/data/visual-basic-for-applications-functions.md)
