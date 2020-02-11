---
title: SortColumn, propriété (RDS) | Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SortColumn property [RDS]
ms.assetid: f6f80f67-f0fb-4e63-a5f5-8fdf312aac63
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b5a9c3f9f50968f3b5e8085052917397bcd90226
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67963394"
---
# <a name="sortcolumn-property-rds"></a>SortColumn, propriété (RDS)
Indique la colonne dans laquelle trier les enregistrements.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DataControl.SortColumn = String  
```  
  
#### <a name="parameters"></a>Paramètres  
 *DataControl*  
 Variable objet qui représente un objet [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) .  
  
 *Chaîne*  
 Valeur de **chaîne** qui représente le nom ou l’alias de la colonne selon laquelle trier les enregistrements.  
  
## <a name="remarks"></a>Notes  
 Les propriétés **SortColumn**, [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md)et [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md) fournissent des fonctionnalités de tri et de filtrage sur le cache côté client. La fonctionnalité de tri commande les enregistrements par valeurs d’une colonne. La fonctionnalité de filtrage affiche un sous-ensemble d’enregistrements basés sur des critères de recherche, tandis que le [jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md) complet est conservé dans le cache. La méthode de [réinitialisation](../../../ado/reference/rds-api/reset-method-rds.md) exécute les critères et remplace le **jeu d’enregistrements** actuel par un **jeu d’enregistrements**pouvant être mis à jour.  
  
 Pour effectuer un tri sur un **jeu d’enregistrements**, vous devez d’abord enregistrer toutes les modifications en attente. Si vous utilisez le **RDS. DataControl**, vous pouvez utiliser la méthode [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) . Par exemple, si votre **objet RDS. DataControl** est nommé ADC1, votre code est `ADC1.SubmitChanges`. Si vous utilisez un **jeu d’enregistrements**ADO, vous pouvez utiliser sa méthode [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) . L’utilisation de **UpdateBatch** est la méthode recommandée pour les objets **Recordset** créés avec la méthode [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md) . Par exemple, votre code peut être `myRS.UpdateBatch` ou `ADC1.Recordset.UpdateBatch`.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn et SortDirection propriétés et Reset, exemple de méthode (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Sort, propriété](../../../ado/reference/ado-api/sort-property.md)   
 [SortDirection, propriété (RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)





