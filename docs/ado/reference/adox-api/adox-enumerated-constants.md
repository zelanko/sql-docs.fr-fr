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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bdbd67d5e4d7d4647b92b32590a5258de038c80f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63308299"
---
# <a name="adox-enumerated-constants"></a>Constantes énumérées ADOX
Pour faciliter le débogage, les constantes énumérées ADOX répertorient une valeur pour chaque constante. Toutefois, cette valeur est purement indicative et peut changer d’une version d’ADOX à un autre. Votre code doit uniquement dépendre du nom, pas la valeur réelle, de constantes énumérées.  
  
 Les constantes énumérées suivantes sont définies.  
  
|Énumération|Description|  
|-----------------|-----------------|  
|[ActionEnum](../../../ado/reference/adox-api/actionenum.md)|Spécifie le type d’action à effectuer lorsque **SetPermissions** est appelée.|  
|[AllowNullsEnum](../../../ado/reference/adox-api/allownullsenum.md)|Spécifie si les enregistrements avec des valeurs null sont indexés.|  
|[ColumnAttributesEnum](../../../ado/reference/adox-api/columnattributesenum.md)|Spécifie les caractéristiques d’un **colonne**.|  
|[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)|Spécifie le type de données d’un **champ**, **paramètre**, ou **propriété**.|  
|[InheritTypeEnum](../../../ado/reference/adox-api/inherittypeenum.md)|Spécifie comment les objets héritent des autorisations définies avec **SetPermissions**.|  
|[KeyTypeEnum](../../../ado/reference/adox-api/keytypeenum.md)|Spécifie le type de **clé**: primaire, étrangère ou unique.|  
|[ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md)|Spécifie le type d’objet de base de données pour lequel définir des autorisations ou la propriété.|  
|[RightsEnum](../../../ado/reference/adox-api/rightsenum.md)|Spécifie les droits ou les autorisations pour un groupe ou utilisateur sur un objet.|  
|[RuleEnum](../../../ado/reference/adox-api/ruleenum.md)|Spécifie la règle à appliquer quand une **clé** est supprimé.|  
|[SortOrderEnum](../../../ado/reference/adox-api/sortorderenum.md)|Spécifie l’ordre de tri pour une colonne indexée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des API ADOX](../../../ado/reference/adox-api/adox-api-reference.md)   
 [Extensions ADO pour le langage de définition de données et la sécurité (ADOX)](../../../ado/guide/extensions/ado-extensions-for-data-definition-language-and-security-adox.md)
