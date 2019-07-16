---
title: Création de Tables SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- SQL Server Native Client OLE DB provider, tables
- DBCOLUMNDESC usage
- adding tables
- CreateTable function
ms.assetid: a7b8d142-d76a-44d9-a583-86ac5109fbe8
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 72a278a142889d8b9d1e43976939f06b002689d7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68069744"
---
# <a name="creating-sql-server-tables"></a>Création de tables SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose la **ITableDefinition::CreateTable** fonction, ce qui permet aux consommateurs de créer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables. Les consommateurs utilisent **CreateTable** pour créer des tables permanentes nommées de consommateur et des tables permanentes ou temporaires avec des noms uniques générés par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif.  
  
 Lorsque le consommateur appelle **ITableDefinition::CreateTable**, si la valeur de la propriété DBPROP_TBL_TEMPTABLE est VARIANT_TRUE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB Native génère un nom de table temporaire pour le consommateur. Le consommateur attribue la valeur NULL au paramètre *pTableID* de la méthode **CreateTable**. Les tables temporaires munies de noms générés par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif n’apparaissent pas dans le **TABLES** ensemble de lignes, mais sont accessibles via le **IOpenRowset** interface.  
  
 Lorsque les consommateurs spécifient le nom de table dans le *pwszName* membre de la *uName* union dans le *pTableID* paramètre, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif Crée un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table portant ce nom. Des contraintes en matière d'affectation de noms aux tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'appliquent et le nom de la table peut indiquer une table permanente ou une table temporaire locale ou globale. Pour plus d’informations, consultez [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md). Le paramètre *ppTableID* peut avoir la valeur NULL.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB Native peut générer les noms des tables permanentes ou temporaires. Lorsque le consommateur définit la *pTableID* paramètre sur NULL et les jeux *ppTableID* pour pointer vers un DBID valid\*, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB Native retourne le nom généré de la table dans le *pwszName* membre de la *uName* union de la structure DBID vers lequel pointe la valeur de *ppTableID*. Pour créer une table temporaire, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table de nommées par le fournisseur OLE DB Native Client, le consommateur inclut la propriété de table OLE DB DBPROP_TBL_TEMPTABLE dans une propriété table référencée dans le *rgPropertySets* paramètre. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB nommées par le fournisseur des tables temporaires sont locaux.  
  
 **CreateTable** retourne DB_E_BADTABLEID si le membre *eKind* du paramètre *pTableID* n’indique pas DBKIND_NAME.  
  
## <a name="dbcolumndesc-usage"></a>Utilisation de la structure DBCOLUMNDESC  
 Le consommateur peut indiquer un type de données de colonne en utilisant soit le membre *pwszTypeName*, soit le membre *wType*. Si le consommateur Spécifie le type de données dans *pwszTypeName*, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client ignore la valeur de *wType*.  
  
 S’il utilise le membre *pwszTypeName*, le consommateur spécifie le type de données à l’aide de noms du type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les noms de type de données valides sont les noms retournés dans la colonne TYPE_NAME de l'ensemble de lignes de schéma PROVIDER_TYPES.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client reconnaît un sous-ensemble de valeurs DBTYPE énumérées à OLE DB dans le *wType* membre. Pour plus d’informations, consultez [mappage de Type de données dans ITableDefinition](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md).  
  
