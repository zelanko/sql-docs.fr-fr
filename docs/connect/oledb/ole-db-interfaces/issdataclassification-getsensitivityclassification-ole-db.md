---
title: ISSDataClassification::GetSensitivityClassification | Microsoft Docs
description: ISSDataClassification::GetSensitivityClassification
ms.custom: ''
ms.date: 09/30/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- ISSDataClassification::GetSensitivityClassification
apitype: COM
helpviewer_keywords:
- GetSensitivityClassification method
author: bazizi
ms.author: v-beaziz
ms.openlocfilehash: 04877e626b57022d0110501b7da6145b2c4997d2
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96506648"
---
# <a name="issdataclassificationgetsensitivityclassification"></a>ISSDataClassification::GetSensitivityClassification
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW](../../../includes/applies-to-version/sql-asdb-asa.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Récupère les données de classification de sensibilité pour l’ensemble de lignes actif. Pour plus d’informations et pour obtenir un exemple de code, consultez [Utilisation de la classification des données](../features/using-data-classification.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSensitivityClassification(
    SENSITIVITYCLASSIFICATION** ppSensitivityClassification);
```  
  
## <a name="arguments"></a>Arguments  
  *ppSensitivityClassification*[out]  
 Pointeur vers un pointeur de structure SENSITIVITYCLASSIFICATION. Si la méthode échoue ou qu’il n’existe pas d’informations de classification des données disponibles, le fournisseur n’alloue pas de mémoire et vérifie que l’argument ppSensitivityClassification est un pointeur null en sortie.  
  
## <a name="return-code-values"></a>Codet de retour  
 S_OK  
 S_OK    
  
 E_INVALIDARG  
 L’argument *ppSensitivityClassification* a la valeur NULL.  
  
 E_OUTOFMEMORY  
 OLE DB Driver pour SQL Server n'a pas pu allouer une mémoire suffisante pour compléter la requête.  

  
## <a name="remarks"></a>Remarques  
OLE DB Driver pour SQL Server alloue un bloc de mémoire pour contenir la structure SENSITIVITYCLASSIFICATION et les données référencées par cette structure. Lorsque le contrôle serveur consommateur ne requiert plus l’accès aux données de classification des données, il doit désallouer cette mémoire avec la méthode [IMalloc::Free](https://docs.microsoft.com/windows/win32/api/objidl/nf-objidl-imalloc-free).  
  
 La structure SENSITIVITYCLASSIFICATION est définie comme suit :
  
```cpp
typedef struct tagSensitivityClassification
{
    USHORT                     cSensitivityLabels;
    SENSITIVITYLABEL          *rgSensitivityLabels;
    USHORT                     cInformationTypes;
    INFORMATIONTYPE           *rgInformationTypes;
    USHORT                     cColumnSensitivityMetadata;
    COLUMNSENSITIVITYMETADATA *rgColumnSensitivityMetadata;
    SENSITIVITYRANKENUM        eQuerySensitivityRank;
} SENSITIVITYCLASSIFICATION;
```  

|Membre|Description|  
|------------|-----------------|  
|*cSensitivityLabels*|Nombre de structures SENSITIVITYLABEL dans *rgSensitivityLabels*.|  
|*rgSensitivityLabels*|Tableau de structures SENSITIVITYLABEL.|  
|*cInformationTypes*|Nombre de structures INFORMATIONTYPE dans *rgInformationTypes*.|  
|*rgInformationTypes*|Tableau de structures INFORMATIONTYPE.|  
|*cColumnSensitivityMetadata*|Nombre de structures COLUMNSENSITIVITYMETADATA dans *rgColumnSensitivityMetadata*.|  
|*rgColumnSensitivityMetadata*|Tableau de structures COLUMNSENSITIVITYMETADATA.|  
|*eQuerySensitivityRank*|Classement relatif de la sensibilité d’une requête exécutée pour obtenir l’ensemble de lignes.|  

La structure SENSITIVITYLABEL est définie comme suit :
```cpp
typedef struct tagSENSITIVITYLABEL
{
    LPOLESTR pwszName;
    LPOLESTR pwszId;
} SENSITIVITYLABEL;
```

|Membre|Description|  
|------------|-----------------|  
|*pwszName*|Nom d’une étiquette de sensibilité.|  
|*pwszId*|L’identificateur d’une étiquette de sensibilité.|  

La structure INFORMATIONTYPE est définie comme suit :
```cpp
typedef struct tagINFORMATIONTYPE
{
    LPOLESTR pwszName;
    LPOLESTR pwszId;
} INFORMATIONTYPE;
```

|Membre|Description|  
|------------|-----------------|  
|*pwszName*|Nom d’un type d’informations.|  
|*pwszId*|L’identificateur d’un type d’informations.|  

La structure COLUMNSENSITIVITYMETADATA est définie comme suit :
```cpp
typedef struct tagCOLUMNSENSITIVITYMETADATA
{
    SENSITIVITYPROPERTY* rgSensitivityProperties;
    USHORT cSensitivityProperties;
} COLUMNSENSITIVITYMETADATA;
```

|Membre|Description|  
|------------|-----------------|  
|*cSensitivityProperties*|Nombre de structures SENSITIVITYLABEL dans *rgSensitivityProperties*.|  
|*rgSensitivityProperties*|Tableau de structures SENSITIVITYPROPERTY.|  

L’énumération SENSITIVITYRANKENUM est définie comme suit :
```cpp
typedef enum tagSENSITIVITYRANKENUM
{
    SENSITIVITYRANK_NOT_DEFINED = -1,
    SENSITIVITYRANK_NONE = 0,
    SENSITIVITYRANK_LOW = 10,
    SENSITIVITYRANK_MEDIUM = 20,
    SENSITIVITYRANK_HIGH = 30,
    SENSITIVITYRANK_CRITICAL = 40
} SENSITIVITYRANKENUM;
```

La structure SENSITIVITYPROPERTY est définie comme suit :
```cpp
typedef struct tagSENSITIVITYPROPERTY
{
    SENSITIVITYLABEL* pSensitivityLabel;
    INFORMATIONTYPE* pInformationType;
    SENSITIVITYRANKENUM eSensitivityRank;
} SENSITIVITYPROPERTY;
```

|Membre|Description|  
|------------|-----------------|  
|*pSensitivityLabel*|Pointeur vers une structure SENSITIVITYLABEL.|  
|*pInformationType*|Pointeur vers une structure INFORMATIONTYPE.|  
|*eSensitivityRank*|Classement relatif de la sensibilité d’une colonne qui fait partie de données par colonne.|  

## <a name="see-also"></a>Voir aussi  
 [ISSDataClassification](../../oledb/ole-db-interfaces/issdataclassification-ole-db.md)  
 [Ensembles de lignes](../ole-db-rowsets/rowsets.md)  
  
