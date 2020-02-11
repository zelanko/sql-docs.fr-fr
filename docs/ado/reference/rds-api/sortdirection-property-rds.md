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
ms.openlocfilehash: 28f0e247c29673fe4dfec507794ad8977b51fcc1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67963416"
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
 Variable objet qui représente un objet [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) .  
  
 *Valeur*  
 Valeur **booléenne** qui, lorsqu’elle est définie sur **true**, indique que le sens de tri est croissant. **False** indique l’ordre décroissant.  
  
## <a name="remarks"></a>Notes  
 Les propriétés [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), **SortDirection**, [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md)et [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md) fournissent des fonctionnalités de tri et de filtrage sur le cache côté client. La fonctionnalité de tri commande les enregistrements à l’aide des valeurs d’une colonne. La fonctionnalité de filtrage affiche un sous-ensemble d’enregistrements basés sur des critères de recherche, tandis que le [jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md) complet est conservé dans le cache. La méthode de [réinitialisation](../../../ado/reference/rds-api/reset-method-rds.md) exécute les critères et remplace le **jeu d’enregistrements** actuel par un **jeu d’enregistrements**pouvant être mis à jour.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn et SortDirection propriétés et Reset, exemple de méthode (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Sort, propriété](../../../ado/reference/ado-api/sort-property.md)   
 [SortColumn, propriété (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)


