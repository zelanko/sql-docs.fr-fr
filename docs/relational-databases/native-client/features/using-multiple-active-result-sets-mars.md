---
title: Utilisation de MARS (Multiple Active Result Sets) | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2b72f93aa979c504c0f6eeb6a3b867cc8360728f
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73761314"
---
# <a name="using-multiple-active-result-sets-mars"></a>Utilisation de MARS (Multiple Active Result Sets)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

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
> Par défaut, la fonctionnalité MARS n’est pas activée par le pilote. Pour utiliser MARS lors de la connexion à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, vous devez spécifiquement activer MARS dans une chaîne de connexion. Toutefois, certaines applications peuvent activer MARS par défaut, si l’application détecte que le pilote prend en charge MARS. Pour ces applications, vous pouvez désactiver MARS dans la chaîne de connexion, si nécessaire. Pour plus d'informations, consultez les sections relatives au fournisseur OLE DB de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client et au pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, plus loin dans cette rubrique.

 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ne limite pas le nombre d'instructions actives sur une connexion.  
  
 Les applications classiques qui n’ont pas besoin d’avoir plus d’un lot à instructions multiples ou d’une procédure stockée unique s’exécutant en même temps pourront tirer parti de MARS sans avoir à comprendre comment MARS est implémenté. Toutefois, les applications ayant des exigences plus complexes doivent prendre ceci compte.  
  
 MARS permet l'exécution entrelacée de plusieurs demandes au sein d'une connexion unique. Autrement dit, il permet à un traitement de s'exécuter, et au sein de cette exécution, il permet à d'autres demandes de s'exécuter. Notez toutefois que MARS est défini en terme d'entrelacement et non en terme d'exécution parallèle.  
  
 L'infrastructure de MARS permet l'exécution entrelacée de plusieurs traitements, mais l'exécution ne peut être basculée qu'à des points bien définis. Par ailleurs, la plupart des instructions doivent s'exécuter atomiquement au sein d'un lot. Les instructions qui retournent des lignes au client, parfois appelées « *points de rendement*», sont autorisées à entrelacer l’exécution avant la fin de l’envoi des lignes au client, par exemple :  
  
-   SELECT  
  
-   FETCH  
  
-   RECEIVE  
  
 Toute autre instruction exécutée dans le cadre d'une procédure stockée ou d'un traitement doit s'exécuter jusqu'à la fin pour que l'exécution puisse être basculée sur d'autres demandes MARS.  
  
 La manière exacte dont les lots entrelacent l'exécution dépend de plusieurs facteurs et il est difficile de prédire la séquence exacte dans laquelle les commandes de plusieurs traitements qui contiennent des points d'interruption seront exécutées. Soyez prudent afin d'éviter des effets secondaires non désirés liés à l'exécution entrelacée de traitements complexes de cet type.  
  
 Évitez des problèmes en utilisant des appels d'API plutôt que des instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)] pour gérer l'état de la connexion (SET, USE) et les transactions (BEGIN TRAN, COMMIT, ROLLBACK) en n'incluant pas ces instructions dans des traitements à instructions multiples qui contiennent également des points d'interruption, et en sérialisant l'exécution de tels traitements par la consommation ou l'annulation de tous les résultats.  
  
> [!NOTE]  
>  Un traitement ou une procédure stockée qui démarre une transaction manuelle ou implicite lorsque MARS est activé doit terminer la transaction avant que le traitement ne quitte. S'il ne le fait pas, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] restaure toutes les modifications apportées par la transaction lorsque le traitement se termine. Une telle transaction est gérée par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en tant que transaction dont l'étendue est définie par traitement. Il s'agit d'un nouveau type de transaction introduit dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] pour permettre aux procédures stockées valides existantes d'être utilisées lorsque MARS est activé. Pour plus d’informations sur les transactions dont l’étendue est définie par traitement, consultez [instructions &#40;de transaction Transact-&#41;SQL](~/t-sql/statements/statements.md).  
  
 Pour obtenir un exemple d’utilisation de MARS à partir d’ADO, consultez [utilisation d’ADO avec SQL Server Native Client](../../../relational-databases/native-client/applications/using-ado-with-sql-server-native-client.md).  
  
