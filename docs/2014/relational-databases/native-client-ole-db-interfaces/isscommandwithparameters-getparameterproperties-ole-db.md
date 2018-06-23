---
title: ISSCommandWithParameters::GetParameterProperties (OLE DB) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetParameterProperties method
ms.assetid: 7f4cc5ea-d028-4fe5-9192-bd153ab3c26c
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f06c97d1f6d1e477700117c3038d0186db085fd1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043346"
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
 *pcParams*[out] [in]  
 Pointeur vers la mémoire qui contient le nombre de structures SSPARAMPROPS retournées dans *prgParamProperties*.  
  
 *prgParamProperties*[out]  
 Pointeur vers la mémoire dans laquelle est retourné un tableau de structures SSPARAMPROPS. Le fournisseur alloue de la mémoire pour les structures et retourne l’adresse à cette mémoire ; le consommateur libère cette mémoire avec **IMalloc::Free** lorsqu’il n’a plus besoin les structures. Avant d’appeler **IMalloc::Free** pour *prgParamProperties*, le consommateur doit également appeler **VariantClear** pour le *vValue* propriété de chaque structure DBPROP afin d’éviter une fuite de mémoire dans les cas où la variante contient une référence de type (par exemple, une chaîne BSTR.) Si *pcParams* est la valeur zéro en sortie ou une erreur autre que DB_E_ERRORSOCCURRED se produit, le fournisseur n’alloue pas de mémoire et garantit que *prgParamProperties* est un pointeur null en sortie.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Le **GetParameterProperties** méthode retourne les mêmes codes d’erreur que le noyau OLE DB **ICommandProperties::GetProperties** (méthode), sauf que DB_S_ERRORSOCCURRED et le DB_E_ERRORSOCCURED ne peut pas être déclenché.  
  
## <a name="remarks"></a>Notes  
 **ISSCommandWithParameters::GetParameterProperties** se comporte de manière cohérente par rapport au **GetParameterInfo**. Si [ISSCommandWithParameters::SetParameterProperties](isscommandwithparameters-setparameterproperties-ole-db.md) ou **SetParameterInfo** n’ont pas été appelé ou a été appelé avec cParams égal à zéro, **GetParameterInfo**dérive les informations sur les paramètres et les retourne. Si **ISSCommandWithParameters::SetParameterProperties** ou **SetParameterInfo** ont été appelés pour au moins un paramètre, **ISSCommandWithParameters::GetParameterProperties**  retourne les propriétés uniquement pour ces paramètres pour lesquels **ISSCommandWithParameters::SetParameterProperties** a été appelée. Si **ISSCommandWithParameters::SetParameterProperties** est appelée après **ISSCommandWithParameters::GetParameterProperties** ou **GetParameterInfo**, les appels suivants à **ISSCommandWithParameters::GetParameterProperties** retourner les valeurs substituées pour les paramètres pour lesquels **ISSCommandWithParameters::SetParameterProperties** a été appelée.  
  
 La structure SSPARAMPROPS est défini comme suit :  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|Membre|Description|  
|------------|-----------------|  
|*iOrdinal*|Position ordinale du paramètre transmis.|  
|*cPropertySets*|Le nombre de structures DBPROPSET dans *rgPropertySets*.|  
|*rgPropertySets*|Pointeur vers la mémoire dans lequel retourner un tableau de structures DBPROPSET.|  
  
## <a name="see-also"></a>Voir aussi  
 [ISSCommandWithParameters &#40;OLE DB&#41;](isscommandwithparameters-ole-db.md)  
  
  