> [!NOTE]  
>  **CreateTable** retourne DB_E_BADTYPE si le consommateur choisit le membre *pTypeInfo* ou *pclsid* pour spécifier le type de données de colonne.  
  
 Le consommateur spécifie le nom de colonne dans le membre *pwszName* de l’union *uName* du membre *dbcid* DBCOLUMNDESC. Le nom de colonne est spécifié en tant que chaîne de caractères Unicode. Le membre *eKind* de *dbcid* doit être DBKIND_NAME. **CreateTable** retourne DB_E_BADCOLUMNID si le membre *eKind* n’est pas valide, si *pwszName* possède la valeur NULL ou si la valeur de *pwszName* n’est pas un identificateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide.  
  
 Toutes les propriétés de colonne sont disponibles dans toutes les colonnes définies pour la table. **CreateTable** peut retourner DB_S_ERRORSOCCURRED ou DB_E_ERRORSOCCURRED si les valeurs des propriétés sont en conflit. **CreateTable** retourne une erreur lorsque les paramètres des propriétés de colonne non valides entraîne un échec lors de la création de tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Les propriétés des colonnes dans une structure DBCOLUMNDESC se définissent de la manière suivante.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|DBPROP_COL_AUTOINCREMENT|R/W : en lecture/écriture<br /><br /> Par défaut : VARIANT_FALSE Description : Définit la propriété identity sur la colonne créée. Pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la propriété d'identité est valide pour une colonne unique au sein d'une table. Définition de la propriété à VARIANT_TRUE pour plusieurs colonnes uniques génère une erreur lors de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les fournisseur OLE DB Native Client tente de créer la table sur le serveur.<br /><br /> La propriété d’identité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est uniquement valide pour les types **integer**, **numeric** et **decimal** lorsque l’échelle est définie sur 0. Définition de la propriété à VARIANT_TRUE sur une colonne d’un autre type de données génère une erreur lors de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les fournisseur OLE DB Native Client tente de créer la table sur le serveur.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client retourne DB_S_ERRORSOCCURRED lorsque DBPROP_COL_AUTOINCREMENT et DBPROP_COL_NULLABLE sont les deux VARIANT_TRUE et *dwOption* de DBPROP_COL_NULLABLE n’est pas DBPROPOPTIONS_ Obligatoire. DB_E_ERRORSOCCURRED est retourné lorsque DBPROP_COL_AUTOINCREMENT et DBPROP_COL_NULLABLE sont tous les deux définis sur VARIANT_TRUE et quand la valeur *dwOption* de DBPROP_COL_NULLABLE est égale à DBPROPOPTIONS_REQUIRED. La colonne est définie avec la propriété d’identité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le membre *dwStatus* DBPROP_COL_NULLABLE est défini sur DBPROPSTATUS_CONFLICTING.|  
