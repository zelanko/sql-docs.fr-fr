---
title: Parameter, objet | Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 22af5fadda96adbe67c1c03aaa5cde3527df1113
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759995"
---
# <a name="parameter-object"></a>Objet Parameter
Représente un paramètre ou un argument associé à un objet de [commande](../../../ado/reference/ado-api/command-object-ado.md) basé sur une requête paramétrable ou une procédure stockée.  
  
## <a name="remarks"></a>Notes  
 De nombreux fournisseurs prennent en charge les commandes paramétrables. Il s’agit de commandes dans lesquelles l’action souhaitée est définie une seule fois, mais les variables (ou paramètres) sont utilisées pour modifier certains détails de la commande. Par exemple, une instruction SQL SELECT peut utiliser un paramètre pour définir les critères de correspondance d’une clause WHERE, et une autre pour définir le nom de colonne d’une clause SORT BY.  
  
 Les objets de **paramètres** représentent des paramètres associés à des requêtes paramétrables, ou les arguments in/out et les valeurs de retour des procédures stockées. Selon la fonctionnalité du fournisseur, certaines collections, méthodes ou propriétés d’un objet de **paramètre** peuvent ne pas être disponibles.  
  
 Avec les collections, les méthodes et les propriétés d’un objet **Parameter** , vous pouvez effectuer les opérations suivantes :  
  
-   Définit ou retourne le nom d’un paramètre avec la propriété [Name](../../../ado/reference/ado-api/name-property-ado.md) .  
  
-   Définit ou retourne la valeur d’un paramètre à l’aide de la propriété [value](../../../ado/reference/ado-api/value-property-ado.md) . La **valeur** est la propriété par défaut de l’objet de **paramètre** .  
  
-   Définissez ou retournez les caractéristiques des paramètres avec les propriétés [attributes](../../../ado/reference/ado-api/attributes-property-ado.md), [direction](../../../ado/reference/ado-api/direction-property.md), [précision](../../../ado/reference/ado-api/precision-property-ado.md), [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md), [taille](../../../ado/reference/ado-api/size-property-ado-parameter.md)et [type](../../../ado/reference/ado-api/type-property-ado.md) .  
  
-   Transmettre des données binaires ou caractères longues à un paramètre avec la méthode [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) .  
  
-   Accédez aux attributs spécifiques au fournisseur à l’aide de la collection [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) .  
  
 Si vous connaissez les noms et les propriétés des paramètres associés à la procédure stockée ou à la requête paramétrable que vous souhaitez appeler, vous pouvez utiliser la méthode [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) pour créer des objets **Parameter** avec les paramètres de propriété appropriés et utiliser la méthode [Append](../../../ado/reference/ado-api/append-method-ado.md) pour les ajouter à la collection [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md) . Cela vous permet de définir et de retourner des valeurs de paramètres sans avoir à appeler la méthode [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) sur la collection **Parameters** pour récupérer les informations sur les paramètres auprès du fournisseur, une opération potentiellement gourmande en ressources.  
  
 L’objet de **paramètre** n’est pas sûr pour l’écriture de scripts.  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de l’objet Parameter](../../../ado/reference/ado-api/parameter-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [CreateParameter, méthode (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Parameters, collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
