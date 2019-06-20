---
title: CreateParameter, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::raw_CreateParameter
- Command15::CreateParameter
helpviewer_keywords:
- CreateParameter method [RDS]
ms.assetid: 9666fdcc-0544-4ed7-a97b-c415f2a56d7e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 251c35977421d63027fbc9d6042e193125da854d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66695635"
---
# <a name="createparameter-method-ado"></a>CreateParameter, méthode (ADO)
Crée un [paramètre](../../../ado/reference/ado-api/parameter-object.md) objet avec les propriétés spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set parameter = command.CreateParameter (Name, Type, Direction, Size, Value)  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un **paramètre** objet.  
  
#### <a name="parameters"></a>Paramètres  
 *Nom*  
 Facultatif. Un **chaîne** valeur qui contienne le nom de la **paramètre** objet.  
  
 *Type*  
 Facultatif. Un [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) valeur qui spécifie le type de données de la **paramètre** objet.  
  
 *Sens*  
 Facultatif. Un [ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md) valeur qui spécifie le type de **paramètre** objet.  
  
 *Taille*  
 Facultatif. Un **Long** valeur qui spécifie la longueur maximale de la valeur du paramètre en caractères ou octets.  
  
 *Valeur*  
 Facultatif. Un **Variant** qui spécifie la valeur pour le **paramètre** objet.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **CreateParameter** pour créer une nouvelle méthode **paramètre** objet avec un nom spécifié, le type, la direction, la taille et le valeur. Toutes les valeurs passées dans les arguments sont écrits correspondant **paramètre** propriétés.  
  
 Cette méthode n’ajoute pas automatiquement le **paramètre** de l’objet à la **paramètres** collection d’un [commande](../../../ado/reference/ado-api/command-object-ado.md) objet. Cela vous permet de définir des propriétés supplémentaires dont ADO valeurs validera lorsque vous ajoutez le **paramètre** objet à la collection.  
  
 Si vous spécifiez un type de données de longueur variable dans la *Type* argument, vous devez soit passer un *taille* argument ou un ensemble la [taille](../../../ado/reference/ado-api/size-property-ado-parameter.md) propriété de le **paramètre**  objet avant de l’ajouter à la **paramètres** collection ; sinon, une erreur se produit.  
  
 Si vous spécifiez un type de données numériques (**adNumeric** ou **adDecimal**) dans le *Type* argument, vous devez également définir le [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) et [Précision](../../../ado/reference/ado-api/precision-property-ado.md) propriétés.  
  
## <a name="applies-to"></a>S'applique à  
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Append et CreateParameter, exemple de méthodes (VB)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [Append et CreateParameter, exemple de méthodes (VC ++)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [Append, méthode (ADO)](../../../ado/reference/ado-api/append-method-ado.md)   
 [Objet de paramètre](../../../ado/reference/ado-api/parameter-object.md)   
 [Parameters, collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