|DBPROP_COL_DEFAULT|R/W : en lecture/écriture<br /><br /> Par défaut : Aucun<br /><br /> Description : Crée un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contrainte par défaut pour la colonne.<br /><br /> Le membre *vValue* DBPROP peut appartenir aux types suivants. Le membre *vValue.vt* doit spécifier un type compatible avec le type de données de la colonne. Par exemple, le choix de BSTR N/A comme valeur par défaut d'une colonne définie en tant que DBTYPE_WSTR offre une valeur de correspondance compatible. Définition de la même valeur par défaut sur une colonne en tant que DBTYPE_R8 une erreur lors de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les fournisseur OLE DB Native Client tente de créer la table sur le serveur.|  
|DBPROP_COL_DESCRIPTION|R/W : en lecture/écriture<br /><br /> Par défaut : Aucun<br /><br /> Description : La propriété de colonne DBPROP_COL_DESCRIPTION n’est pas implémentée par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif.<br /><br /> Le membre *dwStatus* de la structure DBPROP retourne DBPROPSTATUS_NOTSUPPORTED lorsque le consommateur tente d’écrire la valeur de propriété.<br /><br /> Définition de la propriété ne constitue pas une erreur irrécupérable pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif. Si toutes les autres valeurs de paramètres sont valides, la table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est créée.|  
|DBPROP_COL_FIXEDLENGTH|R/W : en lecture/écriture<br /><br /> Par défaut : VARIANT_FALSE<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client utilise DBPROP_COL_FIXEDLENGTH pour déterminer le mappage de type de données lorsque le consommateur définit le type de données d’une colonne à l’aide de la *wType* membre de la structure DBCOLUMNDESC. Pour plus d’informations, consultez [mappage de Type de données dans ITableDefinition](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md).|  
|DBPROP_COL_NULLABLE|R/W : en lecture/écriture<br /><br /> Par défaut : Aucun<br /><br /> Description : Lors de la création de la table, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif indique si la colonne doit accepter les valeurs null si la propriété est définie. Lorsque la propriété n'est pas définie, l'aptitude de la colonne à valider la valeur NULL dépend de l'option de base de données par défaut ANSI_NULLS de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif est un fournisseur conforme à ISO. Les sessions connectées affichent des comportements ISO. Si le consommateur ne définit pas DBPROP_COL_NULLABLE, les colonnes acceptent des valeurs NULL.|  
|DBPROP_COL_PRIMARYKEY|R/W : en lecture/écriture<br /><br /> Par défaut : VARIANT_FALSE Description : Lors de la valeur VARIANT_TRUE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif crée la colonne avec une contrainte PRIMARY KEY.<br /><br /> Si la propriété est définie comme une propriété de colonne, seule une colonne unique peut déterminer la contrainte. Définition de la propriété sur VARIANT_TRUE pour plusieurs colonnes uniques retourne une erreur lors de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client tente de créer le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.<br /><br /> Remarque : Le consommateur peut utiliser **IIndexDefinition::CreateIndex** pour créer une contrainte PRIMARY KEY sur deux ou plusieurs colonnes.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client retourne DB_S_ERRORSOCCURRED lorsque DBPROP_COL_PRIMARYKEY et DBPROP_COL_UNIQUE sont les deux VARIANT_TRUE et *dwOption* de DBPROP_COL_UNIQUE n’est pas DBPROPOPTIONS_REQUIRED.<br /><br /> DB_E_ERRORSOCCURRED est retourné lorsque DBPROP_COL_PRIMARYKEY et DBPROP_COL_UNIQUE sont tous les deux définis sur VARIANT_TRUE et quand la valeur *dwOption* de DBPROP_COL_UNIQUE est égale à DBPROPOPTIONS_REQUIRED. La colonne est définie avec la propriété d’identité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le membre *dwStatus* DBPROP_COL_PRIMARYKEY est défini sur DBPROPSTATUS_CONFLICTING.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les fournisseur OLE DB Native Client retourne une erreur lorsque DBPROP_COL_PRIMARYKEY et DBPROP_COL_NULLABLE sont les deux VARIANT_TRUE.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client retourne une erreur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lorsque le consommateur tente de créer une contrainte PRIMARY KEY sur une colonne de non valide [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données. Vous ne pouvez pas définir des contraintes PRIMARY KEY dans des colonnes créées avec les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **bit**, **text**, **ntext** et **image**.|  
|DBPROP_COL_UNIQUE|R/W : en lecture/écriture<br /><br /> Par défaut : VARIANT_FALSE Description : Applique un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] une contrainte UNIQUE à la colonne.<br /><br /> Si la propriété est définie comme une propriété de colonne, la contrainte est appliquée dans une seule colonne uniquement. Le consommateur peut se servir de la fonction **IIndexDefinition::CreateIndex** pour appliquer une contrainte UNIQUE à des valeurs combinées de deux ou plusieurs colonnes.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client retourne DB_S_ERRORSOCCURRED lorsque DBPROP_COL_PRIMARYKEY et DBPROP_COL_UNIQUE sont les deux VARIANT_TRUE et *dwOption* n’est pas DBPROPOPTIONS_REQUIRED.<br /><br /> DB_E_ERRORSOCCURRED est retourné lorsque DBPROP_COL_PRIMARYKEY et DBPROP_COL_UNIQUE sont tous les deux définis sur VARIANT_TRUE et quand la valeur *dwOption* est égale à DBPROPOPTIONS_REQUIRED. La colonne est définie avec la propriété d’identité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le membre *dwStatus* DBPROP_COL_PRIMARYKEY est défini sur DBPROPSTATUS_CONFLICTING.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client retourne DB_S_ERRORSOCCURRED lorsque DBPROP_COL_NULLABLE et DBPROP_COL_UNIQUE sont les deux VARIANT_TRUE et *dwOption* n’est pas DBPROPOPTIONS_REQUIRED.<br /><br /> DB_E_ERRORSOCCURRED est retourné lorsque DBPROP_COL_NULLABLE et DBPROP_COL_UNIQUE sont tous les deux définis sur VARIANT_TRUE et quand la valeur *dwOption* est égale à DBPROPOPTIONS_REQUIRED. La colonne est définie avec la propriété d’identité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le membre *dwStatus* DBPROP_COL_NULLABLE est défini sur DBPROPSTATUS_CONFLICTING.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client retourne une erreur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lorsque le consommateur tente de créer une contrainte UNIQUE sur une colonne de non valide [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données. Vous ne pouvez pas définir des contraintes UNIQUE sur des colonnes créées avec le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **bit**.|  
  
 Lorsque le consommateur appelle **ITableDefinition::CreateTable**, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les fournisseur OLE DB Native Client interprète les propriétés de la table comme suit.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|DBPROP_TBL_TEMPTABLE|R/W : en lecture/écriture<br /><br /> Par défaut : VARIANT_FALSE Description : Par défaut, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif crée des tables nommées par le consommateur. Lors de la valeur VARIANT_TRUE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB Native génère un nom de table temporaire pour le consommateur. Le consommateur attribue la *pTableID* paramètre de **CreateTable** avec la valeur NULL. Le paramètre *ppTableID* doit contenir un pointeur valide.|  
  
 Si le consommateur demande qu’un ensemble de lignes être ouvert sur une table créée avec succès, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif ouvre un ensemble de lignes de curseur pris en charge. Toutes les propriétés de l'ensemble de lignes peuvent être indiquées dans les jeux de propriétés passés.  
  
 L'exemple ci-dessous crée une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
// This CREATE TABLE statement shows the details of the table created by   
// the following example code.  
//  
// CREATE TABLE OrderDetails  
// (  
//    OrderID      int      NOT NULL  
//    ProductID   int      NOT NULL  
//    CONSTRAINT PK_OrderDetails  
//         PRIMARY KEY CLUSTERED (OrderID, ProductID),  
//    UnitPrice   money      NOT NULL,  
//    Quantity   int      NOT NULL,  
//    Discount   decimal(2,2)   NOT NULL  
//        DEFAULT 0  
// )  
//  
// The PRIMARY KEY constraint is created in an additional example.  
HRESULT CreateTable  
    (  
    ITableDefinition* pITableDefinition  
    )  
    {  
    DBID            dbidTable;  
    const ULONG     nCols = 5;  
    ULONG           nCol;  
    ULONG           nProp;  
    DBCOLUMNDESC    dbcoldesc[nCols];  
  
    HRESULT         hr;  
  
    // Set up column descriptions. First, set default property values for  
    //  the columns.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        dbcoldesc[nCol].pwszTypeName = NULL;  
        dbcoldesc[nCol].pTypeInfo = NULL;  
        dbcoldesc[nCol].rgPropertySets = new DBPROPSET;  
        dbcoldesc[nCol].pclsid = NULL;  
        dbcoldesc[nCol].cPropertySets = 1;  
        dbcoldesc[nCol].ulColumnSize = 0;  
        dbcoldesc[nCol].dbcid.eKind = DBKIND_NAME;  
        dbcoldesc[nCol].wType = DBTYPE_I4;  
        dbcoldesc[nCol].bPrecision = 0;  
        dbcoldesc[nCol].bScale = 0;  
  
        dbcoldesc[nCol].rgPropertySets[0].rgProperties =   
            new DBPROP[NCOLPROPS_MAX];  
        dbcoldesc[nCol].rgPropertySets[0].cProperties = NCOLPROPS_MAX;  
        dbcoldesc[nCol].rgPropertySets[0].guidPropertySet =  
            DBPROPSET_COLUMN;  
  
        for (nProp = 0; nProp < NCOLPROPS_MAX; nProp++)  
            {  
            dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                dwOptions = DBPROPOPTIONS_REQUIRED;  
            dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].colid  
                 = DB_NULLID;  
  
            VariantInit(  
                &(dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                    vValue));  
  
            dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                vValue.vt = VT_BOOL;  
            }  
        }  
  
    // Set the column-specific information.  
    dbcoldesc[0].dbcid.uName.pwszName = L"OrderID";  
    dbcoldesc[0].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[0].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[0].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[1].dbcid.uName.pwszName = L"ProductID";  
    dbcoldesc[1].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[1].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[1].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[2].dbcid.uName.pwszName = L"UnitPrice";  
    dbcoldesc[2].wType = DBTYPE_CY;  
    dbcoldesc[2].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[2].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[2].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[3].dbcid.uName.pwszName = L"Quantity";  
    dbcoldesc[3].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[3].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[3].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[4].dbcid.uName.pwszName = L"Discount";  
    dbcoldesc[4].wType = DBTYPE_NUMERIC;  
    dbcoldesc[4].bPrecision = 2;  
    dbcoldesc[4].bScale = 2;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[1].dwPropertyID =   
        DBPROP_COL_DEFAULT;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[1].vValue.vt = VT_BSTR;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[1].vValue.bstrVal =  
        SysAllocString(L"0");  
    dbcoldesc[4].rgPropertySets[0].cProperties = 2;  
  
    // Set up the dbid for OrderDetails.  
    dbidTable.eKind = DBKIND_NAME;  
    dbidTable.uName.pwszName = L"OrderDetails";  
  
    if (FAILED(hr = pITableDefinition->CreateTable(NULL, &dbidTable,  
        nCols, dbcoldesc, NULL, 0, NULL, NULL, NULL)))  
        {  
        DumpError(pITableDefinition, IID_ITableDefinition);  
        goto SAFE_EXIT;  
        }  
  
SAFE_EXIT:  
    // Clean up dynamic allocation in the property sets.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        for (nProp = 0; nProp < NCOLPROPS_MAX; nProp++)  
            {  
            if (dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                vValue.vt == VT_BSTR)  
                {  
                SysFreeString(dbcoldesc[nCol].rgPropertySets[0].  
                    rgProperties[nProp].vValue.bstrVal);  
                }  
            }  
  
        delete [] dbcoldesc[nCol].rgPropertySets[0].rgProperties;  
        delete [] dbcoldesc[nCol].rgPropertySets;  
        }  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et index](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
