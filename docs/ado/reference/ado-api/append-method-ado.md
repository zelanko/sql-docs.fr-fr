---
title: Append, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _DynaCollection::Append
helpviewer_keywords:
- Append method [ADO]
ms.assetid: f8a9bbed-ba9c-4698-945d-317ad22d2e92
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 17fa0ff30e8dcdbf7ea67080f17c3e066bba8605
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67920674"
---
# <a name="append-method-ado"></a>Append, méthode (ADO)
Ajoute un objet à une collection. Si la collection est [champs](../../../ado/reference/ado-api/fields-collection-ado.md), un nouveau [champ](../../../ado/reference/ado-api/field-object.md) objet peut être créé avant d’être ajoutée à la collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
collection.Append object  
fields.Append Name, Type, DefinedSize, Attrib, FieldValue  
```  
  
#### <a name="parameters"></a>Paramètres  
 *collection*  
 Un objet de collection.  
  
 *fields*  
 Un **champs** collection.  
  
 *object*  
 Une variable objet qui représente l’objet à ajouter.  
  
 *Nom*  
 Un **chaîne** valeur qui contient le nom du nouveau **champ** de l’objet, et doit être pas le même nom que tout autre objet dans *champs*.  
  
 *Type*  
 Un [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) valeur, dont la valeur par défaut est **adEmpty**, qui spécifie le type de données du nouveau champ. Les types de données suivants ne sont pas pris en charge par ADO et de ne doit pas être utilisé lorsque l’ajout de nouveaux champs à un [objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md): **adIDispatch**, **adIUnknown**, **adVariant**.  
  
 *DefinedSize*  
 Facultatif. Un **Long** valeur qui représente la taille définie, en caractères ou octets, du nouveau champ. La valeur par défaut pour ce paramètre est dérivée de *Type*. Les champs qui ont un *DefinedSize* supérieure à 255 octets sont traitées en tant que colonnes de longueur variable. La valeur par défaut pour *DefinedSize* n’est pas spécifié.  
  
 *Attrib*  
 facultatif. Un [FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md) valeur, dont la valeur par défaut est **adFldDefault**, qui spécifie les attributs pour le nouveau champ. Si cette valeur n’est pas spécifiée, le champ contient les attributs dérivés de *Type*.  
  
 *FieldValue*  
 facultatif. Un **Variant** qui représente la valeur du nouveau champ. Si non spécifié, le champ est ajouté avec une valeur null.  
  
## <a name="remarks"></a>Notes  
  
## <a name="parameters-collection"></a>Collection Parameters  
 Vous devez définir le [Type](../../../ado/reference/ado-api/type-property-ado.md) propriété d’un [paramètre](../../../ado/reference/ado-api/parameter-object.md) objet avant de l’ajouter à la [paramètres](../../../ado/reference/ado-api/parameters-collection-ado.md) collection. Si vous sélectionnez un type de données de longueur variable, vous devez également définir le [taille](../../../ado/reference/ado-api/size-property-ado-parameter.md) propriété une valeur supérieure à zéro.  
  
 Décrivant les paramètres réduit les appels au fournisseur et améliore ainsi les performances lorsque vous utilisez des procédures stockées ou des requêtes paramétrables. Toutefois, vous devez connaître les propriétés des paramètres associés à la procédure stockée ou la requête paramétrée que vous souhaitez appeler.  
  
 Utiliser le [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) méthode pour créer **paramètre** objets avec les paramètres de propriété approprié et l’utilisation du **Append** méthode pour les ajouter à la [ Paramètres](../../../ado/reference/ado-api/parameters-collection-ado.md) collection. Cela vous permet de définir et retourner des valeurs de paramètre sans devoir appeler le fournisseur pour les informations de paramètre. Si vous écrivez un fournisseur qui ne fournit pas d’informations sur les paramètres, vous devez utiliser cette méthode pour remplir manuellement la **paramètres** collection afin d’utiliser des paramètres.  
  
## <a name="fields-collection"></a>Collection Fields  
 Le *FieldValue* paramètre est valide uniquement lorsque vous ajoutez un **champ** de l’objet à un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) de l’objet, pas à un **Recordset** objet. Avec un **enregistrement** de l’objet, vous pouvez ajouter des champs et fournir des valeurs en même temps. Avec un **Recordset** de l’objet, vous devez créer des champs lors de la **Recordset** est fermé et puis ouvrez le **Recordset** et affecter des valeurs aux champs.  
  
> [!NOTE]
>  Pour les nouveaux **champ** les objets qui ont été ajoutées à la **champs** collection d’un **enregistrement** objet, le [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété doit être définie avant toute autre **champ** propriétés peuvent être spécifiées. Tout d’abord, une valeur spécifique pour le **valeur** propriété doit avoir été affectée et [mise à jour](../../../ado/reference/ado-api/update-method.md) sur le **champs** collection appelée. Ensuite, d’autres propriétés, telles que [Type](../../../ado/reference/ado-api/type-property-ado.md) ou [attributs](../../../ado/reference/ado-api/attributes-property-ado.md) sont accessibles. **Champ** objets des types de données suivantes (**DataTypeEnum**) ne peut pas être ajouté à la **champs** collection et provoque une erreur se produise : **adArray**, **adChapter**, **adEmpty**, **adPropVariant**, et **adUserDefined**. En outre, les types de données suivants ne sont pas pris en charge par ADO : **adIDispatch**, **adIUnknown**, et **adIVariant**. Pour ces types, aucune erreur ne se produira lorsqu’il est ajouté, mais l’utilisation peut produire des résultats imprévisibles, notamment les fuites de mémoire.  
  
## <a name="recordset"></a>Ensemble d'enregistrements  
 Si vous ne définissez pas la [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété avant d’appeler le **Append** (méthode), **CursorLocation** sera défini sur **adUseClient** () un [CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md) valeur) automatiquement lors de la [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) méthode de la [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet est appelé.  
  
 Une erreur d’exécution se produit si le **Append** méthode est appelée sur le **champs** collection ouvert **Recordset**, ou sur un **Recordset** où les [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) propriété a été définie. Vous pouvez uniquement ajouter des champs à un **Recordset** qui n’est pas ouvert et n’a pas encore été connecté à une source de données. C’est généralement le cas lorsqu’un **Recordset** objet est créé avec le [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md) méthode ou assigné à une variable objet.  
  
## <a name="record"></a>Enregistrement  
 Une erreur d’exécution ne produira pas si le **Append** méthode est appelée sur le **champs** collection ouvert **enregistrement**. Le nouveau champ est ajouté à la **champs** collection de la **enregistrement** objet. Si le **enregistrement** a été dérivé un **Recordset**, le nouveau champ n’apparaîtra pas dans le **champs** collection de la **Recordset** objet.  
  
 Un champ inexistant peut être créé et ajouté à la **champs** collection en affectant une valeur à l’objet de champ comme s’il existait déjà dans la collection. Cette affectation déclenche la création automatique et l’ajout de la **champ** objet, puis l’attribution seront terminée.  
  
 Après l’ajout un **champ** à la **champs** collection d’un **enregistrement** de l’objet, appelez le **mise à jour** méthode de la **champs**  collection pour enregistrer la modification.  
  
## <a name="applies-to"></a>S'applique à  
  
- [Fields, collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
- [Parameters, collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Append et CreateParameter, exemple de méthodes (VB)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [Append et CreateParameter, exemple de méthodes (VC ++)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [CreateParameter, méthode (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [DELETE, méthode (Collection de champs ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [DELETE, méthode (Collection de paramètres ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [DELETE, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Update, méthode](../../../ado/reference/ado-api/update-method.md)
