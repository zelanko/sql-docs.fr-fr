---
title: SortDirection, propriété (RDS) | Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SortDirection property [RDS]
ms.assetid: 1d9d8715-e4ad-4ff3-bf7f-f1dc0532d8c2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ef187cd2ae291413fccf10e2af51642c50e06e5
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51601309"
---
# <a name="sortdirection-property-rds"></a>SortDirection, propriété (RDS)
Indique si un ordre de tri est croissant ou décroissant.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DataControl.SortDirection = value  
```  
  
#### <a name="parameters"></a>Paramètres  
 *DataControl*  
 Une variable objet qui représente un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) objet.  
  
 *Valeur*  
 Un **booléenne** valeur qui, lorsque la valeur **True**, indique le sens de tri est croissant. **False** indique l’ordre décroissant.  
  
## <a name="remarks"></a>Notes  
 Le [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), **SortDirection**, [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md), et [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)fournissent des propriétés de tri et de filtrage sur le cache côté client. La fonctionnalité de tri trie les enregistrements à l’aide de valeurs d’une colonne. La fonctionnalité de filtrage affiche un sous-ensemble des enregistrements selon des critères de recherche, lors de la version complète [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) est conservé dans le cache. Le [réinitialiser](../../../ado/reference/rds-api/reset-method-rds.md) méthode exécute les critères et remplacez actuel **Recordset** avec un actualisable **Recordset**.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn et SortDirection, propriétés et exemple de méthode de réinitialisation (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Propriété de tri](../../../ado/reference/ado-api/sort-property.md)   
 [SortColumn, propriété (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)


