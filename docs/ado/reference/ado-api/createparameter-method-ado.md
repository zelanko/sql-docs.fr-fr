---
title: "CreateParameter, méthode (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Command15::raw_CreateParameter
- Command15::CreateParameter
helpviewer_keywords: CreateParameter method [RDS]
ms.assetid: 9666fdcc-0544-4ed7-a97b-c415f2a56d7e
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 929d7e91566aa18938a64f1085b1d77153205898
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="createparameter-method-ado"></a>CreateParameter, méthode (ADO)
Crée un nouveau [paramètre](../../../ado/reference/ado-api/parameter-object.md) objet avec les propriétés spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set parameter = command.CreateParameter (Name, Type, Direction, Size, Value)  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un **paramètre** objet.  
  
#### <a name="parameters"></a>Paramètres  
 *Nom*  
 Ce paramètre est facultatif. A **chaîne** valeur qui contient le nom de la **paramètre** objet.  
  
 *Type*  
 Ce paramètre est facultatif. A [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) valeur qui spécifie le type de données de la **paramètre** objet.  
  
 *Direction*  
 Ce paramètre est facultatif. A [ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md) valeur qui spécifie le type de **paramètre** objet.  
  
 *Taille*  
 Ce paramètre est facultatif. A **Long** valeur qui spécifie la longueur maximale de la valeur du paramètre en caractères ou en octets.  
  
 *Valeur*  
 Ce paramètre est facultatif. A **Variant** qui spécifie la valeur pour le **paramètre** objet.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **CreateParameter** pour créer une nouvelle méthode **paramètre** objet avec le nom spécifié, direction, taille, valeur et un type. Toutes les valeurs passées dans les arguments sont écrites correspondant **paramètre** propriétés.  
  
 Cette méthode n’ajoute pas automatiquement le **paramètre** de l’objet à la **paramètres** collection d’un [commande](../../../ado/reference/ado-api/command-object-ado.md) objet. Cela vous permet de définir des propriétés supplémentaires dont ADO de valeurs valide lorsque vous ajoutez le **paramètre** objet à la collection.  
  
 Si vous spécifiez un type de données de longueur variable dans la *Type* argument, vous devez soit passer un *taille* argument ou un jeu le [taille](../../../ado/reference/ado-api/size-property-ado-parameter.md) propriété de le **paramètre**  objet avant de l’ajouter à la **paramètres** collection ; sinon, une erreur se produit.  
  
 Si vous spécifiez un type de données numérique (**adNumeric** ou **adDecimal**) dans le *Type* argument, alors vous devez également définir le [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) et [Précision](../../../ado/reference/ado-api/precision-property-ado.md) propriétés.  
  
## <a name="applies-to"></a>S'applique à  
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Append et CreateParameter, méthodes-exemple (VB)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [Append et CreateParameter, méthodes-exemple (VC ++)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [Append (méthode) (ADO)](../../../ado/reference/ado-api/append-method-ado.md)   
 [Objet de paramètre](../../../ado/reference/ado-api/parameter-object.md)   
 [Parameters, collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
