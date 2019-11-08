---
title: bcp_bind | Microsoft Docs
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_bind
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_bind function
ms.assetid: 6e335a5c-64b2-4bcf-a88f-35dc9393f329
author: markingmyname
ms.author: maghan
ms.custom: ''
ms.reviewer: ''
ms.date: 03/14/2017
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 601a584a315eba7013c086dc59c9fb5bfeff8693
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73783221"
---
# <a name="bcp_bind"></a>bcp_bind

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Lie les données d'une variable de programme à une colonne de table pour une copie en bloc dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

## <a name="syntax"></a>Syntaxe

```  
  
RETCODE bcp_bind (  
        HDBC hdbc,
        LPCBYTE pData,  
        INT cbIndicator,  
        DBINT cbData,  
        LPCBYTE pTerm,  
        INT cbTerm,  
        INT eDataType,  
        INT idxServerCol);  
```  
  
## <a name="arguments"></a>Arguments

 *hdbc*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
 *pData*  
 Pointeur vers les données copiées. Si *eDataType* a la valeur SQLTEXT, SQLNTEXT, SQLXML, SQLUDT, SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SqlBinary, SQLNCHAR ou SQLIMAGE, *pData* peut être null. Un *pData* null indique que des valeurs de données longues sont envoyées à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans des segments à l’aide de [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md). L’utilisateur doit uniquement définir *pData* sur la valeur null si la colonne correspondant au champ lié à l’utilisateur est une colonne BLOB, sinon **bcp_bind** échoue.  
  
 Si les indicateurs sont présents dans les données, ils apparaissent directement en mémoire avant les données. Le paramètre *pData* pointe vers la variable indicateur dans ce cas, et la largeur de l’indicateur, le paramètre *cbIndicator* , est utilisée par la copie en bloc pour traiter correctement les données utilisateur.  
  
 *cbIndicator*  
 Longueur, en octets, d'un indicateur de longueur ou d'un indicateur null pour les données de la colonne. Les valeurs de longueur d'indicateur valides sont 0 (quand aucun indicateur n'est utilisé), 1, 2, 4 ou 8. Les indicateurs apparaissent directement en mémoire avant les données. Par exemple, la définition de type de structure suivante peut être utilisée pour insérer les valeurs entières dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de la copie en bloc :  
  
