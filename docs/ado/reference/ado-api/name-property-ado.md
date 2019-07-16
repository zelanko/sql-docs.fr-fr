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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a919bb377eee2da1c3c1a65e85ddfb9807ed8d50
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67918032"
---
# <a name="name-property-ado"></a>Name, propriété (ADO)
Indique le nom d’un objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **chaîne** valeur qui indique le nom d’un objet.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **nom** propriété à attribuer un nom à ou à récupérer le nom d’un **commande**, **propriété**, **champ**, ou **paramètre**  objet.  
  
 La valeur est en lecture/écriture sur un **commande** objet et en lecture seule sur un **propriété** objet.  
  
 Pour un **champ** objet, **nom** est généralement en lecture seule. Toutefois, pour les nouveaux **champ** les objets qui ont été ajoutées à la [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md), **nom** est en lecture/écriture uniquement après le [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété pour le **champ** a été spécifié et le fournisseur de données a correctement ajouté le nouveau **champ** en appelant le [ Mise à jour](../../../ado/reference/ado-api/update-method.md) méthode de la **champs** collection.  
  
 Pour **paramètre** objets pas encore ajouté à la [paramètres](../../../ado/reference/ado-api/parameters-collection-ado.md) collection, le **nom** propriété est en lecture/écriture. Pour ajouter **paramètre** objets et toutes les autres, le **nom** propriété est en lecture seule. Noms n’ont pas à être unique au sein d’une collection.  
  
 Vous pouvez récupérer le **nom** propriété d’un objet par référence ordinale, après quoi vous pouvez faire référence à l’objet directement par nom. Par exemple, si `rstMain.Properties(20).Name` génère `Updatability`, vous pouvez ensuite référencer cette propriété en tant que `rstMain.Properties("Updatability")`.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Field, objet](../../../ado/reference/ado-api/field-object.md)|  
|[Parameter, objet](../../../ado/reference/ado-api/parameter-object.md)|[Property, objet (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs et des exemples de propriétés de nom (VB)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vb.md)   
 [Attributs et des exemples de propriétés de nom (VC ++)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vc.md)   
