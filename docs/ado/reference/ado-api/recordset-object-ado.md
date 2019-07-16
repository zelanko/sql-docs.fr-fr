---
title: L’objet Recordset (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset
helpviewer_keywords:
- Recordset object [ADO]
ms.assetid: ede1415f-c3df-4cc5-a05b-2576b2b84b60
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e76bc993b6f3fed781b8458bc7cf4a70081cd167
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931366"
---
# <a name="recordset-object-ado"></a>Recordset, objet (ADO)
Représente l’ensemble des enregistrements à partir d’une table de base ou les résultats d’une commande exécutée. À tout moment, le **Recordset** objet fait référence à un seul enregistrement dans le jeu en tant que l’enregistrement en cours.  
  
## <a name="remarks"></a>Notes  
 Vous utilisez **Recordset** objets pour manipuler des données à partir d’un fournisseur. Lorsque vous utilisez ADO, vous manipulez les données à l’aide de presque entièrement **Recordset** objets. Tous les **Recordset** objets sont constitués d’enregistrements (lignes) et des champs (colonnes). Selon les fonctionnalités prises en charge par le fournisseur, certaines **Recordset** méthodes ou propriétés ne soient pas disponibles.  
  
 ADODB. Jeu d’enregistrements est le ProgID qui doit être utilisé pour créer un **Recordset** objet. Applications existantes qui font référence à l’objet ADOR obsolète. Recordset ProgID continueront à fonctionner sans recompilation, mais tout nouveau développement doit référencer ADODB. Jeu d’enregistrements.  
  
 Il existe quatre types de curseurs définis dans ADO :  
  
-   **Curseur dynamique** vous permet d’afficher les ajouts, modifications et suppressions par d’autres utilisateurs ; permet à tous les types de déplacement dans le **Recordset** qui ne repose pas sur les signets ; et permet des signets si le fournisseur prend en charge les.  
  
-   **Curseur keyset** ajouter Behaves comme un curseur dynamique, à ceci près qu’elle vous empêche d’afficher les enregistrements que les autres utilisateurs et empêche l’accès aux enregistrements supprimés par d’autres utilisateurs. Modifications de données par d’autres utilisateurs seront toujours visibles. Il prend toujours en charge les signets et donc tous les types de déplacements à la **Recordset**.  
  
-   **Curseur statique** fournit une copie statique d’un jeu d’enregistrements que vous pouvez utiliser pour rechercher des données ou générer des rapports ; permet toujours de signets et donc tous les types de déplacement dans le **Recordset**. Ajouts, modifications ou suppressions par d’autres utilisateurs ne seront pas visibles. Il s’agit du seul type de curseur accepté lorsque vous ouvrez une côté client **Recordset** objet.  
  
-   **Curseur avant uniquement** vous permet uniquement le défilement vers l’avant via le **Recordset**. Ajouts, modifications ou suppressions par d’autres utilisateurs ne seront pas visibles. Cela améliore les performances dans les situations où vous devez passer uniquement un seul dans un **Recordset**.  
  
 Définir le [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) propriété avant ouverture le **Recordset** pour choisir le type de curseur, ou passer un *CursorType* argument avec le [ouvrir](../../../ado/reference/ado-api/open-method-ado-recordset.md)(méthode). Certains fournisseurs ne prennent pas en charge tous les types de curseur. Consultez la documentation pour le fournisseur. Si vous ne spécifiez pas un type de curseur, ADO ouvre un curseur avant uniquement par défaut.  
  
 Si le [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété est définie sur **adUseClient** pour ouvrir un **Recordset**, le **UnderlyingValue** propriété sur [Champ](../../../ado/reference/ado-api/field-object.md) objets n’est pas disponible dans la liste retournée **Recordset** objet. Lorsqu’il est utilisé avec certains fournisseurs (par exemple, le fournisseur ODBC Microsoft pour OLE DB conjointement avec Microsoft SQL Server), vous pouvez créer **Recordset** objets indépendamment défini précédemment [connexion](../../../ado/reference/ado-api/connection-object-ado.md)en passant une chaîne de connexion avec le **Open** (méthode). ADO crée toujours un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet, mais il ne l’affecte à une variable objet. Toutefois, si vous ouvrez plusieurs **Recordset** objets sur la même connexion, vous devez explicitement créer et ouvrir un **connexion** objet ; ce affecte le **connexion**objet à une variable objet. Si vous n’utilisez pas cette variable d’objet lors de l’ouverture votre **Recordset** objets, ADO crée un nouveau **connexion** objet pour chaque nouveau **Recordset**, même si vous passez le même chaîne de connexion.  
  
 Vous pouvez créer autant **Recordset** objets en fonction des besoins.  
  
 Lorsque vous ouvrez un **Recordset**, l’enregistrement actif est positionné au premier enregistrement (le cas échéant) et le [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) et [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) propriétés sont définies sur **False**. Si aucun enregistrement, la **BOF** et **EOF** sont des paramètres de propriété **True**.  
  
 Vous pouvez utiliser la [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), **MoveLast**, **MoveNext**, et **MovePrevious** méthodes ; le [déplacer](../../../ado/reference/ado-api/move-method-ado.md) méthode ; et le [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md), [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md), et [filtre](../../../ado/reference/ado-api/filter-property.md) propriétés repositionner l’enregistrement en cours, en supposant que le fournisseur prend en charge les informations pertinentes fonctionnalité. Avant uniquement **Recordset** objets prennent en charge uniquement le [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) (méthode). Lorsque vous utilisez le **déplacer** méthodes à visiter chaque enregistrement (ou énumérer les **Recordset**), vous pouvez utiliser la **BOF** et **EOF** propriétés pour déterminer si vous avez dépassé le début ou la fin de la **Recordset**.  
  
 Avant d’utiliser toutes les fonctionnalités d’un **Recordset** de l’objet, vous devez appeler la **prend en charge** méthode sur l’objet à vérifier que la fonctionnalité est prise en charge ou disponible. Vous ne devez pas utiliser la fonctionnalité lors de la **prend en charge** méthode retourne la valeur false. Par exemple, vous pouvez utiliser la **MovePrevious** uniquement si de méthode `Recordset.Supports(adMovePrevious)` retourne **True**. Sinon, vous obtiendrez une erreur, car le **Recordset** objet fermé et la fonctionnalité devient indisponible sur l’instance. Si une fonctionnalité qui vous intéresse n’est pas pris en charge, **prend en charge** retournera la valeur false également. Dans ce cas, vous devez éviter d’appeler la propriété correspondante ou la méthode sur le **Recordset** objet.  
  
 **Jeu d’enregistrements** objets peuvent prendre en charge deux types de mise à jour : immédiate et par lot. Dans la mise à jour immédiate, toutes les modifications apportées aux données sont écrites immédiatement dans la source de données sous-jacente lorsque vous appelez le [mise à jour](../../../ado/reference/ado-api/update-method.md) (méthode). Vous pouvez également passer des tableaux de valeurs en tant que paramètres avec le [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) et **mettre à jour** méthodes et mettre à jour simultanément plusieurs champs dans un enregistrement.  
  
 Si un fournisseur prend en charge la mise à jour par lots, vous pouvez avoir le fournisseur de cache des modifications à plusieurs enregistrements et de les transmettre ensuite dans un seul appel à la base de données avec le [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) (méthode). Cela s’applique aux modifications apportées avec les **AddNew**, **mise à jour**, et [supprimer](../../../ado/reference/ado-api/delete-method-ado-recordset.md) méthodes. Après avoir appelé la **UpdateBatch** (méthode), vous pouvez utiliser la [état](../../../ado/reference/ado-api/status-property-ado-recordset.md) propriété à vérifier les conflits de données afin de les résoudre.  
  
> [!NOTE]
>  Pour exécuter une requête sans utiliser un [commande](../../../ado/reference/ado-api/command-object-ado.md) d’objet, passez une chaîne de requête à la **Open** méthode d’un **Recordset** objet. Toutefois, un **commande** objet est requis lorsque vous souhaitez conserver le texte de commande et exécuter de nouveau ou utiliser des paramètres de requête.  
  
 Le [Mode](../../../ado/reference/ado-api/mode-property-ado.md) propriété régit les autorisations d’accès.  
  
 Le **champs** collection est le membre par défaut de la **Recordset** objet. Par conséquent, les deux instructions suivantes sont équivalentes.  
  
```  
Debug.Print objRs.Fields.Item(0)  ' Both statements print   
Debug.Print objRs(0)              '  the Value of Item(0).  
```  
  
 Quand un **Recordset** objet est passé entre les processus, uniquement le **ensemble de lignes** valeurs sont marshalés et les propriétés de la **Recordset** objet sont ignorés. Au cours d’unmarshalling, le **ensemble de lignes** est décompressé dans nouvellement créé **Recordset** objet, qui définit également ses propriétés pour les valeurs par défaut.  
  
 Le **Recordset** objet est sécurisé pour le script.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés de l’objet Recordset, méthodes et événements](../../../ado/reference/ado-api/recordset-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Collection de champs (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Collection de propriétés (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Annexe A : fournisseurs](../../../ado/guide/appendixes/appendix-a-providers.md)