```
typedef struct tagBCPBOUNDINT  
    {  
    int iIndicator;  
    int Value;  
    } BCPBOUNDINT;  
```  
  
 Dans le cas de l’exemple, le paramètre *pData* est défini sur l’adresse d’une instance déclarée de la structure, l’adresse du membre de la structure BCPBOUNDINT *iIndicator* . Le paramètre *cbIndicator* est défini sur la taille d’un entier (sizeof (int)) et le paramètre *cbData* sur la valeur de la taille d’un entier (sizeof (int)). Pour copier en bloc une ligne sur le serveur contenant une valeur NULL pour la colonne liée, la valeur du membre *iIndicator* de l’instance doit être définie sur SQL_NULL_DATA.  
  
 *cbData*  
 Nombre d'octets de données dans la variable de programme, à l'exclusion de tout indicateur de longueur ou indicateur null ou terminateur.  
  
 La définition de *cbData* sur SQL_NULL_DATA signifie que toutes les lignes copiées sur le serveur contiennent une valeur null pour la colonne.  
  
 La définition de *cbData* sur SQL_VARLEN_DATA indique que le système utilisera un terminateur de chaîne ou une autre méthode pour déterminer la longueur des données copiées.  
  
 Pour les types de données de longueur fixe, tels que les entiers, le type de données indique la longueur des données au système. Par conséquent, pour les types de données de longueur fixe, *cbData* peut être SQL_VARLEN_DATA en toute sécurité ou la longueur des données.  
  
 Pour les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les types de données binaires et de caractères, *cbData* peut être SQL_VARLEN_DATA, SQL_NULL_DATA, une valeur positive ou 0. Si *cbData* est SQL_VARLEN_DATA, le système utilise un indicateur de longueur/null (le cas échéant) ou une séquence de marque de fin pour déterminer la longueur des données. Si les deux sont fournis, le système utilise celui qui se traduit par la quantité de données à copier la moins élevée. Si *cbData* est SQL_VARLEN_DATA, le type de données de la colonne est un caractère [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou un type binaire, et ni un indicateur de longueur ni une séquence de marque de fin n’est spécifié, le système retourne un message d’erreur.  
  
 Si *cbData* est égal à 0 ou à une valeur positive, le système utilise *cbData* comme longueur de données. Toutefois, si, en plus d’une valeur *cbData* positive, un indicateur de longueur ou une séquence de terminaison est fourni, le système détermine la longueur des données à l’aide de la méthode qui produit le moins de données copiées.  
  
 La valeur du paramètre *cbData* représente le nombre d’octets de données. Si les données caractères sont représentées par des caractères larges Unicode, une valeur de paramètre *cbData* positive représente le nombre de caractères multiplié par la taille en octets de chaque caractère.  
  
 *pTerm*  
 Pointeur vers le modèle d'octet, s'il existe, qui marque la fin de cette variable de programme. Par exemple, les chaines C ANSI et MBCS ont habituellement un terminateur d'1 octet (\0).  
  
 Si aucune marque de fin n’est définie pour la variable, affectez la valeur NULL à *pterm* .  
  
 Vous pouvez utiliser une chaîne vide ("") pour désigner l'indicateur de fin C null comme terminateur de variable de programme. Étant donné que la chaîne vide se terminant par un caractère null constitue un octet unique (l’octet de terminateur lui-même), affectez la valeur 1 à *cbTerm avec* . Par exemple, pour indiquer que la chaîne dans *szName* se termine par un caractère null et que la marque de fin doit être utilisée pour indiquer la longueur :  
  
```
bcp_bind(hdbc, szName, 0,  
   SQL_VARLEN_DATA, "", 1,  
   SQLCHARACTER, 2)  
```

 Une forme non terminée de cet exemple peut indiquer que 15 caractères sont copiés de la variable *szName* vers la deuxième colonne de la table liée :  

```
bcp_bind(hdbc, szName, 0, 15,
   NULL, 0, SQLCHARACTER, 2)  
```

 L'interface de programmation d'applications (API) de la copie en bloc procède à la conversion des caractères Unicode vers MBCS en fonction des besoins. Veillez à définir correctement la chaîne d'octet de marque de fin et la longueur de la chaîne d'octets. Par exemple, pour indiquer que la chaîne dans *szName* est une chaîne Unicode à caractères larges, se termine par la valeur de terminateur NULL Unicode :  
  
```  
bcp_bind(hdbc, szName, 0,
   SQL_VARLEN_DATA, L"",  
   sizeof(WCHAR), SQLNCHAR, 2)  
```  
  
 Si la colonne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] liée est un caractère élargi, aucune conversion n’est effectuée sur [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md). Si la colonne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possède MBCS comme type de caractère, la conversion des caractères larges en caractères multioctets s'effectue quand les données sont envoyées à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *cbTerm avec*  
 Nombre d'octets présents dans le terminateur de la variable de programme, s'il existe. Si aucune marque de fin n’est définie pour la variable, affectez la valeur 0 à *cbTerm avec* .  

*eDataType* Type de données C de la variable de programme. Les données de la variable de programme sont converties dans le type de la colonne de base de données. Si ce paramètre est égal à 0, aucune conversion n'est effectuée.  

Le paramètre *eDataType* est énuméré par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les jetons de type de données dans sqlncli. h, et non les énumérateurs de type de données C ODBC. Par exemple, vous pouvez spécifier un entier à deux octets, type ODBC SQL_C_SHORT, à l'aide du type SQLINT2 propre à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] introduit la prise en charge des jetons de type de données SQLXML et SQLUDT dans le paramètre **_eDataType_** .  

Le tableau suivant répertorie les types de données énumérées valides et les types de données ODBC C correspondants.

