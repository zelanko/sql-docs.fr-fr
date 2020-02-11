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
ms.openlocfilehash: e5b14e042c7566b6b6f8559e9dc371028a509979
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67964072"
---
# <a name="filtercriterion-property-rds"></a>FilterCriterion, propriété (RDS)
Indique l’opérateur d’évaluation à utiliser dans la valeur de filtre.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DataControl.FilterCriterion = String  
```  
  
#### <a name="parameters"></a>Paramètres  
 *DataControl*  
 Variable objet qui représente un objet [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) .  
  
 *Chaîne*  
 Valeur de **chaîne** qui spécifie l’opérateur d’évaluation de [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md) pour les enregistrements. Il peut s’agir de l’un des éléments suivants \<: <, =, >, >=, = ou <>.  
  
## <a name="remarks"></a>Notes  
 Les propriétés [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), **FilterCriterion**et [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md) fournissent des fonctionnalités de tri et de filtrage sur le cache côté client. La fonctionnalité de tri commande les enregistrements par valeurs d’une colonne. La fonctionnalité de filtrage affiche un sous-ensemble d’enregistrements basés sur des critères de recherche, tandis que le [jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md) complet est conservé dans le cache. La méthode de [réinitialisation](../../../ado/reference/rds-api/reset-method-rds.md) exécute les critères et remplace le **jeu d’enregistrements** actuel par un **jeu d’enregistrements**pouvant être mis à jour.  
  
 L’opérateur «  ! = » n’est pas valide pour **FilterCriterion**; Utilisez plutôt « <> ».  
  
 Si les propriétés Filter et sort sont toutes les deux définies et que vous appelez la méthode **Reset** , l’ensemble de lignes est tout d’abord filtré, puis trié. Pour les tris croissants, les valeurs NULL sont en haut ; pour les tris décroissants, les valeurs NULL sont en bas (le comportement croissant est le comportement par défaut).  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn et SortDirection propriétés et Reset, exemple de méthode (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [FilterColumn, propriété (RDS)](../../../ado/reference/rds-api/filtercolumn-property-rds.md)   
 [FilterValue, propriété (RDS)](../../../ado/reference/rds-api/filtervalue-property-rds.md)   
 [SortColumn, propriété (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [SortDirection, propriété (RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)


