---
description: AddNew, méthode (ADO)
title: AddNew, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::AddNew
- Recordset15::raw_AddNew
helpviewer_keywords:
- AddNew method [ADO]
ms.assetid: a9f54be9-5763-45d0-a6eb-09981b03bc08
author: rothja
ms.author: jroth
ms.openlocfilehash: b3c6d6b33177f3c3db7c2d414759a5067a91b80d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451581"
---
# <a name="addnew-method-ado"></a>AddNew, méthode (ADO)
Crée un nouvel enregistrement pour un objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) pouvant être mis à jour.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
recordset.AddNew FieldList, Values  
```  
  
#### <a name="parameters"></a>Paramètres  
 *recordset*  
 Objet **Recordset** .  
  
 *FieldList*  
 facultatif. Un nom unique, ou un tableau de noms ou de positions ordinales des champs dans le nouvel enregistrement.  
  
 *Valeurs*  
 facultatif. Une valeur unique, ou un tableau de valeurs pour les champs dans le nouvel enregistrement. Si *FieldList* est un tableau, les *valeurs* doivent également être un tableau avec le même nombre de membres ; dans le cas contraire, une erreur se produit. L’ordre des noms de champs doit correspondre à l’ordre des valeurs de champ dans chaque tableau.  
  
## <a name="remarks"></a>Notes  
 Utilisez la méthode **AddNew** pour créer et initialiser un nouvel enregistrement. Utilisez la méthode [supports](../../../ado/reference/ado-api/supports-method.md) avec **adAddNew** (une valeur [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md) ) pour vérifier si vous pouvez ajouter des enregistrements à l’objet **Recordset** actuel.  
  
 Une fois que vous avez appelé la méthode **AddNew** , le nouvel enregistrement devient l’enregistrement actif et reste actif après l’appel de la méthode [Update](../../../ado/reference/ado-api/update-method.md) . Étant donné que le nouvel enregistrement est ajouté au **Recordset**, un appel à **MoveNext** après la mise à jour se déplacera au-delà de la fin de l’ensemble d' **enregistrements**, ce qui rend **EOF** true. Si l’objet **Recordset** ne prend pas en charge les signets, vous risquez de ne pas pouvoir accéder au nouvel enregistrement après l’avoir déplacé vers un autre enregistrement. Selon le type de curseur, vous devrez peut-être appeler la méthode [Requery](../../../ado/reference/ado-api/requery-method.md) pour rendre le nouvel enregistrement accessible.  
  
 Si vous appelez **AddNew** pendant la modification de l’enregistrement en cours ou lors de l’ajout d’un nouvel enregistrement, ADO appelle la méthode **Update** pour enregistrer les modifications apportées, puis crée le nouvel enregistrement.  
  
 Le comportement de la méthode **AddNew** dépend du mode de mise à jour de l’objet **Recordset** et du fait que vous passiez les arguments *FieldList* et *values* .  
  
 En *mode de mise à jour immédiate* (dans lequel le fournisseur enregistre les modifications apportées à la source de données sous-jacente une fois que vous avez appelé la méthode **Update** ), l’appel de la méthode **AddNew** sans arguments définit la propriété [EditMode](../../../ado/reference/ado-api/editmode-property.md) sur **adEditAdd** (une valeur [EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md) ). Le fournisseur met en cache toutes les modifications de valeur de champ localement. L’appel de la méthode **Update** publie le nouvel enregistrement dans la base de données et réinitialise la propriété **EditMode** sur **adEditNone** (une valeur **EditModeEnum** ). Si vous transmettez les arguments *FieldList* et *values* , ADO publie immédiatement le nouvel enregistrement dans la base de données (aucun appel de **mise à jour** n’est nécessaire); la valeur de la propriété **EditMode** ne change pas (**adEditNone**).  
  
 En *mode de mise à jour par lot* (dans lequel le fournisseur met en cache plusieurs modifications et les écrit dans la source de données sous-jacente uniquement lorsque vous appelez la méthode [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) ), l’appel de la méthode **AddNew** sans arguments affecte à la propriété **EditMode** la valeur **adEditAdd**. Le fournisseur met en cache toutes les modifications de valeur de champ localement. L’appel de la méthode de **mise à jour** ajoute le nouvel enregistrement au **Recordset**actuel, mais le fournisseur ne publie pas les modifications dans la base de données sous-jacente, ou réinitialisez **le mode de restauration en** **adEditNone**, jusqu’à ce que vous appeliez la méthode **UpdateBatch** . Si vous transmettez les arguments *FieldList* et *values* , ADO envoie le nouvel enregistrement au fournisseur pour le stockage dans un cache et définit le paramètre **EditMode** sur **adEditAdd**. vous devez appeler la méthode **UpdateBatch** pour poster le nouvel enregistrement dans la base de données sous-jacente.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la méthode AddNew avec la liste de champs et la liste de valeurs incluse, pour voir comment inclure la liste de champs et la liste de valeurs en tant que tableaux.  
  
```  
create table aa1 (intf int, charf char(10))  
insert into aa1 values (2, 'aa')  
  
Dim cn As New adodb.Connection  
Dim rs As New adodb.Recordset  
Dim cmd As New adodb.Command  
  
cn.ConnectionString = "Provider=SQLOLEDB;Data Source=alexverb2;uid=sa;pwd=foo$bar00;"  
  
cn.Open  
rs.Open "select * from xxx..aa1", cn, adOpenKeyset, adLockOptimistic  
  
Dim fieldsArray(1) As Variant  
fieldsArray(0) = "intf"  
fieldsArray(1) = "charf"  
Dim values(1) As Variant  
values(0) = 4  
values(1) = "as"  
rs.AddNew fieldsArray, values  
rs.Update  
```  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [AddNew, exemple de méthode (VB)](../../../ado/reference/ado-api/addnew-method-example-vb.md)   
 [AddNew, exemple de méthode (VBScript)](../../../ado/reference/ado-api/addnew-method-example-vbscript.md)   
 [AddNew, exemple de méthode (VC + +)](../../../ado/reference/ado-api/addnew-method-example-vc.md)   
 [CancelUpdate, méthode (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [EditMode, propriété](../../../ado/reference/ado-api/editmode-property.md)   
 [Requery, méthode](../../../ado/reference/ado-api/requery-method.md)   
 [Prend en charge la méthode](../../../ado/reference/ado-api/supports-method.md)   
 [Update, méthode](../../../ado/reference/ado-api/update-method.md)   
 [UpdateBatch, méthode](../../../ado/reference/ado-api/updatebatch-method.md)