|eDataType|Type C|
|-----------------------|------------|  
|SQLTEXT|char *|  
|SQLNTEXT|wchar_t *|  
|SQLCHARACTER|char *|  
|SQLBIGCHAR|char *|  
|SQLVARCHAR|char *|  
|SQLBIGVARCHAR|char *|  
|SQLNCHAR|wchar_t *|  
|SQLNVARCHAR|wchar_t *|  
|SQLBINARY|unsigned char *|  
|SQLBIGBINARY|unsigned char *|  
|SQLVARBINARY|unsigned char *|  
|SQLBIGVARBINARY|unsigned char *|  
|SQLBIT|char|  
|SQLBITN|char|  
|SQLINT1|char|  
|SQLINT2|short int|  
|SQLINT4|int|  
|SQLINT8|_int64|  
|SQLINTN|*cbIndicator*<br /> 1: SQLINT1<br /> 2: SQLINT2<br /> 4: SQLINT4<br /> 8: SQLINT8|  
|SQLFLT4|float|  
|SQLFLT8|float|  
|SQLFLTN|*cbIndicator*<br /> 4: SQLFLT4<br /> 8: SQLFLT8|  
|SQLDECIMALN|SQL_NUMERIC_STRUCT|  
|SQLNUMERICN|SQL_NUMERIC_STRUCT|  
|SQLMONEY|DBMONEY|  
|SQLMONEY4|DBMONEY4|  
|SQLMONEYN|*cbIndicator*<br /> 4: SQLMONEY4<br /> 8: SQLMONEY|  
|SQLTIMEN|SQL_SS_TIME2_STRUCT|  
|SQLDATEN|SQL_DATE_STRUCT|  
|SQLDATETIM4|DBDATETIM4|  
|SQLDATETIME|DBDATETIME|  
|SQLDATETIMN|*cbIndicator*<br /> 4: SQLDATETIM4<br /> 8: SQLDATETIME|  
|SQLDATETIME2N|SQL_TIMESTAMP_STRUCT|  
|SQLDATETIMEOFFSETN|SQL_SS_TIMESTAMPOFFSET_STRUCT|  
|SQLIMAGE|unsigned char *|  
|SQLUDT|unsigned char *|  
|SQLUNIQUEID|SQLGUID|  
|SQLVARIANT|*Tout type de données sauf :*<br />-   text<br />-   ntext<br />-   image<br />-   varchar(max)<br />-   varbinary(max)<br />-   nvarchar(max)<br />-   xml<br />-   timestamp|  
|SQLXML|*Types de données C pris en charge :*<br />-   char*<br />-   wchar_t *<br />-   unsigned char *|  

*idxServerCol* Position ordinale de la colonne dans la table de base de données dans laquelle les données sont copiées. La première colonne d'une table est la colonne 1. La position ordinale d'une colonne est indiquée par [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md).  
  
## <a name="returns"></a>Valeur renvoyée

 SUCCEED ou FAIL.

## <a name="remarks"></a>Notes

Utilisez **bcp_bind** pour une façon rapide et efficace de copier des données à partir d’une variable de programme dans une table de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

Appelez [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) avant d’appeler cette fonction ou toute autre fonction de copie en bloc. L’appel de **bcp_init** définit la table cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour la copie en bloc. Lors de l’appel de **bcp_init** pour une utilisation avec **bcp_bind** et [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md), le paramètre **bcp_init** _szDataFile_ , qui indique le fichier de données, a la valeur null ; le paramètre **bcp_init**_eDirection_ est défini sur DB_IN.  

Effectuez un appel de **bcp_bind** distinct pour chaque colonne de la table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans laquelle vous souhaitez effectuer la copie. Une fois les appels de **bcp_bind** nécessaires effectués, appelez **bcp_sendrow** pour envoyer une ligne de données à partir de vos variables de programme vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La reliaison des colonnes n'est pas prise en charge.

Chaque fois que vous souhaitez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valider les lignes déjà reçues, appelez [bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md). Par exemple, appelez **bcp_batch** une fois pour chaque ligne de 1000 insérée ou à tout autre intervalle.  

Lorsqu’il n’y a plus de lignes à insérer, appelez [bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md). L'échec de cette opération entraîne une erreur.

Les paramètres de contrôle de paramètre, spécifiés avec [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md), n’ont aucun effet sur les transferts de lignes **bcp_bind** .  

Si *pData* pour une colonne a la valeur null, car sa valeur sera fournie par les appels à [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md), toutes les colonnes suivantes avec *EDATATYPE* défini sur SQLTEXT, SQLNTEXT, SQLXML, SQLUDT, SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SqlBinary, SQLNCHAR, ou SQLIMAGE doit également être lié avec *pData* défini sur null, et leurs valeurs doivent également être fournies par des appels à **bcp_moretext**.  

