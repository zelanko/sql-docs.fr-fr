---
title: Création d’index SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- CreateIndex function
- constraints [OLE DB]
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
- adding indexes
ms.assetid: 6239d440-2818-4b98-bb79-732dced41952
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5770c54e748ab7658acb3319e1e1c3b56a8c178f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301660"
---
# <a name="creating-sql-server-indexes"></a>Création d'index SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native Client OLE DB expose la fonction **IIndexDefinition::CreateIndex,** permettant aux consommateurs de définir de nouveaux index sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les tables.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone crée des index de table comme index ou contraintes. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] donne le privilège de création de contraintes au propriétaire de la table, au propriétaire de la base de données et aux membres de certains rôles d'administration. Par défaut, seul le propriétaire de la table peut créer un index sur une table. Par conséquent, le succès ou l’échec de **CreateIndex** ne dépend pas uniquement des droits d’accès de l’utilisateur de l’application, mais également du type d’index créé.  
  
 Les consommateurs spécifient le nom de table en tant que chaîne de caractères Unicode dans le membre *pwszName* de l’union *uName* dans le paramètre *pTableID*. Le membre *eKind* de *pTableID* doit être DBKIND_NAME.  
  
 Le paramètre *pIndexID* peut être NULL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et si c’est le cas, le fournisseur native Client OLE DB crée un nom unique pour l’index. Le consommateur peut capturer le nom de l’index en spécifiant un pointeur valide vers un DBID dans le paramètre *ppIndexID*.  
  
 Le consommateur peut spécifier le nom d’index comme chaîne de caractères Unicode dans le membre *pwszName* de l’union *uName* du paramètre *pIndexID*. Le membre *eKind* de *pIndexID* doit être DBKIND_NAME.  
  
 Le consommateur spécifie la colonne ou les colonnes qui participent à l'index par leur nom. Pour chaque structure DBINDEXCOLUMNDESC utilisée dans **CreateIndex**, le membre *eKind* de *pColumnID* doit être DBKIND_NAME. Le nom de la colonne est spécifié comme chaîne de caractères Unicode dans le membre *pwszName*de l’union *uName* de *pColumnID*.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE de client autochtone et appuie l’ordre ascendant sur les valeurs de l’indice. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone retourne E_INVALIDARG si le consommateur spécifie DBINDEX_COL_ORDER_DESC dans n’importe quelle structure DBINDEXCOLUMNDESC.  
  
 **CreateIndex** interprète les propriétés d’index de la façon suivante :  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|DBPROP_INDEX_AUTOUPDATE|R/W : lecture/écriture<br /><br /> Valeur par défaut : aucune<br /><br /> Description: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le fournisseur de clients autochtones OLE DB ne prend pas en charge cette propriété. Les tentatives de définir la propriété dans **CreateIndex** provoquent une valeur de retour DB_S_ERRORSOCCURRED. Le membre *dwStatus* de la structure de propriété indique DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_CLUSTERED|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : contrôle le clustering d'index.<br /><br /> VARIANT_TRUE : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE native Client tente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de créer un index groupé sur la table. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge au plus un index cluster sur une table.<br /><br /> VARIANT_FALSE : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone tente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de créer un index non isolé sur la table.|  
|DBPROP_INDEX_FILLFACTOR|R/W : lecture/écriture<br /><br /> Valeur par défaut : 0<br /><br /> Description : spécifie le pourcentage d'une page d'index utilisée pour le stockage. Pour plus d’informations, voir [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md).<br /><br /> Le type de la variante est VT_I4. La valeur doit être supérieure ou égale à 1 et inférieure ou égale à 100.|  
|DBPROP_INDEX_INITIALIZE|R/W : lecture/écriture<br /><br /> Valeur par défaut : aucune<br /><br /> Description: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le fournisseur de clients autochtones OLE DB ne prend pas en charge cette propriété. Les tentatives de définir la propriété dans **CreateIndex** provoquent une valeur de retour DB_S_ERRORSOCCURRED. Le membre *dwStatus* de la structure de propriété indique DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_NULLCOLLATION|R/W : lecture/écriture<br /><br /> Valeur par défaut : aucune<br /><br /> Description: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le fournisseur de clients autochtones OLE DB ne prend pas en charge cette propriété. Les tentatives de définir la propriété dans **CreateIndex** provoquent une valeur de retour DB_S_ERRORSOCCURRED. Le membre *dwStatus* de la structure de propriété indique DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_NULLS|R/W : lecture/écriture<br /><br /> Valeur par défaut : aucune<br /><br /> Description: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le fournisseur de clients autochtones OLE DB ne prend pas en charge cette propriété. Les tentatives de définir la propriété dans **CreateIndex** provoquent une valeur de retour DB_S_ERRORSOCCURRED. Le membre *dwStatus* de la structure de propriété indique DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_PRIMARYKEY|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE Description : crée l'index comme intégrité référentielle, contrainte PRIMARY KEY.<br /><br /> VARIANT_TRUE : l'index est créé pour prendre en charge la contrainte PRIMARY KEY de la table. Les colonnes ne doivent pas accepter les valeurs null.<br /><br /> VARIANT_FALSE : l'index n'est pas utilisé comme contrainte PRIMARY KEY pour les valeurs de ligne de la table.|  
|DBPROP_INDEX_SORTBOOKMARKS|R/W : lecture/écriture<br /><br /> Valeur par défaut : aucune<br /><br /> Description: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le fournisseur de clients autochtones OLE DB ne prend pas en charge cette propriété. Les tentatives de définir la propriété dans **CreateIndex** provoquent une valeur de retour DB_S_ERRORSOCCURRED. Le membre *dwStatus* de la structure de propriété indique DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_TEMPINDEX|R/W : lecture/écriture<br /><br /> Valeur par défaut : aucune<br /><br /> Description: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le fournisseur de clients autochtones OLE DB ne prend pas en charge cette propriété. Les tentatives de définir la propriété dans **CreateIndex** provoquent une valeur de retour DB_S_ERRORSOCCURRED. Le membre *dwStatus* de la structure de propriété indique DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_TYPE|R/W : lecture/écriture<br /><br /> Valeur par défaut : aucune<br /><br /> Description: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le fournisseur de clients autochtones OLE DB ne prend pas en charge cette propriété. Les tentatives de définir la propriété dans **CreateIndex** provoquent une valeur de retour DB_S_ERRORSOCCURRED. Le membre *dwStatus* de la structure de propriété indique DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_UNIQUE|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : crée l'index comme contrainte UNIQUE sur la colonne ou les colonnes participantes.<br /><br /> VARIANT_TRUE : l'index est utilisé pour définir une contrainte unique sur les valeurs de ligne de la table.<br /><br /> VARIANT_FALSE : l'index ne définit pas de contrainte unique sur les valeurs de ligne.|  
  
 Dans l’ensemble de propriétés spécifique [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au fournisseur DBPROPSET_SQLSERVERINDEX, le fournisseur de DB OLE de client autochtone définit la propriété d’information de source de données suivante.  
  
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
 [Tableaux et indices](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
