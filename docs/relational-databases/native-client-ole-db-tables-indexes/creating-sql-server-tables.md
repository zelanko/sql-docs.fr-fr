---
title: Création de tables SQL Server | Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6f3d1ae29828e18cf98941666e7884e70115ba39
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301860"
---
# <a name="creating-sql-server-tables"></a>Création de tables SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native Client OLE DB expose la fonction **ITableDefinition::CreateTable,** permettant aux consommateurs de créer des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables. Les consommateurs utilisent **CreateTable** pour créer des tables permanentes nommées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le consommateur, et des tables permanentes ou temporaires avec des noms uniques générés par le fournisseur de DB OLE de client autochtone.  
  
 Lorsque le consommateur appelle **ITableDefinition::CreateTable**, si la valeur de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] propriété DBPROP_TBL_TEMPTABLE est VARIANT_TRUE, le fournisseur de DB OLE de client autochtone génère un nom de table temporaire pour le consommateur. Le consommateur attribue la valeur NULL au paramètre *pTableID* de la méthode **CreateTable**. Les tables temporaires avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les noms générés par le fournisseur native De DB OLE de client ne figurent pas dans le jeu de ligne **TABLES,** mais sont accessibles par l’interface **IOpenRowset.**  
  
 Lorsque les consommateurs spécifier le nom de table dans le membre *pwszName* du syndicat *uName* dans le paramètre *pTableID,* le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone crée une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table avec ce nom. Des contraintes en matière d'affectation de noms aux tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'appliquent et le nom de la table peut indiquer une table permanente ou une table temporaire locale ou globale. Pour plus d’informations, voir [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md). Le paramètre *ppTableID* peut avoir la valeur NULL.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone peut générer les noms des tables permanentes ou temporaires. Lorsque le consommateur définit le paramètre *pTableID* à NULL et\*définit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *ppTableID* pour pointer vers un DBID valide , le fournisseur native De DB OLE client retourne le nom généré de la table dans le membre *pwszName* du syndicat *uName* de la DBID souligné par la valeur de *ppTableID*. Pour créer une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table temporaire nommée fournisseur OLE DB de client autochtone, le consommateur inclut la propriété de table OLE DB DBPROP_TBL_TEMPTABLE dans un ensemble de propriété de table référencé dans le paramètre *rgPropertySets.* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Les tables temporaires nommées par le fournisseur OLE DB de client autochtone sont locales.  
  
 **CreateTable** retourne DB_E_BADTABLEID si le membre *eKind* du paramètre *pTableID* n’indique pas DBKIND_NAME.  
  
## <a name="dbcolumndesc-usage"></a>Utilisation de la structure DBCOLUMNDESC  
 Le consommateur peut indiquer un type de données de colonne en utilisant soit le membre *pwszTypeName*, soit le membre *wType*. Si le consommateur spécifie le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans *pwszTypeName*, le fournisseur Native Client OLE DB ignore la valeur de *wType*.  
  
 S’il utilise le membre *pwszTypeName*, le consommateur spécifie le type de données à l’aide de noms du type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les noms de type de données valides sont les noms retournés dans la colonne TYPE_NAME de l'ensemble de lignes de schéma PROVIDER_TYPES.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE native Client reconnaît un sous-ensemble de valeurs DBTYPE énumérées OLE DB dans le membre *wType.* Pour plus d'informations, voir [Mappage de types de données dans ITableDefinition](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md).  
  
