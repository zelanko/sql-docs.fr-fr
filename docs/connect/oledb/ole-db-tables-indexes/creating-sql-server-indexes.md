---
title: Création d’index SQL Server | Microsoft Docs
description: Création d’index SQL Server à l’aide d’OLE DB pilote pour SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- CreateIndex function
- constraints [OLE DB]
- OLE DB Driver for SQL Server, indexes
- indexes [OLE DB]
- adding indexes
author: pmasl
ms.author: pelopes
ms.openlocfilehash: ca823023764a691eae0afc1e6df62bab91dd075d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015261"
---
# <a name="creating-sql-server-indexes"></a>Création d'index SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server expose la fonction **IIndexDefinition::CreateIndex**, en permettant aux consommateurs de définir de nouveaux index sur les tables [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Le pilote OLE DB pour SQL Server crée des index de table comme des index ou des contraintes. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] donne le privilège de création de contraintes au propriétaire de la table, au propriétaire de la base de données et aux membres de certains rôles d'administration. Par défaut, seul le propriétaire de la table peut créer un index sur une table. Par conséquent, le succès ou l’échec de **CreateIndex** ne dépend pas uniquement des droits d’accès de l’utilisateur de l’application, mais également du type d’index créé.  
  
 Les consommateurs spécifient le nom de table en tant que chaîne de caractères Unicode dans le membre *pwszName* de l’union *uName* dans le paramètre *pTableID*. Le membre *eKind* de *pTableID* doit être DBKIND_NAME.  
  
 Le paramètre *pIndexID* peut être Null, et si tel est le cas, le pilote OLE DB pour SQL Server crée un nom unique pour l’index. Le consommateur peut capturer le nom de l’index en spécifiant un pointeur valide vers un DBID dans le paramètre *ppIndexID*.  
  
 Le consommateur peut spécifier le nom d’index comme chaîne de caractères Unicode dans le membre *pwszName* de l’union *uName* du paramètre *pIndexID*. Le membre *eKind* de *pIndexID* doit être DBKIND_NAME.  
  
 Le consommateur spécifie la colonne ou les colonnes qui participent à l'index par leur nom. Pour chaque structure DBINDEXCOLUMNDESC utilisée dans **CreateIndex**, le membre *eKind* de *pColumnID* doit être DBKIND_NAME. Le nom de la colonne est spécifié comme chaîne de caractères Unicode dans le membre *pwszName*de l’union *uName* de *pColumnID*.  
  
 Le pilote OLE DB pour SQL Server et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prendre en charge l’ordre croissant sur les valeurs de l’index. Le pilote OLE DB pour SQL Server retourne E_INVALIDARG si le consommateur spécifie DBINDEX_COL_ORDER_DESC dans une structure DBINDEXCOLUMNDESC.  
  
 **CreateIndex** interprète les propriétés d’index de la façon suivante :  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|DBPROP_INDEX_AUTOUPDATE|R/W : lecture/écriture<br /><br /> Valeur par défaut : aucune<br /><br /> Description: le pilote OLE DB pour SQL Server ne prend pas en charge cette propriété. Les tentatives de définir la propriété dans **CreateIndex** provoquent une valeur de retour DB_S_ERRORSOCCURRED. Le membre *dwStatus* de la structure de propriété indique DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_CLUSTERED|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : contrôle le clustering d'index.<br /><br /> VARIANT_TRUE: le pilote OLE DB pour SQL Server tente de créer un index cluster sur la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge au plus un index cluster sur une table.<br /><br /> VARIANT_FALSE: le pilote OLE DB pour SQL Server tente de créer un index non-cluster sur la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table.|  