Pour les nouveaux types de valeur de grande taille, tels que **varchar (max)** , **varbinary (max)** ou **nvarchar (max)** , vous pouvez utiliser SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SqlBinary et SQLNCHAR comme indicateurs de type dans le paramètre *eDataType* .  

Si *cbTerm avec* n’est pas égal à 0, toute valeur (1, 2, 4 ou 8) est valide pour le préfixe (*cbIndicator*). Dans ce cas, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client recherche la marque de fin, calcule la longueur des données par rapport au terminateur (*i*) et affecte à *cbData* la valeur la plus petite et la valeur du préfixe.  

Si *cbTerm avec* a la valeur 0 et que *cbIndicator* (le préfixe) n’est pas égal à 0, *cbIndicator* doit avoir la valeur 8. Le préfixe de 8 octets peut prendre les valeurs suivantes :  

- 0xFFFFFFFFFFFFFFFF signifie une valeur NULL pour le champ  

- 0xFFFFFFFFFFFFFFFE est traité comme une valeur de préfixe spéciale, qui est utilisée pour envoyer efficacement des données par segments au serveur. Le format des données avec ce préfixe particulier est :  

- < SPECIAL_PREFIX > \<0 ou plusieurs segments de données > < ZERO_CHUNK > où :  

- SPECIAL_PREFIX est 0xFFFFFFFFFFFFFFFE  

- DATA_CHUNK est un préfixe de 4 octets contenant la longueur du segment, suivi des données réelles dont la longueur est spécifiée dans le préfixe de 4 octets.  

- ZERO_CHUNK est une valeur de 4 octets contenant uniquement des zéros (00000000) indiquant la fin des données.  

- Toute autre longueur valide de 8 octets est traitée comme une longueur de données normale.  

 L’appel de [bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) lors de l’utilisation de **bcp_bind** génère une erreur.  
  
## <a name="bcp_bind-support-for-enhanced-date-and-time-features"></a>Prise en charge de bcp_bind pour les fonctionnalités Date et Heure améliorées

Pour plus d’informations sur les types utilisés avec le paramètre *eDataType* pour les types date/heure, consultez [modifications de copie en bloc pour &#40;les types de&#41;date et d’heure améliorés OLE DB et ODBC](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).  

Pour plus d’informations, consultez [améliorations &#40;de la date&#41;et de l’heure ODBC](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  

## <a name="example"></a>Exemple
  
```
#include sql.h  
#include sqlext.h  
#include odbcss.h  
// Variables like henv not specified.  
HDBC      hdbc;  
char         szCompanyName[MAXNAME];  
DBINT      idCompany;  
DBINT      nRowsProcessed;  
DBBOOL      bMoreData;  
char*      pTerm = "\t\t";  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source; return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bcp.
if (bcp_init(hdbc, "comdb..accounts_info", NULL, NULL  
   DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Bind program variables to table columns.
if (bcp_bind(hdbc, (LPCBYTE) &idCompany, 0, sizeof(DBINT), NULL, 0,  
   SQLINT4, 1)    == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_bind(hdbc, (LPCBYTE) szCompanyName, 0, SQL_VARLEN_DATA,  
   (LPCBYTE) pTerm, strnlen(pTerm, sizeof(pTerm)), SQLCHARACTER, 2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
while (TRUE)  
   {  
   // Retrieve and process program data.
   if ((bMoreData = getdata(&idCompany, szCompanyName)) == TRUE)  
      {  
      // Send the data.
      if (bcp_sendrow(hdbc) == FAIL)  
         {  
         // Raise error and return.  
         return;  
         }  
      }  
   else  
      {  
      // Break out of loop.  
      break;  
      }  
   }  
  
// Terminate the bulk copy operation.  
if ((nRowsProcessed = bcp_done(hdbc)) == -1)  
   {  
   printf_s("Bulk-copy unsuccessful.\n");  
   return;  
   }  
  
printf_s("%ld rows copied.\n", nRowsProcessed);  
```  
  
## <a name="see-also"></a>Voir aussi

 [Fonctions de copie en bloc](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)