> [!NOTE]  
>  **CreateTable** retourne DB_E_BADTYPE si le consommateur choisit le membre *pTypeInfo* ou *pclsid* pour spécifier le type de données de colonne.  
  
 Le consommateur spécifie le nom de colonne dans le membre *pwszName* de l’union *uName* du membre *dbcid* DBCOLUMNDESC. Le nom de colonne est spécifié en tant que chaîne de caractères Unicode. Le membre *eKind* de *dbcid* doit être DBKIND_NAME. **CreateTable** retourne DB_E_BADCOLUMNID si le membre *eKind* n’est pas valide, si *pwszName* possède la valeur NULL ou si la valeur de *pwszName* n’est pas un identificateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide.  
  
 Toutes les propriétés de colonne sont disponibles dans toutes les colonnes définies pour la table. **CreateTable** peut retourner DB_S_ERRORSOCCURRED ou DB_E_ERRORSOCCURRED si les valeurs des propriétés sont en conflit. **CreateTable** retourne une erreur lorsque les paramètres des propriétés de colonne non valides entraîne un échec lors de la création de tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Les propriétés des colonnes dans une structure DBCOLUMNDESC se définissent de la manière suivante.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|DBPROP_COL_AUTOINCREMENT|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE Description : définit la propriété d'identité dans la colonne créée. Pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la propriété d'identité est valide pour une colonne unique au sein d'une table. La définition de la propriété à VARIANT_TRUE pour plus d’une seule colonne génère une erreur lorsque le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native Client OLE DB tente de créer la table sur le serveur.<br /><br /> La propriété d’identité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est uniquement valide pour les types **integer**, **numeric** et **decimal** lorsque l’échelle est définie sur 0. La définition de la propriété pour VARIANT_TRUE sur une colonne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tout autre type de données génère une erreur lorsque le fournisseur de DB OLE du client autochtone tente de créer la table sur le serveur.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone retourne DB_S_ERRORSOCCURRED quand DBPROP_COL_AUTOINCREMENT et DBPROP_COL_NULLABLE sont à la fois VARIANT_TRUE et la *dwOption* de DBPROP_COL_NULLABLE n’est pas DBPROPOPTIONS_REQUIRED. DB_E_ERRORSOCCURRED est retourné lorsque DBPROP_COL_AUTOINCREMENT et DBPROP_COL_NULLABLE sont tous les deux définis sur VARIANT_TRUE et quand la valeur *dwOption* de DBPROP_COL_NULLABLE est égale à DBPROPOPTIONS_REQUIRED. La colonne est définie avec la propriété d’identité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le membre *dwStatus* DBPROP_COL_NULLABLE est défini sur DBPROPSTATUS_CONFLICTING.|  
