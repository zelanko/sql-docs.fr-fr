---
title: Reset, méthode (RDS) | Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Reset method [ADO]
ms.assetid: 3957197a-f543-4d6b-9e11-67a77c2063b7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 416aaefa95871e909a12117756ea59747c555650
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67963493"
---
# <a name="reset-method-rds"></a>Reset, méthode (RDS)
Exécute le tri ou le filtre sur une côté client **Recordset** basée sur les propriétés de tri et de filtre spécifiées.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DataControl.Reset(value)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *DataControl*  
 Une variable objet qui représente un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) objet.  
  
 *value*  
 Facultatif. Un **booléenne** valeur **True** (valeur par défaut) si vous souhaitez filtrer sur l’ensemble de lignes « filtré » actuel. **False** effectuer le filtrage sur l’ensemble de lignes d’origine, suppression des options de filtre précédentes.  
  
## <a name="remarks"></a>Notes  
 Le [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md), et [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)fournissent des propriétés de tri et de filtrage sur le cache côté client. La fonctionnalité de tri trie les enregistrements par les valeurs d’une colonne. La fonctionnalité de filtrage affiche un sous-ensemble des enregistrements selon un critère de recherche, lors de la version complète [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) est conservé dans le cache. Le **réinitialiser** méthode exécute les critères et remplacez actuel **Recordset** avec un actualisable **Recordset**.  
  
 Si des modifications sont apportées aux données d’origine qui n’ont pas été envoyées, le **réinitialiser** méthode échoue. Tout d’abord, utilisez le [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) méthode pour enregistrer les modifications dans une lecture/écriture **Recordset**, puis utilisez le **réinitialiser** méthode trier ou filtrer les enregistrements.  
  
 Si vous souhaitez effectuer plusieurs filtres sur votre ensemble de lignes, vous pouvez utiliser le paramètre facultatif *booléenne* argument avec le **réinitialiser** (méthode). L’exemple suivant montre comment procéder :  
  
```  
ADC.SQL = "Select au_lname from authors"  
ADC.Refresh    ' Get the new rowset.  
  
ADC.FilterColumn = "au_lname"  
ADC.FilterCriterion = "<"  
ADC.FilterValue = "'M'"  
ADC.Reset         ' Rowset now has all Last Names < "M".  
  
ADC.FilterCriterion = ">"  
ADC.FilterValue = "'F'"  
' Passing True is not necessary, because it is the   
' default filter on the current "filtered" rowset.  
ADC.Reset(TRUE)     ' Rowset now has all Last   
                    ' Names < "M" and > "F".  
  
ADC.FilterCriterion = ">"  
ADC.FilterValue = "'T'"  
' Filter on the original rowset, throwing out the  
' previous filter options.  
ADC.Reset(FALSE)   ' Rowset now has all Last Names > "T".  
```  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn et SortDirection, propriétés et exemple de méthode de réinitialisation (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [SubmitChanges, méthode (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)



