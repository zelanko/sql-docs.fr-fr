---
title: ISSCommandWithParameters::GetParameterProperties (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetParameterProperties method
ms.assetid: 7f4cc5ea-d028-4fe5-9192-bd153ab3c26c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d492a64b6d8a4e8ddf7de27067f1f0bcfef205e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62638081"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties (OLE DB)
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
 Pointeur vers la mémoire dans laquelle est retourné un tableau de structures SSPARAMPROPS. Le fournisseur alloue de la mémoire pour les structures et retourne l’adresse à cette mémoire ; le consommateur libère cette mémoire avec **IMalloc :: Free** lorsqu’il n’a plus besoin des structures. Avant d’appeler **IMalloc :: Free** pour *prgParamProperties*, le consommateur doit également appeler **VariantClear** pour la propriété *vValue* de chaque structure DBPROP afin d’éviter une fuite de mémoire dans les cas où le variant contient un type référence (par exemple, BSTR). Si *pcParams* est égal à zéro en cas de sortie ou si une erreur autre que DB_E_ERRORSOCCURRED se produit, le fournisseur n’alloue pas de mémoire et vérifie que *prgParamProperties* est un pointeur null sur la sortie.  
  
## <a name="return-code-values"></a>Codet de retour  
 La méthode **GetParameterProperties** retourne les mêmes codes d’erreur que la méthode Core OLE DB **ICommandProperties :: GetProperties** , sauf que DB_S_ERRORSOCCURRED et DB_E_ERRORSOCCURED ne peuvent pas être déclenchés.  
  
## <a name="remarks"></a>Notes  
 **ISSCommandWithParameters :: GetParameterProperties** se comporte de manière cohérente par rapport à **GetParameterInfo**. Si [ISSCommandWithParameters :: SetParameterProperties](isscommandwithparameters-setparameterproperties-ole-db.md) ou **SetParameterInfo** n’ont pas été appelés ou ont été appelés avec cParams égal à zéro, **GetParameterInfo** dérive les informations de paramètre et retourne This. Si **ISSCommandWithParameters :: SetParameterProperties** ou **SetParameterInfo** ont été appelés pour au moins un paramètre, **ISSCommandWithParameters :: GetParameterProperties** retourne les propriétés uniquement pour les paramètres pour lesquels **ISSCommandWithParameters :: SetParameterProperties** a été appelé. Si **ISSCommandWithParameters :: SetParameterProperties** est appelé après **ISSCommandWithParameters :: GetParameterProperties** ou **GetParameterInfo**, les appels suivants à **ISSCommandWithParameters :: GetParameterProperties** retournent les valeurs substituées pour les paramètres pour lesquels **ISSCommandWithParameters :: SetParameterProperties** a été appelé.  
  
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
 [ISSCommandWithParameters &#40;OLE DB&#41;](isscommandwithparameters-ole-db.md)  
  
  
