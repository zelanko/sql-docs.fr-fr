---
title: CommandTypeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CommandTypeEnum
helpviewer_keywords:
- CommandTypeEnum enumeration [ADO]
ms.assetid: 4b1feb9c-a855-40fe-a906-efe688687e9f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5a2de155d9c4a61246245b2c7f9c3c73a535994a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67919688"
---
# <a name="commandtypeenum"></a>CommandTypeEnum
Spécifie comment un argument de commande doit être interprété.  
  
 Il est important de valider les valeurs *CommandString* fournies par l’utilisateur pour éviter aux utilisateurs de l’application d’injecter des commandes potentiellement dangereuses pour l’exécution d’ADO.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adCmdUnspecified**|-1|Ne spécifie pas l’argument de type de commande.|  
|**adCmdText**|1|Évalue [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) comme définition textuelle d’une commande ou d’un appel de procédure stockée.|  
|**adCmdTable**|2|Évalue **CommandText** en tant que nom de table dont les colonnes sont toutes retournées par une requête SQL générée en interne.|  
|**adCmdStoredProc**|4|Évalue **CommandText** comme nom de procédure stockée.|  
|**adCmdUnknown**|8|Par défaut. Indique que le type de commande dans la propriété **CommandText** n’est pas connu.<br /><br /> Lorsque le type de commande n’est pas connu, ADO effectue plusieurs tentatives pour interpréter le **CommandText**.<br /><br /> -   **CommandText** est interprété comme une définition textuelle d’une commande ou d’un appel de procédure stockée. Il s’agit du même comportement que **adCmdText**.<br />-   **CommandText** est le nom d’une procédure stockée. Il s’agit du même comportement que **adCmdStoredProc**.<br />-   **CommandText** est interprété comme le nom d’une table. Toutes les colonnes sont retournées par une requête SQL générée en interne. Il s’agit du même comportement que **adCmdTable**.|  
|**adCmdFile**|256|Évalue **CommandText** comme nom de fichier d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)stocké de manière permanente. Utilisé avec le **Recordset.** [Ouvrir](../../../ado/reference/ado-api/open-method-ado-recordset.md) ou [Actualiser](../../../ado/reference/ado-api/requery-method.md) uniquement.|  
|**adCmdTableDirect**|512|Évalue **CommandText** en tant que nom de table dont les colonnes sont toutes retournées. Utilisé avec **Recordset. Open** ou **Requery** uniquement. Pour utiliser la méthode [Seek](../../../ado/reference/ado-api/seek-method.md) , vous devez ouvrir le **jeu d’enregistrements** avec **adCmdTableDirect**.<br /><br /> Cette valeur ne peut pas être combinée avec la valeur [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) **adAsyncExecute**.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums.CommandType.UNSPECIFIED|  
|AdoEnums.CommandType.TEXT|  
|AdoEnums.CommandType.TABLE|  
|AdoEnums.CommandType.STOREDPROC|  
|AdoEnums.CommandType.UNKNOWN|  
|AdoEnums.CommandType.FILE|  
|AdoEnums.CommandType.TABLEDIRECT|  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[CommandType, propriété (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)|[Execute, méthode (commande ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[Execute, méthode (objet Connection ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|[Open, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[Requery, méthode](../../../ado/reference/ado-api/requery-method.md)||
