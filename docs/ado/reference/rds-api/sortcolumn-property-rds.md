---
title: SortColumn Property (RDS) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: e11588900c963576d4fec31545b27c6fdb480ab8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63272809"
---
# <a name="sortcolumn-property-rds"></a>SortColumn, propriété (RDS)
Indique la colonne selon laquelle trier les enregistrements.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DataControl.SortColumn = String  
```  
  
#### <a name="parameters"></a>Paramètres  
 *DataControl*  
 Une variable objet qui représente un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) objet.  
  
 *String*  
 Un **chaîne** valeur qui représente le nom ou l’alias de la colonne selon laquelle trier les enregistrements.  
  
## <a name="remarks"></a>Notes  
 Le **SortColumn**, [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md), et [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)fournissent des propriétés de tri et de filtrage sur le cache côté client. La fonctionnalité de tri trie les enregistrements par les valeurs d’une colonne. La fonctionnalité de filtrage affiche un sous-ensemble des enregistrements selon des critères de recherche, lors de la version complète [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) est conservé dans le cache. Le [réinitialiser](../../../ado/reference/rds-api/reset-method-rds.md) méthode exécute les critères et remplacez actuel **Recordset** avec un actualisable **Recordset**.  
  
 Pour effectuer un tri sur un **Recordset**, vous devez d’abord enregistrer les modifications en attente. Si vous utilisez le **RDS. DataControl**, vous pouvez utiliser la [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) (méthode). Par exemple, si votre **RDS. DataControl** est nommé ADC1, votre code sera `ADC1.SubmitChanges`. Si vous utilisez ADO **Recordset**, vous pouvez utiliser ses [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) (méthode). À l’aide de **UpdateBatch** est la méthode recommandée pour **Recordset** objets créés avec le [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md) (méthode). Par exemple, votre code peut être `myRS.UpdateBatch` ou `ADC1.Recordset.UpdateBatch`.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn et SortDirection, propriétés et exemple de méthode de réinitialisation (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Propriété de tri](../../../ado/reference/ado-api/sort-property.md)   
 [SortDirection, propriété (RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)





