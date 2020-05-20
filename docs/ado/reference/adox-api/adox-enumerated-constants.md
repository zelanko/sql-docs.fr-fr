---
title: Constantes énumérées ADOX | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- enumerated constants [ADOX]
ms.assetid: 9d91f511-d46f-44ef-97ef-77bf93836186
author: rothja
ms.author: jroth
ms.openlocfilehash: 84a03af49152bc305f62aceb149d904ef0acf9a0
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764140"
---
# <a name="adox-enumerated-constants"></a>Constantes énumérées ADOX
Pour faciliter le débogage, les constantes énumérées ADOX répertorient une valeur pour chaque constante. Toutefois, cette valeur est purement consultative et peut passer d’une version d’ADOX à une autre. Votre code ne doit dépendre que du nom, et non de la valeur réelle, des constantes énumérées.  
  
 Les constantes énumérées suivantes sont définies.  
  
|Énumération|Description|  
|-----------------|-----------------|  
|[ActionEnum](../../../ado/reference/adox-api/actionenum.md)|Spécifie le type d’action à effectuer lorsque l’opération **SetPermissions** est appelée.|  
|[AllowNullsEnum](../../../ado/reference/adox-api/allownullsenum.md)|Spécifie si les enregistrements avec des valeurs NULL sont indexés.|  
|[ColumnAttributesEnum](../../../ado/reference/adox-api/columnattributesenum.md)|Spécifie les caractéristiques d’une **colonne**.|  
|[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)|Spécifie le type de données d’un **champ**, d’un **paramètre**ou d’une **propriété**.|  
|[InheritTypeEnum](../../../ado/reference/adox-api/inherittypeenum.md)|Spécifie la manière dont les objets héritent des autorisations définies avec **SetPermissions**.|  
|[KeyTypeEnum](../../../ado/reference/adox-api/keytypeenum.md)|Spécifie le type de **clé**: primaire, étrangère ou unique.|  
|[ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md)|Spécifie le type d’objet de base de données pour lequel définir des autorisations ou la propriété.|  
|[RightsEnum](../../../ado/reference/adox-api/rightsenum.md)|Spécifie les droits ou les autorisations pour un groupe ou un utilisateur sur un objet.|  
|[RuleEnum](../../../ado/reference/adox-api/ruleenum.md)|Spécifie la règle à suivre lorsqu’une **clé** est supprimée.|  
|[SortOrderEnum](../../../ado/reference/adox-api/sortorderenum.md)|Spécifie la séquence de tri pour une colonne indexée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’API ADOX](../../../ado/reference/adox-api/adox-api-reference.md)   
 [Extensions ADO pour le langage de définition de données et la sécurité (ADOX)](../../../ado/guide/extensions/ado-extensions-for-data-definition-language-and-security-adox.md)
