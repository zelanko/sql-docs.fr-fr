---
title: Objet de paramètre | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Parameter
helpviewer_keywords:
- Parameter object [ADO]
ms.assetid: e010e794-7f0f-4026-8b5b-37328e437d63
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 15df27e3dc48decf743a78dd4d147a22dc7cf276
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931664"
---
# <a name="parameter-object"></a>Objet Parameter
Représente un paramètre ou un argument associé à un [commande](../../../ado/reference/ado-api/command-object-ado.md) objet basé sur une procédure stockée ou une requête paramétrable.  
  
## <a name="remarks"></a>Notes  
 De nombreux fournisseurs prennent en charge les commandes paramétrables. Il s’agit de commandes dans lequel l’action souhaitée est définie une seule fois, mais les variables (ou paramètres) sont utilisées pour modifier certains détails de la commande. Par exemple, une instruction SQL SELECT peut utiliser un paramètre pour définir les critères de correspondance d’une clause WHERE et l’autre pour définir le nom de colonne pour une clause de tri.  
  
 **Paramètre** objets représentent des paramètres associés aux requêtes paramétrables ou les arguments d’entrée/sortie et les valeurs de retour de procédures stockées. Selon les fonctionnalités du fournisseur, certaines collections, les méthodes ou les propriétés d’un **paramètre** objet n’est peut-être pas disponible.  
  
 Avec les collections, les méthodes et les propriétés d’un **paramètre** de l’objet, vous pouvez procédez comme suit :  
  
-   Définir ou retourner le nom d’un paramètre avec le [nom](../../../ado/reference/ado-api/name-property-ado.md) propriété.  
  
-   Définir ou retourner la valeur d’un paramètre avec le [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété. **Valeur** est la propriété par défaut de la **paramètre** objet.  
  
-   Définir ou retourner les caractéristiques des paramètres avec le [attributs](../../../ado/reference/ado-api/attributes-property-ado.md), [Direction](../../../ado/reference/ado-api/direction-property.md), [précision](../../../ado/reference/ado-api/precision-property-ado.md), [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md), [ Taille](../../../ado/reference/ado-api/size-property-ado-parameter.md), et [Type](../../../ado/reference/ado-api/type-property-ado.md) propriétés.  
  
-   Passer des données binaires longues ou de caractères à un paramètre avec le [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) (méthode).  
  
-   Accéder aux attributs spécifiques au fournisseur à l’aide de la [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection.  
  
 Si vous connaissez les noms et les propriétés des paramètres associés avec la procédure stockée ou une requête paramétrable que vous souhaitez appeler, vous pouvez utiliser la [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) méthode pour créer **paramètre** objets avec les paramètres de propriété approprié et l’utilisation du [Append](../../../ado/reference/ado-api/append-method-ado.md) méthode pour les ajouter à la [paramètres](../../../ado/reference/ado-api/parameters-collection-ado.md) collection. Cela vous permet de définir et retourner des valeurs de paramètre sans devoir appeler le [Actualiser](../../../ado/reference/ado-api/refresh-method-ado.md) méthode sur le **paramètres** collection pour récupérer les informations de paramètre à partir du fournisseur, un potentiellement opération de gourmandes en ressources.  
  
 Le **paramètre** objet n’est pas sécurisé pour le script.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés de l’objet paramètre, méthodes et événements](../../../ado/reference/ado-api/parameter-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [CreateParameter, méthode (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Collection de paramètres (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
