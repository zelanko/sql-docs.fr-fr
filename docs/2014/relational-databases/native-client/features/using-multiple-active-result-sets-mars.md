---
title: À l’aide de jeux de résultats actifs multiples (MARS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, MARS
- SQLNCLI, MARS
- data access [SQL Server Native Client], MARS
- Multiple Active Result Sets
- SQL Server Native Client, MARS
- MARS [SQL Server]
- SQL Server Native Client ODBC driver, MARS
ms.assetid: ecfd9c6b-7d29-41d8-af2e-89d7fb9a1d83
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c5cbf5efeb5b5381636b57d50b86a5affa4a2595
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68206631"
---
# <a name="using-multiple-active-result-sets-mars"></a>Utilisation de MARS (Multiple Active Result Sets)
  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] a introduit la prise en charge de MARS (Multiple Active Result Sets) dans les applications accédant au [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. Dans les versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], les applications de base de données ne pouvaient pas gérer plusieurs instructions actives sur une connexion. Lors de l'utilisation de jeux de résultats [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] par défaut, l'application devait traiter ou annuler tous les jeux de résultats d'un lot avant de pouvoir exécuter tout autre lot sur cette connexion. Un nouvel attribut de connexion a été introduit dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] de manière à ce que les applications puissent gérer plus d'une demande en attente par connexion et, plus spécifiquement, pour qu'elles puissent avoir plus d'un jeu de résultats par défaut actif par connexion.  
  
 MARS simplifie la conception d'applications grâce aux nouvelles fonctionnalités suivantes :  
  
-   Les applications peuvent avoir plusieurs jeux de résultats par défaut ouverts et entrelacer leur lecture.  
  
-   Les applications peuvent exécuter d'autres instructions (par exemple, INSERT, UPDATE, DELETE et des appels de procédure stockée) pendant que les jeux de résultats par défaut sont ouverts.  
  
 Voici quelques recommandations pour les applications utilisant MARS :  
  
-   Les jeux de résultats par défaut doivent être utilisés pour des jeux de résultats à courte durée de vie ou des jeux de résultats de petites taille générés par des instructions SQL uniques (SELECT, DML avec OUTPUT, RECEIVE, READ TEXT, etc.).  
  
-   Des curseurs côté serveur doivent être utilisés pour des jeux de résultats à plus longue durée de vie ou des jeux de résultats de grande taille générés par des instructions SQL uniques.  
  
-   Lisez systématiquement les résultats dans leur intégralité afin de savoir s'ils contiennent des demandes de procédure ou des traitements qui renvoient des résultats multiples.  
  
-   Si possible, utilisez des appels d'API pour modifier les propriétés de connexion et gérez les transactions plutôt que les instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
-   Dans MARS, l'emprunt d'identité à l'échelle de la session est interdit lorsque des traitements simultanés sont en cours d'exécution.  
  
> [!NOTE]  
>  Par défaut, la fonctionnalités MARS n'est pas activée. Pour utiliser MARS lors de la connexion à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, vous devez l'activer spécifiquement dans une chaîne de connexion. Pour plus d'informations, consultez les sections relatives au fournisseur OLE DB de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client et au pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, plus loin dans cette rubrique.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ne limite pas le nombre d'instructions actives sur une connexion.  
  
 Les applications conventionnelles n'ayant pas besoin que plus d'un traitement à instructions multiples ou plus d'une procédure stockée s'exécute simultanément peuvent tirer parti de MARS sans avoir à comprendre comment ce dernier est implémenté. Toutefois, les applications ayant des exigences plus complexes doivent prendre ceci compte.  
  
 MARS permet l'exécution entrelacée de plusieurs demandes au sein d'une connexion unique. Autrement dit, il permet à un traitement de s'exécuter, et au sein de cette exécution, il permet à d'autres demandes de s'exécuter. Notez toutefois que MARS est défini en terme d'entrelacement et non en terme d'exécution parallèle.  
  
 L'infrastructure de MARS permet l'exécution entrelacée de plusieurs traitements, mais l'exécution ne peut être basculée qu'à des points bien définis. Par ailleurs, la plupart des instructions doivent s'exécuter atomiquement au sein d'un lot. Instructions qui retournent des lignes au client, qui sont parfois appelés *points d’interruption*, sont autorisées à entrelacer l’exécution avant la fin, tandis que les lignes sont envoyées au client, par exemple :  
  
-   SELECT  
  
-   FETCH  
  