## <a name="in-memory-oltp"></a>OLTP en mémoire  
 L’OLTP en mémoire prend en charge MARS à l’aide de requêtes et de procédures stockées compilées en mode natif. MARS permet de demander des données à partir de plusieurs requêtes sans avoir à récupérer complètement chaque jeu de résultats avant d’envoyer une demande d’extraction de lignes à partir d’un nouveau jeu de résultats. Pour lire correctement à partir de plusieurs jeux de résultats ouverts, vous devez utiliser une connexion MARS activée.  
  
 MARS est désactivé par défaut. vous devez donc l’activer explicitement en ajoutant `MultipleActiveResultSets=True` à une chaîne de connexion. L’exemple suivant montre comment se connecter à une instance de SQL Server et spécifier que MARS est activé :  
  
```  
Data Source=MSSQL; Initial Catalog=AdventureWorks; Integrated Security=SSPI; MultipleActiveResultSets=True  
```  
  
 MARS avec OLTP en mémoire est fondamentalement identique à MARS dans le reste du moteur SQL. La liste suivante répertorie les différences lors de l’utilisation de MARS dans les tables optimisées en mémoire et les procédures stockées compilées en mode natif.  
  
 **MARS et tables optimisées en mémoire**  
  
 Voici les différences entre les tables sur disque et les tables mémoire optimisées lors de l’utilisation d’une connexion MARS activée :  
  
-   Deux instructions peuvent modifier des données dans le même objet cible, mais si elles tentent de modifier le même enregistrement, un conflit d’écriture entraîne l’échec de la nouvelle opération. Toutefois, si les deux opérations modifient des enregistrements différents, les opérations échouent.  
  
-   Chaque instruction s’exécute sous le niveau d’isolement d’instantané. les nouvelles opérations ne peuvent pas voir les modifications apportées par les instructions existantes. Même si les instructions simultanées sont exécutées dans le cadre de la même transaction, le moteur SQL crée des transactions de portée de lot pour chaque instruction isolée les unes des autres. Toutefois, les transactions dont l’étendue est définie par lot sont toujours liées, si bien que la restauration d’une transaction d’étendue de traitement affecte les autres dans le même lot.  
  
