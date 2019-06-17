---
title: FieldAttributeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FieldAttributeEnum
helpviewer_keywords:
- FieldAttributeEnum enumeration [ADO]
ms.assetid: 6e34d886-005a-40dc-bd5c-6adcbf81e5cd
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e0f6984c464c08518c7b3143986a041b195cce69
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66695062"
---
# <a name="fieldattributeenum"></a>FieldAttributeEnum
Spécifie un ou plusieurs attributs d’un [champ](../../../ado/reference/ado-api/field-object.md) objet.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adFldCacheDeferred**|0x1000|Indique que le fournisseur met en cache les valeurs de champ et que les lectures suivantes sont effectuées à partir du cache.|  
|**adFldFixed**|0x10|Indique que le champ contienne des données de longueur fixe.|  
|**adFldIsChapter**|0x2000|Indique que le champ contient une valeur de chapitre, qui spécifie un jeu d’enregistrements enfants spécifiques liée à ce champ parent. En général, les champs de chapitre sont utilisés avec la mise en forme des données ou des filtres.|  
|**adFldIsCollection**|0x40000|Indique que le champ spécifie que la ressource représentée par l’enregistrement est une collection d’autres ressources, tel qu’un dossier, plutôt que d’une ressource simple, tel qu’un fichier texte.|  
|**adFldKeyColumn**|0x8000|Indique que le champ spécifie tout ou partie de la clé primaire de la colonne.|  
|**adFldIsDefaultStream**|0x20000|Indique que le champ contienne le flux par défaut pour la ressource représentée par l’enregistrement. Par exemple, le flux de valeur par défaut peut être le contenu HTML d’un dossier racine sur un site Web, qui est automatiquement servi lorsque l’URL racine est spécifiée.|  
|**adFldIsNullable**|0x20|Indique que le champ accepte des valeurs null.|  
|**adFldIsRowURL**|0x10000|Indique que le champ contient l’URL que les noms de la ressource à partir du magasin de données représenté par l’enregistrement.|  
|**adFldLong**|0x80|Indique que le champ est un champ binaire longue. Indique également que vous pouvez utiliser la [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) et [GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md) méthodes.|  
|**adFldMayBeNull**|0x40|Indique que vous pouvez lire les valeurs null à partir du champ.|  
|**adFldMayDefer**|0x2|Indique que le champ est différé qu’est, les valeurs de champ ne sont pas récupérées à partir de la source de données avec l’intégralité de l’enregistrement, mais uniquement lorsque vous y accédez de manière explicite.|  
|**adFldNegativeScale**|0x4000|Indique que le champ représente une valeur numérique à partir d’une colonne qui prend en charge les valeurs d’échelle négative. La mise à l’échelle est spécifiée par le [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) propriété.|  
|**adFldRowID**|0x100|Indique que le champ contient un identificateur de ligne persistant qui ne peuvent pas être écrits à et n’a aucune valeur significative, excepté pour identifier la ligne (par exemple, un numéro d’enregistrement, identificateur unique et ainsi de suite).|  
|**adFldRowVersion**|0x200|Indique que le champ contienne un cachet de date ou d’heure utilisé pour effectuer le suivi des mises à jour.|  
|**adFldUnknownUpdatable**|0x8|Indique que le fournisseur ne peut pas déterminer si vous pouvez écrire dans le champ.|  
|**adFldUnspecified**|-0xFFFFFFFF 1|Indique que le fournisseur ne spécifie pas les attributs de champ.|  
|**adFldUpdatable**|0x4|Indique que vous pouvez écrire dans le champ.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.FieldAttribute.CACHEDEFERRED|  
|AdoEnums.FieldAttribute.FIXED|  
|AdoEnums.FieldAttribute.ISNULLABLE|  
|AdoEnums.FieldAttribute.LONG|  
|AdoEnums.FieldAttribute.MAYBENULL|  
|AdoEnums.FieldAttribute.MAYDEFER|  
|AdoEnums.FieldAttribute.NEGATIVESCALE|  
|AdoEnums.FieldAttribute.ROWID|  
|AdoEnums.FieldAttribute.ROWVERSION|  
|AdoEnums.FieldAttribute.UNKNOWNUPDATABLE|  
|AdoEnums.FieldAttribute.UNSPECIFIED|  
|AdoEnums.FieldAttribute.UPDATABLE|  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Append, méthode (ADO)](../../../ado/reference/ado-api/append-method-ado.md)|[Attributes, propriété (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)|