-   RECEIVE  
  
 Toute autre instruction exécutée dans le cadre d'une procédure stockée ou d'un traitement doit s'exécuter jusqu'à la fin pour que l'exécution puisse être basculée sur d'autres demandes MARS.  
  
 La manière exacte dont les lots entrelacent l'exécution dépend de plusieurs facteurs et il est difficile de prédire la séquence exacte dans laquelle les commandes de plusieurs traitements qui contiennent des points d'interruption seront exécutées. Soyez prudent afin d'éviter des effets secondaires non désirés liés à l'exécution entrelacée de traitements complexes de cet type.  
  
 Évitez des problèmes en utilisant des appels d'API plutôt que des instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)] pour gérer l'état de la connexion (SET, USE) et les transactions (BEGIN TRAN, COMMIT, ROLLBACK) en n'incluant pas ces instructions dans des traitements à instructions multiples qui contiennent également des points d'interruption, et en sérialisant l'exécution de tels traitements par la consommation ou l'annulation de tous les résultats.  
  
> [!NOTE]  
>  Un traitement ou une procédure stockée qui démarre une transaction manuelle ou implicite lorsque MARS est activé doit terminer la transaction avant que le traitement ne quitte. S'il ne le fait pas, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] restaure toutes les modifications apportées par la transaction lorsque le traitement se termine. Une telle transaction est gérée par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en tant que transaction dont l'étendue est définie par traitement. Il s'agit d'un nouveau type de transaction introduit dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] pour permettre aux procédures stockées valides existantes d'être utilisées lorsque MARS est activé. Pour plus d’informations sur les transactions délimitées au traitement, consultez [instructions Transaction &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transactions-transact-sql).  
  
 Pour obtenir un exemple d’utilisation de MARS à partir d’ADO, consultez [à l’aide d’ADO avec SQL Server Native Client](../applications/using-ado-with-sql-server-native-client.md).  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Fournisseur OLE DB SQL Server Native Client  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif prend en charge MARS via l’ajout de la propriété de l’initialisation SSPROP_INIT_MARSCONNECTION données source qui est implémentée dans le jeu de propriétés DBPROPSET_SQLSERVERDBINIT. De plus, un nouveau mot clé de chaîne de connexion, `MarsConn`, a été ajouté. Il accepte les valeurs `true` ou `false` ; `false` étant la valeur par défaut.  
  
 Le propriété de source de données DBPROP_MULTIPLECONNECTIONS a la valeur par défaut VARIANT_TRUE. Cela signifie que le fournisseur générera dynamiquement plusieurs connexions pour prendre en charge plusieurs objets command et rowset simultanés. Lorsque MARS est activé, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client peut prendre en charge plusieurs objets command et rowset sur une seule connexion, donc MULTIPLE_CONNECTIONS est définie à VARIANT_FALSE par défaut.  
  
 Pour plus d’informations sur les améliorations apportées au jeu de propriétés DBPROPSET_SQLSERVERDBINIT, consultez [propriétés d’initialisation et d’autorisation](../../native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
### <a name="sql-server-native-client-ole-db-provider-example"></a>Exemple de fournisseur OLE DB de SQL Server Native Client  
 Dans cet exemple, un objet de source de données est créé à l’aide de le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur OLE DB natif et que MARS est activé à l’aide de propriétés DBPROPSET_SQLSERVERDBINIT avant la création de l’objet de session.  
  
```  
#include <sqlncli.h>  
  
IDBInitialize *pIDBInitialize = NULL;  
IDBCreateSession *pIDBCreateSession = NULL;  
IDBProperties *pIDBProperties = NULL;  
  
// Create the data source object.  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL,  
   CLSCTX_INPROC_SERVER,  
   IID_IDBInitialize,   
    (void**)&pIDBInitialize);  
  
hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void**)&pIDBProperties);  
  
// Set the MARS property.  
DBPROP rgPropMARS;  
  
// The following is necessary since MARS is off by default.  
rgPropMARS.dwPropertyID = SSPROP_INIT_MARSCONNECTION;  
rgPropMARS.dwOptions = DBPROPOPTIONS_REQUIRED;  
rgPropMARS.dwStatus = DBPROPSTATUS_OK;  
rgPropMARS.colid = DB_NULLID;  
V_VT(&(rgPropMARS.vValue)) = VT_BOOL;  
V_BOOL(&(rgPropMARS.vValue)) = VARIANT_TRUE;  
  
// Create the structure containing the properties.  
DBPROPSET PropSet;  
PropSet.rgProperties = &rgPropMARS;  
PropSet.cProperties = 1;  
PropSet.guidPropertySet = DBPROPSET_SQLSERVERDBINIT;  
  
// Get an IDBProperties pointer and set the initialization properties.  
pIDBProperties->SetProperties(1, &PropSet);  
pIDBProperties->Release();  
  
// Initialize the data source object.  
hr = pIDBInitialize->Initialize();  
  
//Create a session object from a data source object.  
IOpenRowset * pIOpenRowset = NULL;  
hr = IDBInitialize->QueryInterface(IID_IDBCreateSession, (void**)&pIDBCreateSession));  
hr = pIDBCreateSession->CreateSession(  
   NULL,             // pUnkOuter  
   IID_IOpenRowset,  // riid  
  &pIOpenRowset ));  // ppSession  
  
// Create a rowset with a firehose mode cursor.  
IRowset *pIRowset = NULL;  
DBPROP rgRowsetProperties[2];  
  
// To get a firehose mode cursor request a   
// forward only read only rowset.  
rgRowsetProperties[0].dwPropertyID = DBPROP_IRowsetLocate;  
rgRowsetProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
rgRowsetProperties[0].dwStatus = DBPROPSTATUS_OK;  
rgRowsetProperties[0].colid = DB_NULLID;  
VariantInit(&(rgRowsetProperties[0].vValue));  
rgRowsetProperties[0].vValue.vt = VARIANT_BOOL;  
rgRowsetProperties[0].vValue.boolVal = VARIANT_FALSE;  
  
rgRowsetProperties[1].dwPropertyID = DBPROP_IRowsetChange;  
rgRowsetProperties[1].dwOptions = DBPROPOPTIONS_REQUIRED;  
rgRowsetProperties[1].dwStatus = DBPROPSTATUS_OK;  
rgRowsetProperties[1].colid = DB_NULLID;  
VariantInit(&(rgRowsetProperties[1].vValue));  
rgRowsetProperties[1].vValue.vt = VARIANT_BOOL;  
rgRowsetProperties[1].vValue.boolVal = VARIANT_FALSE;  
  
DBPROPSET rgRowsetPropSet[1];  
rgRowsetPropSet[0].rgProperties = rgRowsetProperties  
rgRowsetPropSet[0].cProperties = 2  
rgRowsetPropSet[0].guidPropertySet = DBPROPSET_ROWSET;  
  
hr = pIOpenRowset->OpenRowset (NULL,  
   &TableID,  
   NULL,  
   IID_IRowset,  
   1,  
   rgRowsetPropSet  
   (IUnknown**)&pIRowset);  
```  
  
## <a name="sql-server-native-client-odbc-driver"></a>Pilote ODBC SQL Server Native Client  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge MARS par le biais ajouts à la [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) et [SQLGetConnectAttr](../../native-client-odbc-api/sqlgetconnectattr.md) fonctions. SQL_COPT_SS_MARS_ENABLED a été ajouté pour accepter SQL_MARS_ENABLED_YES ou SQL_MARS_ENABLED_NO ; SQL_MARS_ENABLED_NO étant la valeur par défaut. De plus, un nouveau mot clé de chaîne de connexion, `Mars_Connection`, a été ajouté. Il accepte les valeurs « yes » ou « non » ; «no » étant la valeur par défaut.  
  
### <a name="sql-server-native-client-odbc-driver-example"></a>Exemple de pilote ODBC SQL Server Native Client  
 Dans cet exemple, le **SQLSetConnectAttr** fonction est utilisée pour activer MARS avant d’appeler le **SQLDriverConnect** (fonction) pour se connecter à la base de données. Une fois que la connexion est établie, deux **SQLExecDirect** fonctions sont appelées pour créer deux jeux de résultats distincts sur la même connexion.  
  
```  
#include <sqlncli.h>  
  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_MARS_ENABLED, SQL_MARS_ENABLED_YES, SQL_IS_UINTEGER);  
SQLDriverConnect(hdbc, hwnd,   
   "DRIVER=SQL Server Native Client 10.0;  
   SERVER=(local);trusted_connection=yes;", SQL_NTS, szOutConn,   
   MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt1);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt2);  
  
// The 2nd execute would have failed with connection busy error if  
// MARS were not enabled.  
SQLExecDirect(hstmt1, L"SELECT * FROM Authors", SQL_NTS);  
SQLExecDirect(hstmt2, L"SELECT * FROM Titles", SQL_NTS);  
  
// Result set processing can interleave.  
SQLFetch(hstmt1);  
SQLFetch(hstmt2);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](sql-server-native-client-features.md)   
 [Utilisation de jeux de résultats SQL Server par défaut](../../native-client-odbc-cursors/implementation/using-sql-server-default-result-sets.md)  
  
  