|DBPROP_COL_DEFAULT|R/W : lecture/écriture<br /><br /> Valeur par défaut : aucune<br /><br /> Description : crée une contrainte DEFAULT [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour la colonne.<br /><br /> Le membre *vValue* DBPROP peut appartenir aux types suivants. Le membre *vValue.vt* doit spécifier un type compatible avec le type de données de la colonne. Par exemple, le choix de BSTR N/A comme valeur par défaut d'une colonne définie en tant que DBTYPE_WSTR offre une valeur de correspondance compatible. Définir le même défaut sur une colonne définie comme DBTYPE_R8 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère une erreur lorsque le fournisseur native OLE DB tente de créer la table sur le serveur.|  
|DBPROP_COL_DESCRIPTION|R/W : lecture/écriture<br /><br /> Valeur par défaut : aucune<br /><br /> Description: La propriété DBPROP_COL_DESCRIPTION colonne n’est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pas implémentée par le fournisseur de DB OLE de client autochtone.<br /><br /> Le membre *dwStatus* de la structure DBPROP retourne DBPROPSTATUS_NOTSUPPORTED lorsque le consommateur tente d’écrire la valeur de propriété.<br /><br /> La mise en place de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] propriété ne constitue pas une erreur fatale pour le fournisseur de DB OLE du client autochtone. Si toutes les autres valeurs de paramètres sont valides, la table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est créée.|  
|DBPROP_COL_FIXEDLENGTH|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le fournisseur de DB OLE native Client utilise DBPROP_COL_FIXEDLENGTH pour déterminer la cartographie de type de données lorsque le consommateur définit le type de données d’une colonne en utilisant le membre *wType* du DBCOLUMNDESC. Pour plus d'informations, voir [Mappage de types de données dans ITableDefinition](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md).|  
|DBPROP_COL_NULLABLE|R/W : lecture/écriture<br /><br /> Valeur par défaut : aucune<br /><br /> Description : Lors de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la création de la table, le fournisseur de DB OLE du client autochtone indique si la colonne doit accepter des valeurs nulles si la propriété est définie. Lorsque la propriété n'est pas définie, l'aptitude de la colonne à valider la valeur NULL dépend de l'option de base de données par défaut ANSI_NULLS de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native Client OLE DB est un fournisseur conforme à l’ISO. Les sessions connectées affichent des comportements ISO. Si le consommateur ne définit pas DBPROP_COL_NULLABLE, les colonnes acceptent des valeurs NULL.|  
|DBPROP_COL_PRIMARYKEY|R/W : lecture/écriture<br /><br /> Défaut : VARIANT_FALSE Description : Lorsqu’VARIANT_TRUE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le fournisseur de DB OLE de client autochtone crée la colonne avec une contrainte KEY PRIMAIRE.<br /><br /> Si la propriété est définie comme une propriété de colonne, seule une colonne unique peut déterminer la contrainte. La configuration de la propriété VARIANT_TRUE pour plus d’une seule colonne renvoie une erreur lorsque le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone tente de créer la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.<br /><br /> Remarque : Le consommateur peut faire appel à la fonction **IIndexDefinition::CreateIndex** pour créer une contrainte PRIMARY KEY dans deux ou plusieurs colonnes.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone retourne DB_S_ERRORSOCCURRED quand DBPROP_COL_PRIMARYKEY et DBPROP_COL_UNIQUE sont à la fois VARIANT_TRUE et la *dwOption* de DBPROP_COL_UNIQUE n’est pas DBPROPOPTIONS_REQUIRED.<br /><br /> DB_E_ERRORSOCCURRED est retourné lorsque DBPROP_COL_PRIMARYKEY et DBPROP_COL_UNIQUE sont tous les deux définis sur VARIANT_TRUE et quand la valeur *dwOption* de DBPROP_COL_UNIQUE est égale à DBPROPOPTIONS_REQUIRED. La colonne est définie avec la propriété d’identité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le membre *dwStatus* DBPROP_COL_PRIMARYKEY est défini sur DBPROPSTATUS_CONFLICTING.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone renvoie une erreur lorsque DBPROP_COL_PRIMARYKEY et DBPROP_COL_NULLABLE sont tous deux VARIANT_TRUE.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de client autochtone renvoie une erreur à partir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du moment où le consommateur tente de créer une contrainte KEY PRIMARY sur une colonne de type de données invalides. Vous ne pouvez pas définir des contraintes PRIMARY KEY dans des colonnes créées avec les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**bit**, **text**, **ntext** et **image**.|  
|DBPROP_COL_UNIQUE|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE Description : applique une contrainte UNIQUE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à la colonne.<br /><br /> Si la propriété est définie comme une propriété de colonne, la contrainte est appliquée dans une seule colonne uniquement. Le consommateur peut se servir de la fonction **IIndexDefinition::CreateIndex** pour appliquer une contrainte UNIQUE à des valeurs combinées de deux ou plusieurs colonnes.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone retourne DB_S_ERRORSOCCURRED quand DBPROP_COL_PRIMARYKEY et DBPROP_COL_UNIQUE sont à la fois VARIANT_TRUE et *dwOption* n’est pas DBPROPOPTIONS_REQUIRED.<br /><br /> DB_E_ERRORSOCCURRED est retourné lorsque DBPROP_COL_PRIMARYKEY et DBPROP_COL_UNIQUE sont tous les deux définis sur VARIANT_TRUE et quand la valeur *dwOption* est égale à DBPROPOPTIONS_REQUIRED. La colonne est définie avec la propriété d’identité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le membre *dwStatus* DBPROP_COL_PRIMARYKEY est défini sur DBPROPSTATUS_CONFLICTING.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone retourne DB_S_ERRORSOCCURRED quand DBPROP_COL_NULLABLE et DBPROP_COL_UNIQUE sont à la fois VARIANT_TRUE et *dwOption n’est* pas DBPROPOPTIONS_REQUIRED.<br /><br /> DB_E_ERRORSOCCURRED est retourné lorsque DBPROP_COL_NULLABLE et DBPROP_COL_UNIQUE sont tous les deux définis sur VARIANT_TRUE et quand la valeur *dwOption* est égale à DBPROPOPTIONS_REQUIRED. La colonne est définie avec la propriété d’identité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le membre *dwStatus* DBPROP_COL_NULLABLE est défini sur DBPROPSTATUS_CONFLICTING.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de client autochtone renvoie une erreur à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] partir du moment où le consommateur tente de créer une contrainte UNIQUE sur une colonne de type de données invalides. Vous ne pouvez pas définir des contraintes UNIQUE sur des colonnes créées avec le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **bit**.|  
  
 Lorsque le consommateur appelle **ITableDefinition::CreateTable**, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native De DB OLE client interprète les propriétés de table comme suit.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|DBPROP_TBL_TEMPTABLE|R/W : lecture/écriture<br /><br /> Défaut : VARIANT_FALSE Description : Par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] défaut, le fournisseur de DB OLE de client autochtone crée des tables nommées par le consommateur. Lorsqu’VARIANT_TRUE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone génère un nom de table temporaire pour le consommateur. Le consommateur attribue la valeur NULL au paramètre *pTableID* de **CreateTable**. Le paramètre *ppTableID* doit contenir un pointeur valide.|  
  
 Si le consommateur demande qu’un achage soit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ouvert sur une table créée avec succès, le fournisseur de DB OLE native Client ouvre un jeu de ligne appuyé par un curseur. Toutes les propriétés de l'ensemble de lignes peuvent être indiquées dans les jeux de propriétés passés.  
  
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
 [Tableaux et indices](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
