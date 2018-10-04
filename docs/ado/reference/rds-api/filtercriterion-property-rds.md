---
title: FilterCriterion, propriété (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- FilterCriterion property [RDS]
ms.assetid: 24eb03ba-ccfd-4353-b6af-03586b2da6fd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f3c45059eb0ed2599a25623f7e5f88946778429c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47730337"
---
# <a name="filtercriterion-property-rds"></a>FilterCriterion, propriété (RDS)
Indique l’opérateur d’évaluation à utiliser dans la valeur de filtre.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DataControl.FilterCriterion = String  
```  
  
#### <a name="parameters"></a>Paramètres  
 *DataControl*  
 Une variable objet qui représente un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) objet.  
  
 *Chaîne*  
 Un **chaîne** valeur qui spécifie l’opérateur d’évaluation de la [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md) aux enregistrements. Peut prendre l’une des opérations suivantes : <, \<=, >, > =, =, ou <>.  
  
## <a name="remarks"></a>Notes  
 Le [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), **FilterCriterion**, et [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)fournissent des propriétés de tri et de filtrage sur le cache côté client. La fonctionnalité de tri trie les enregistrements par les valeurs d’une colonne. La fonctionnalité de filtrage affiche un sous-ensemble des enregistrements selon des critères de recherche, lors de la version complète [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) est conservé dans le cache. Le [réinitialiser](../../../ado/reference/rds-api/reset-method-rds.md) méthode exécute les critères et remplacez actuel **Recordset** avec un actualisable **Recordset**.  
  
 Le « ! = « opérateur n’est pas valide pour **FilterCriterion**; au lieu de cela, utilisez « <> ».  
  
 Si les propriétés de filtre et de tri sont définies et que vous appelez le **réinitialiser** (méthode), l’ensemble de lignes est tout d’abord filtré, puis il est trié. Pour les tris croissants, les valeurs null figurent en haut ; pour les tris décroissants, les valeurs null sont en bas (croissant est le comportement par défaut).  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn et SortDirection, propriétés et exemple de méthode de réinitialisation (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [FilterColumn, propriété (RDS)](../../../ado/reference/rds-api/filtercolumn-property-rds.md)   
 [FilterValue, propriété (RDS)](../../../ado/reference/rds-api/filtervalue-property-rds.md)   
 [SortColumn, propriété (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [SortDirection, propriété (RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)


