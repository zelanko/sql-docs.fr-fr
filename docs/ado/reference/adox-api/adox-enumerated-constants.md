---
description: Constantes énumérées ADOX
title: Constantes énumérées ADOX | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- enumerated constants [ADOX]
ms.assetid: 9d91f511-d46f-44ef-97ef-77bf93836186
author: rothja
ms.author: jroth
ms.openlocfilehash: d4a6ab82630c058db9bbb0b05ca9ee5713a4c8ab
ms.sourcegitcommit: 370cab80fba17c15fb0bceed9f80cb099017e000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97641179"
---
# <a name="adox-enumerated-constants"></a>Constantes énumérées ADOX
Pour faciliter le débogage, les constantes énumérées ADOX répertorient une valeur pour chaque constante. Toutefois, cette valeur est purement consultative et peut passer d’une version d’ADOX à une autre. Votre code ne doit dépendre que du nom, et non de la valeur réelle, des constantes énumérées.  
  
 Les constantes énumérées suivantes sont définies.  
  
|Énumération|Description|  
|-----------------|-----------------|  
|[ActionEnum](./actionenum.md)|Spécifie le type d’action à effectuer lorsque l’opération **SetPermissions** est appelée.|  
|[AllowNullsEnum](./allownullsenum.md)|Spécifie si les enregistrements avec des valeurs NULL sont indexés.|  
|[ColumnAttributesEnum](./columnattributesenum.md)|Spécifie les caractéristiques d’une **colonne**.|  
|[DataTypeEnum](../ado-api/datatypeenum.md)|Spécifie le type de données d’un **champ**, d’un **paramètre** ou d’une **propriété**.|  
|[InheritTypeEnum](./inherittypeenum.md)|Spécifie la manière dont les objets héritent des autorisations définies avec **SetPermissions**.|  
|[KeyTypeEnum](./keytypeenum.md)|Spécifie le type de **clé**: primaire, étrangère ou unique.|  
|[ObjectTypeEnum](./objecttypeenum.md)|Spécifie le type d’objet de base de données pour lequel définir des autorisations ou la propriété.|  
|[RightsEnum](./rightsenum.md)|Spécifie les droits ou les autorisations pour un groupe ou un utilisateur sur un objet.|  
|[RuleEnum](./ruleenum.md)|Spécifie la règle à suivre lorsqu’une **clé** est supprimée.|  
|[SortOrderEnum](./sortorderenum.md)|Spécifie la séquence de tri pour une colonne indexée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’API ADOX](./adox-object-model.md)   
 [Extensions ADO pour le langage de définition de données et la sécurité (ADOX)](../../guide/extensions/ado-extensions-for-data-definition-language-and-security-adox.md)