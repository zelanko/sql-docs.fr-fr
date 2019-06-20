---
title: FilterValue, propriété (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- FilterValue property [ADO]
ms.assetid: 28f17186-b842-4cf9-b320-a9bb941c481b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 1e45986cdd44d0ab9bffc1ea11fe1a9ced350e3c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66712614"
---
# <a name="filtervalue-property-rds"></a>FilterValue, propriété (RDS)
Indique la valeur avec laquelle filtrer les enregistrements.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DataControl.FilterValue = String  
```  
  
#### <a name="parameters"></a>Paramètres  
 *DataControl*  
 Une variable objet qui représente un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) objet.  
  
 *String*  
 Un **chaîne** valeur qui représente une valeur de données avec laquelle filtrer les enregistrements (par exemple, `'Programmer'` ou `125`).  
  
## <a name="remarks"></a>Notes  
 Le [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), **FilterValue**, [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md), et [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)fournissent des propriétés de tri et de filtrage sur le cache côté client. La fonctionnalité de tri trie les enregistrements par les valeurs d’une colonne. La fonctionnalité de filtrage affiche un sous-ensemble des enregistrements selon des critères de recherche, lors de la version complète [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) est conservé dans le cache. Le [réinitialiser](../../../ado/reference/rds-api/reset-method-rds.md) méthode exécute les critères et remplacez actuel **Recordset** avec un actualisable **Recordset**.  
  
 Valeurs NULL provoquent une erreur d’incompatibilité de type.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn et SortDirection, propriétés et exemple de méthode de réinitialisation (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [FilterColumn Property (RDS)](../../../ado/reference/rds-api/filtercolumn-property-rds.md)   
 [FilterCriterion, propriété (RDS)](../../../ado/reference/rds-api/filtercriterion-property-rds.md)   
 [SortColumn, propriété (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [SortDirection, propriété (RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)






