-   Les opérations DDL ne sont pas autorisées dans les transactions utilisateur afin qu’elles échouent immédiatement.  
  
 **MARS et procédures stockées compilées en mode natif**  
  
 Les procédures stockées compilées en mode natif peuvent s’exécuter dans les connexions MARS et peuvent provoquer une exécution vers une autre instruction uniquement lorsqu’un point de rendement est rencontré. Un point de rendement requiert une instruction SELECT, qui est la seule instruction au sein d’une procédure stockée compilée en mode natif qui peut provoquer une exécution vers une autre instruction. Si une instruction SELECT n’est pas présente dans la procédure, elle ne peut pas être exécutée jusqu’à la fin avant que d’autres instructions commencent.  
  
 **Transactions de l’OLTP en mémoire et MARS**  
  
 Les modifications apportées par les instructions et les blocs Atomic entrelacés sont isolés les uns des autres. Par exemple, si une instruction ou un bloc Atomic effectue des modifications, puis produit l’exécution dans une autre instruction, la nouvelle instruction ne verra pas les modifications apportées par la première instruction. En outre, quand la première instruction reprend l’exécution, elle ne voit pas les modifications apportées par d’autres instructions. Les instructions ne voient que les modifications qui sont terminées et validées avant le début de l’instruction.  
  
 Une nouvelle transaction utilisateur peut être démarrée dans la transaction de l’utilisateur en cours à l’aide de l’instruction BEGIN TRANSACTION. cette opération est prise en charge uniquement en mode Interop, de sorte que l’BEGIN TRANSACTION ne peut être appelé qu’à partir d’une instruction T-SQL, et non à partir d’un stocké compilé en mode natif procédures. Vous pouvez créer un point d’enregistrement dans une transaction en utilisant SAVE TRANSACTION ou un appel d’API à transaction. Enregistrez (save_point_name) pour revenir au point de sauvegarde. Cette fonctionnalité est également activée uniquement à partir d’instructions T-SQL, et non à partir de procédures stockées compilées en mode natif.  
  
 **Index MARS et ColumnStore**  
  
 SQL Server (à partir de 2016) prend en charge MARS avec les index ColumnStore. SQL Server 2014 utilise MARS pour les connexions en lecture seule à des tables avec un index columnstore.    Toutefois, SQL Server 2014 ne prend pas en charge MARS pour les opérations de langage de manipulation de données (DML) simultanées sur une table avec un index columnstore. Quand ce cas se produit, SQL Server met fin aux connexions et annule les transactions.   SQL Server 2012 a des index ColumnStore en lecture seule et MARS ne s’y applique pas.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Fournisseur OLE DB SQL Server Native Client  
 Le fournisseur d’OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client prend en charge MARS par le biais de l’ajout de la propriété d’initialisation de la source de données SSPROP_INIT_MARSCONNECTION, qui est implémentée dans le jeu de propriétés DBPROPSET_SQLSERVERDBINIT. De plus, un nouveau mot clé de chaîne de connexion, **MarsConn**, a été ajouté. Il accepte les valeurs **true** ou **false** ; la valeur par défaut est **false** .  
  
 Le propriété de source de données DBPROP_MULTIPLECONNECTIONS a la valeur par défaut VARIANT_TRUE. Cela signifie que le fournisseur générera dynamiquement plusieurs connexions pour prendre en charge plusieurs objets command et rowset simultanés. Lorsque MARS est activé, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client peut prendre en charge plusieurs objets Command et rowset sur une seule connexion, donc MULTIPLE_CONNECTIONS est défini sur VARIANT_FALSE par défaut.  
  
 Pour plus d’informations sur les améliorations apportées au jeu de propriétés DBPROPSET_SQLSERVERDBINIT, consultez [propriétés d’initialisation et d’autorisation](../../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
### <a name="sql-server-native-client-ole-db-provider-example"></a>Exemple de fournisseur OLE DB de SQL Server Native Client  
 Dans cet exemple, un objet de source de données est créé à l’aide du fournisseur de OLE DB natif [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], et MARS est activé à l’aide de la propriété DBPROPSET_SQLSERVERDBINIT définie avant la création de l’objet de session.  
  
```cpp
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
 Le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client prend en charge MARS par le biais d’ajouts aux fonctions [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) et [SQLGetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) . SQL_COPT_SS_MARS_ENABLED a été ajouté pour accepter SQL_MARS_ENABLED_YES ou SQL_MARS_ENABLED_NO ; SQL_MARS_ENABLED_NO étant la valeur par défaut. En outre, un nouveau mot clé de chaîne de connexion, **Mars_Connection**, a été ajouté. Il accepte les valeurs « yes » ou « non » ; «no » étant la valeur par défaut.  
  
### <a name="sql-server-native-client-odbc-driver-example"></a>Exemple de pilote ODBC SQL Server Native Client  
 Dans cet exemple, la fonction **SQLSetConnectAttr** est utilisée pour activer mars avant d’appeler la fonction **SQLDriverConnect** pour connecter la base de données. Une fois la connexion établie, deux fonctions **SQLExecDirect** sont appelées pour créer deux jeux de résultats distincts sur la même connexion.  
  
```cpp
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
 [Fonctionnalités de SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [Utilisation de jeux de résultats SQL Server par défaut](../../../relational-databases/native-client-odbc-cursors/implementation/using-sql-server-default-result-sets.md)  
  
  