|DBPROP_INDEX_FILLFACTOR|R/W : lecture/écriture<br /><br /> Valeur par défaut : 0<br /><br /> Description : spécifie le pourcentage d'une page d'index utilisée pour le stockage. Pour plus d’informations, consultez [CREATE INDEX](../../../t-sql/statements/create-index-transact-sql.md).<br /><br /> Le type de la variante est VT_I4. La valeur doit être supérieure ou égale à 1 et inférieure ou égale à 100.|  
|DBPROP_INDEX_INITIALIZE|R/W : lecture/écriture<br /><br /> Valeur par défaut : aucune<br /><br /> Description: le pilote OLE DB pour SQL Server ne prend pas en charge cette propriété. Les tentatives de définir la propriété dans **CreateIndex** provoquent une valeur de retour DB_S_ERRORSOCCURRED. Le membre *dwStatus* de la structure de propriété indique DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_NULLCOLLATION|R/W : lecture/écriture<br /><br /> Valeur par défaut : aucune<br /><br /> Description: le pilote OLE DB pour SQL Server ne prend pas en charge cette propriété. Les tentatives de définir la propriété dans **CreateIndex** provoquent une valeur de retour DB_S_ERRORSOCCURRED. Le membre *dwStatus* de la structure de propriété indique DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_NULLS|R/W : lecture/écriture<br /><br /> Valeur par défaut : aucune<br /><br /> Description: le pilote OLE DB pour SQL Server ne prend pas en charge cette propriété. Les tentatives de définir la propriété dans **CreateIndex** provoquent une valeur de retour DB_S_ERRORSOCCURRED. Le membre *dwStatus* de la structure de propriété indique DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_PRIMARYKEY|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE Description : crée l'index comme intégrité référentielle, contrainte PRIMARY KEY.<br /><br /> VARIANT_TRUE : l'index est créé pour prendre en charge la contrainte PRIMARY KEY de la table. Les colonnes ne doivent pas accepter les valeurs null.<br /><br /> VARIANT_FALSE : l'index n'est pas utilisé comme contrainte PRIMARY KEY pour les valeurs de ligne de la table.|  
|DBPROP_INDEX_SORTBOOKMARKS|R/W : lecture/écriture<br /><br /> Valeur par défaut : aucune<br /><br /> Description: le pilote OLE DB pour SQL Server ne prend pas en charge cette propriété. Les tentatives de définir la propriété dans **CreateIndex** provoquent une valeur de retour DB_S_ERRORSOCCURRED. Le membre *dwStatus* de la structure de propriété indique DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_TEMPINDEX|R/W : lecture/écriture<br /><br /> Valeur par défaut : aucune<br /><br /> Description: le pilote OLE DB pour SQL Server ne prend pas en charge cette propriété. Les tentatives de définir la propriété dans **CreateIndex** provoquent une valeur de retour DB_S_ERRORSOCCURRED. Le membre *dwStatus* de la structure de propriété indique DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_TYPE|R/W : lecture/écriture<br /><br /> Valeur par défaut : aucune<br /><br /> Description: le pilote OLE DB pour SQL Server ne prend pas en charge cette propriété. Les tentatives de définir la propriété dans **CreateIndex** provoquent une valeur de retour DB_S_ERRORSOCCURRED. Le membre *dwStatus* de la structure de propriété indique DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_UNIQUE|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : crée l'index comme contrainte UNIQUE sur la colonne ou les colonnes participantes.<br /><br /> VARIANT_TRUE : l'index est utilisé pour définir une contrainte unique sur les valeurs de ligne de la table.<br /><br /> VARIANT_FALSE : l'index ne définit pas de contrainte unique sur les valeurs de ligne.|  
  
 Dans le jeu de propriétés DBPROPSET_SQLSERVERINDEX spécifique au fournisseur, le pilote OLE DB pour SQL Server définit les propriétés des informations de la source de données suivantes.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|SSPROP_INDEX_XML|Type : VT_BOOL (R/W)<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : lorsque cette propriété est spécifiée avec la valeur VARIANT_TRUE avec IIndexDefinition::CreateIndex, il s'ensuit la création d'un index xml primaire, correspondant à la colonne indexée. Si cette propriété est VARIANT_TRUE, cIndexColumnDescs doit être 1, sinon, il s'agit d'une erreur.|  
  
 Cet exemple crée un index de clé primaire :  
  
```  
// This CREATE TABLE statement shows the referential integrity and   
// PRIMARY KEY constraint on the OrderDetails table that will be created   
// by the following example code.  
//  
// CREATE TABLE OrderDetails  
// (  
//    OrderID      int      NOT NULL  
//    ProductID   int      NOT NULL  
//        CONSTRAINT PK_OrderDetails  
//        PRIMARY KEY CLUSTERED (OrderID, ProductID),  
//    UnitPrice   money      NOT NULL,  
//    Quantity   int      NOT NULL,  
//    Discount   decimal(2,2)   NOT NULL  
//        DEFAULT 0  
// )  
//  
HRESULT CreatePrimaryKey  
    (  
    IIndexDefinition* pIIndexDefinition  
    )  
    {  
    HRESULT             hr = S_OK;  
  
    DBID                dbidTable;  
    DBID                dbidIndex;  
    const ULONG         nCols = 2;  
    ULONG               nCol;  
    const ULONG         nProps = 2;  
    ULONG               nProp;  
  
    DBINDEXCOLUMNDESC   dbidxcoldesc[nCols];  
    DBPROP              dbpropIndex[nProps];  
    DBPROPSET           dbpropset;  
  
    DBID*               pdbidIndexOut = NULL;  
  
    // Set up identifiers for the table and index.  
    dbidTable.eKind = DBKIND_NAME;  
    dbidTable.uName.pwszName = L"OrderDetails";  
  
    dbidIndex.eKind = DBKIND_NAME;  
    dbidIndex.uName.pwszName = L"PK_OrderDetails";  
  
    // Set up column identifiers.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        dbidxcoldesc[nCol].pColumnID = new DBID;  
        dbidxcoldesc[nCol].pColumnID->eKind = DBKIND_NAME;  
  
        dbidxcoldesc[nCol].eIndexColOrder = DBINDEX_COL_ORDER_ASC;  
        }  
    dbidxcoldesc[0].pColumnID->uName.pwszName = L"OrderID";  
    dbidxcoldesc[1].pColumnID->uName.pwszName = L"ProductID";  
  
    // Set properties for the index. The index is clustered,  
    // PRIMARY KEY.  
    for (nProp = 0; nProp < nProps; nProp++)  
        {  
        dbpropIndex[nProp].dwOptions = DBPROPOPTIONS_REQUIRED;  
        dbpropIndex[nProp].colid = DB_NULLID;  
  
        VariantInit(&(dbpropIndex[nProp].vValue));  
  
        dbpropIndex[nProp].vValue.vt = VT_BOOL;  
        }  
    dbpropIndex[0].dwPropertyID = DBPROP_INDEX_CLUSTERED;  
    dbpropIndex[0].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropIndex[1].dwPropertyID = DBPROP_INDEX_PRIMARYKEY;  
    dbpropIndex[1].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropset.rgProperties = dbpropIndex;  
    dbpropset.cProperties = nProps;  
    dbpropset.guidPropertySet = DBPROPSET_INDEX;  
  
    hr = pIIndexDefinition->CreateIndex(&dbidTable, &dbidIndex, nCols,  
        dbidxcoldesc, 1, &dbpropset, &pdbidIndexOut);  
  
    // Clean up dynamically allocated DBIDs.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        delete dbidxcoldesc[nCol].pColumnID;  
        }  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et index](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
