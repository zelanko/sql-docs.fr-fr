---
title: Name, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Name
- Field20::Name
helpviewer_keywords:
- Name property [ADO]
ms.assetid: cfd0e29c-8310-44ab-85c3-5761184b865d
author: rothja
ms.author: jroth
ms.openlocfilehash: 38846bcb832df7cc535d35d8f07fb636f2db37f7
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762420"
---
# <a name="name-property-ado"></a>Name, propriété (ADO)
Indique le nom d’un objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **chaîne** qui indique le nom d’un objet.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **Name** pour attribuer un nom à une **commande**, une **propriété**, un **champ**ou un objet **Parameter** ou pour en récupérer le nom.  
  
 La valeur est en lecture/écriture sur un objet **Command** et en lecture seule sur un objet **Property** .  
  
 Pour un objet **Field** , **Name** est généralement en lecture seule. Toutefois, pour les nouveaux objets de **champ** qui ont été ajoutés à la collection de [champs](../../../ado/reference/ado-api/fields-collection-ado.md) d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md), le **nom** est en lecture/écriture uniquement après la spécification de la propriété [value](../../../ado/reference/ado-api/value-property-ado.md) du **champ** et que le fournisseur de données a correctement ajouté le nouveau **champ** en appelant la méthode [Update](../../../ado/reference/ado-api/update-method.md) de la collection **Fields** .  
  
 Pour les objets de **paramètre** qui n’ont pas encore été ajoutés à la collection [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md) , la propriété **Name** est en lecture/écriture. Pour les objets de **paramètre** ajoutés et tous les autres objets, la propriété **Name** est en lecture seule. Les noms ne doivent pas nécessairement être uniques dans une collection.  
  
 Vous pouvez récupérer la propriété **Name** d’un objet à l’aide d’une référence ordinale, après laquelle vous pouvez faire référence à l’objet directement par son nom. Par exemple, si `rstMain.Properties(20).Name` donne `Updatability` , vous pouvez ensuite faire référence à cette propriété en tant que `rstMain.Properties("Updatability")` .  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Objet Field](../../../ado/reference/ado-api/field-object.md)|  
|[Objet Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Property, objet (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Attributes et Name, exemple de propriétés (VB)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vb.md)   
 [Attributes et Name, exemple de propriétés (VC + +)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vc.md)   
