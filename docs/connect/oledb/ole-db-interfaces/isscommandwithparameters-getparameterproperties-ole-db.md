---
title: ISSCommandWithParameters::GetParameterProperties (OLE DB) | Microsoft Docs
description: ISSCommandWithParameters::GetParameterProperties (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- GetParameterProperties method
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 5b492706895a774d5b916058394ff352123bd708
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66783939"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Retourne un tableau de structures de jeu de propriétés SSPARAMPROPS, avec une propriété SSPARAMPROPS définie pour chaque paramètre UDT ou XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT GetParameterProperties(  
      DB_UPARAMS *pcParams,  
      SSPARAMPROPS **prgParamProperties);  
```  
  
## <a name="arguments"></a>Arguments  
 *pcParams*[out][in]  
 Pointeur vers la mémoire qui contient le nombre de structures SSPARAMPROPS retournées dans *prgParamProperties*.  
  
 *prgParamProperties*[out]  
 Pointeur vers la mémoire dans laquelle est retourné un tableau de structures SSPARAMPROPS. Le fournisseur attribue la mémoire pour les structures et retourne l’adresse à cette mémoire. Le consommateur libère la mémoire avec **IMalloc::Free** lorsqu’il n’a plus besoin des structures. Avant d’appeler **IMalloc::Free** pour *prgParamProperties*, le consommateur doit également appeler **VariantClear** pour la propriété *vValue* de chaque structure DBPROP afin d’empêcher une fuite de mémoire dans les cas où la variante contient un type référence (BSTR, par exemple). Si *pcParams* a la valeur zéro en sortie ou qu’il se produit une erreur autre que DB_E_ERRORSOCCURRED, le fournisseur n’alloue aucune mémoire et garantit que *prgParamProperties* est un pointeur Null en sortie.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 La méthode **GetParameterProperties** retourne les mêmes codes d’erreur que la méthode OLE DB **ICommandProperties::GetProperties** principale, si ce n’est que DB_S_ERRORSOCCURRED et DB_E_ERRORSOCCURED ne peuvent pas être déclenchés.  
  
## <a name="remarks"></a>Notes  
 La méthode **ISSCommandWithParameters::GetParameterProperties** se comporte de façon cohérente par rapport à **GetParameterInfo**. Si [ISSCommandWithParameters::SetParameterProperties](../../oledb/ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) ou **SetParameterInfo** n’ont pas été appelés ou ont été appelés avec cParams égal à zéro, **GetParameterInfo** dérive les informations de paramètre et les retourne. Si **ISSCommandWithParameters::SetParameterProperties** ou **SetParameterInfo** ont été appelés pour au moins un paramètre, **ISSCommandWithParameters::GetParameterProperties** retourne uniquement des propriétés pour les paramètres pour lesquels **ISSCommandWithParameters::SetParameterProperties** a été appelé. Si **ISSCommandWithParameters::SetParameterProperties** est appelé après **ISSCommandWithParameters::GetParameterProperties** ou **GetParameterInfo**, les appels suivants à **ISSCommandWithParameters::GetParameterProperties** retournent les valeurs substituées des paramètres pour lesquels **ISSCommandWithParameters::SetParameterProperties** a été appelé.  
  
 La structure SSPARAMPROPS est défini comme suit :  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|Membre|Description|  
|------------|-----------------|  
|*iOrdinal*|Position ordinale du paramètre transmis.|  
|*cPropertySets*|Nombre de structures DBPROPSET dans *rgPropertySets*.|  
|*rgPropertySets*|Pointeur vers la mémoire dans lequel retourner un tableau de structures DBPROPSET.|  
  
## <a name="see-also"></a>Voir aussi  
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
