---
description: SortDirection, propriété (RDS)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: a7a8aca2bb5dd4acf6a2b7b2702eb7807d520f73
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88767468"
---
# <a name="sortdirection-property-rds"></a>SortDirection, propriété (RDS)
Indique si un ordre de tri est croissant ou décroissant.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DataControl.SortDirection = value  
```  
  
#### <a name="parameters"></a>Paramètres  
 *DataControl*  
 Variable objet qui représente un objet [RDS. DataControl](./datacontrol-object-rds.md) .  
  
 *Valeur*  
 Valeur **booléenne** qui, lorsqu’elle est définie sur **true**, indique que le sens de tri est croissant. **False** indique l’ordre décroissant.  
  
## <a name="remarks"></a>Notes  
 Les propriétés [SortColumn](./sortcolumn-property-rds.md), **SortDirection**, [FilterValue](./filtervalue-property-rds.md), [FilterCriterion](./filtercriterion-property-rds.md)et [FilterColumn](./filtercolumn-property-rds.md) fournissent des fonctionnalités de tri et de filtrage sur le cache côté client. La fonctionnalité de tri commande les enregistrements à l’aide des valeurs d’une colonne. La fonctionnalité de filtrage affiche un sous-ensemble d’enregistrements basés sur des critères de recherche, tandis que le [jeu d’enregistrements](../ado-api/recordset-object-ado.md) complet est conservé dans le cache. La méthode de [réinitialisation](./reset-method-rds.md) exécute les critères et remplace le **jeu d’enregistrements** actuel par un **jeu d’enregistrements**pouvant être mis à jour.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn et SortDirection propriétés et Reset, exemple de méthode (VBScript)](./filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Sort, propriété](../ado-api/sort-property.md)   
 [SortColumn, propriété (RDS)](./sortcolumn-property-rds.md)