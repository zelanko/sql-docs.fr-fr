---
description: 'ISSCommandWithParameters :: GetParameterProperties en SQL Server Native Client (OLE DB)'
title: ISSCommandWithParameters::GetParameterProperties (OLE DB)
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- GetParameterProperties method
ms.assetid: 7f4cc5ea-d028-4fe5-9192-bd153ab3c26c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5ed13eb576aaf85e734be14446f0f6f94d0dddf7
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97469300"
---
# <a name="isscommandwithparametersgetparameterproperties-in-sql-server-native-client-ole-db"></a>ISSCommandWithParameters :: GetParameterProperties en SQL Server Native Client (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Retourne un tableau de structures de jeu de propriétés SSPARAMPROPS, avec une propriété SSPARAMPROPS définie pour chaque paramètre UDT ou XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
  
## <a name="remarks"></a>Remarks  
 **ISSCommandWithParameters :: GetParameterProperties** se comporte de manière cohérente par rapport à **GetParameterInfo**. Si [ISSCommandWithParameters :: SetParameterProperties](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) ou **SetParameterInfo** n’ont pas été appelés ou ont été appelés avec cParams égal à zéro, **GetParameterInfo** dérive les informations de paramètre et retourne This. Si **ISSCommandWithParameters :: SetParameterProperties** ou **SetParameterInfo** ont été appelés pour au moins un paramètre, **ISSCommandWithParameters :: GetParameterProperties** retourne les propriétés uniquement pour les paramètres pour lesquels **ISSCommandWithParameters :: SetParameterProperties** a été appelé. Si **ISSCommandWithParameters :: SetParameterProperties** est appelé après **ISSCommandWithParameters :: GetParameterProperties** ou **GetParameterInfo**, les appels suivants à **ISSCommandWithParameters :: GetParameterProperties** retournent les valeurs substituées pour les paramètres pour lesquels **ISSCommandWithParameters :: SetParameterProperties** a été appelé.  
  
 La structure SSPARAMPROPS est défini comme suit :  

```cpp
struct SSPARAMPROPS {
    DBORDINAL iOrdinal;
    ULONG cPropertySets;
    DBPROPSET *rgPropertySets;
};
```

|Membre|Description|  
|------------|-----------------|  
|*iOrdinal*|Position ordinale du paramètre transmis.|  
|*cPropertySets*|Nombre de structures DBPROPSET dans *rgPropertySets*.|  
|*rgPropertySets*|Pointeur vers la mémoire dans lequel retourner un tableau de structures DBPROPSET.|  
|||

## <a name="see-also"></a>Voir aussi  
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
