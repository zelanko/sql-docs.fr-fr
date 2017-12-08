---
title: Ensemble de lignes DISCOVER_MEMORYUSAGE | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: e416ea61-9615-468c-a96f-bbf731f803b1
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d5fbb9282e35ff9d6c4a2e18b155f5a884a8f538
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="discovermemoryusage-rowset"></a>DISCOVER_MEMORYUSAGE, ensemble de lignes
  Retourne les statistiques DISCOVER_MEMORYUSAGE pour plusieurs objets alloués par le serveur.  
  
> [!WARNING]  
>  Cet ensemble de lignes peut produire des jeux de résultats très volumineux. Si les résultats ne peuvent pas être affichés car ils nécessitent davantage de mémoire d'affichage que ne le permet SQL Server Management Studio, ils sont écrits dans un fichier temporaire, dans l'emplacement par défaut suivant :  
>   
>  «\<lecteur > : \Users\\< nom d’utilisateur\>\AppData\Local\Temp\\< fileID\>.xml ».  
  
 **S'applique à :** modèles tabulaires, modèles multidimensionnels  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le **DISCOVER_MEMORYUSAGE** ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Restriction| Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**MemoryID**|**DBTYPE_UI8**||Numéro identifiant la mémoire.|  
|**MemoryName**|**DBTYPE_WSTR**||Nom de l'objet qui possède la mémoire.|  
|**SPID**|**DBTYPE_UI4**|Oui|Session qui a alloué la mémoire. Zéro indique la mémoire non liée à une session spécifique.|  
|**CreationTime**|**DBTYPE_DBTIMESTAMP**||Soit l'« heure de création de l'objet », soit l'« l'heure d'allocation de la mémoire ».|  
|**Baseobjecttype sont**|**DBTYPE_UI4**|Oui|Numéro qui décrit le type de l'objet. Les objets avec le même BaseObjectType sont de même type.|  
|**MemoryUsed**|**DBTYPE_UI8**|Oui|Il s'agit de la taille actuelle de l'objet, qui peut être inférieure à la mémoire allouée à l'utilisation de l'objet.|  
|**MemoryAllocated**|**DBTYPE_UI8**||Quantité de mémoire allouée à l'utilisation de l'objet, qui peut être supérieure à la quantité de mémoire réellement utilisée par l'objet.|  
|**MemoryAllocBase**|**DBTYPE_UI8**||Octets initialement alloués pour l'objet lui-même (à l'exception des allocations supplémentaires pour le contenu de l'objet).|  
|**MemoryAllocFromAlloc**|**DBTYPE_UI8**||Mémoire allouée au contenu de cet objet.|  
|**Valeur d’ElementCount**|**DBTYPE_UI4**||Pour un objet conteneur, il s'agit du nombre d'objets contenus par cet objet.|  
|**Réductible**|**DBTYPE_BOOL**|Oui|Valeur booléenne qui indique si la mémoire est réductible (peut être supprimée en cas de sollicitation de la mémoire). Si la valeur est true, la mémoire est réductible ; si la valeur est false, la mémoire n'est pas réductible.|  
|**ObjectParentPath**|**DBTYPE_WSTR**||Chaîne identifiant le chemin complet de cet objet.|  
|**ObjectID**|**DBTYPE_WSTR**||Chaîne identifiant l'objet. Le chemin d’accès complet de cet objet est représenté par la chaîne : (ObjectParentPath + '.' + ObjectId).|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Le tableau suivant fournit le GUID et les valeurs de chaîne qui identifient cet ensemble de lignes.  
  
|Argument|Valeur|  
|--------------|-----------|  
|GUID|A07CCD21-8148-11D0-87BB-00C04FC33942|  
|ADOMDNAME|MemoryUsage|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
