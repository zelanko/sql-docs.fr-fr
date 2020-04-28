---
title: Conversion de DB-Library en copie en bloc ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- converting DB-Library to ODBC bulk copy
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], DB-Library bulk copy
- ODBC, bulk copy operations
- DB-Library bulk copy
ms.assetid: 0bc15bdb-f19f-4537-ac6c-f249f42cf07f
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b7e14018ea62edb5dd262b87ddbea467d1872132
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "73785190"
---
# <a name="converting-from-db-library-to-odbc-bulk-copy"></a>Conversion à partir de la bibliothèque de bases de données vers une copie en bloc ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  La conversion d’un programme de copie en bloc DB-Library vers ODBC est simple, car les fonctions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de copie en bloc prises en charge par le pilote ODBC native client sont similaires aux fonctions de copie en bloc de DB-Library, avec les exceptions suivantes :  
  
-   Les applications de bibliothèque de bases de données passent un pointeur à une structure DBPROCESS comme premier paramètre de fonctions de copie en bloc. Dans les applications ODBC, le pointeur DBPROCESS est remplacé par un handle de connexion ODBC.  
  
-   Les applications DB-Library appellent **BCP_SETL** avant de se connecter pour activer les opérations de copie en bloc sur un DBPROCESS. Les applications ODBC appellent plutôt [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) avant de se connecter pour activer les opérations en bloc sur un handle de connexion :  
  
    ```  
    SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP,  
        (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
    ```  
  
-   Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client ne prend pas en charge les gestionnaires d’erreurs et de messages DB-Library ; vous devez appeler **SQLGetDiagRec** pour recevoir les erreurs et les messages générés par les fonctions de copie en bloc ODBC. Les versions ODBC de fonctions de copie en bloc retournent les codes de retour de copie en bloc standard de SUCCEED ou FAILED, et non les codes de retour de style ODBC, tels que SQL_SUCCESS ou SQL_ERROR.  
  
-   Les valeurs spécifiées pour le paramètre DB-Library [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)*varlen* sont interprétées différemment du paramètre ODBC **bcp_bind**_cbData_ .  
  
    |Condition indiquée|Valeur *VARLEN* DB-Library|Valeur *CBDATA* ODBC|  
    |-------------------------|--------------------------------|-------------------------|  
    |Valeurs NULL fournies|0|-1 (SQL_NULL_DATA)|  
    |Données de variables fournies|-1|-10 (SQL_VARLEN_DATA)|  
    |Caractère de longueur nulle ou chaîne binaire|NA|0|  
  
     Dans DB-Library, une valeur *varlen* de-1 indique que les données de longueur variable sont fournies, ce qui, dans le *cbData* ODBC, est interprété comme signifiant que seules les valeurs NULL sont fournies. Modifiez les spécifications *VARLEN* DB-Library de-1 en SQL_VARLEN_DATA et toutes les spécifications *varlen* de 0 à SQL_NULL_DATA.  
  
-   Les **BCP_COLFMT**DB-Library_file_collen_ et ODBC [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)*cbUserData* ont le même problème que les paramètres **bcp_bind**_varlen_ et *cbData* indiqués ci-dessus. Remplacez les spécifications de *FILE_COLLEN* DB-Library de-1 par SQL_VARLEN_DATA et toutes les spécifications de *file_collen* comprises entre 0 et SQL_NULL_DATA.  
  
-   Le paramètre *iValue* de la fonction [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) ODBC est un pointeur void. Dans DB-Library, *iValue* était un entier. Effectuez un cast des valeurs pour le *IVALUE* ODBC vers void *.  
  
-   L’option **BCP_CONTROL** BCPMAXERRS spécifie le nombre de lignes individuelles pouvant comporter des erreurs avant l’échec d’une opération de copie en bloc. La valeur par défaut de BCPMAXERRS est 0 (échec de la première erreur) dans la version DB-Library de **bcp_control** et 10 dans la version ODBC. Les applications DB-Library qui dépendent de la valeur par défaut 0 pour terminer une opération de copie en bloc doivent être modifiées pour appeler le **BCP_CONTROL** ODBC afin de définir BCPMAXERRS sur 0.  
  
-   La fonction ODBC **bcp_control** prend en charge les options suivantes non prises en charge par la version DB-Library de **bcp_control**:  
  
    -   BCPODBC  
  
         Lorsque la valeur est TRUE, spécifie que les valeurs **DateTime** et **smalldatetime** enregistrées au format caractère auront le préfixe et le suffixe de séquence d’échappement d’horodateur ODBC. Cela s'applique seulement aux opérations BCP_OUT.  
  
         Avec BCPODBC défini sur FALSe, une valeur **DateTime** convertie en chaîne de caractères est sortie comme suit :  
  
        ```  
        1997-01-01 00:00:00.000  
        ```  
  
         Avec BCPODBC défini sur TRUE, la même valeur **DateTime** est générée comme suit :  
  
        ```  
        {ts '1997-01-01 00:00:00.000' }  
        ```  
  
    -   BCPKEEPIDENTITY  
  
         Si la valeur est TRUE, spécifie que les fonctions de copie en bloc insèrent les valeurs de données fournies pour les colonnes avec des contraintes d'identité. Si cela n'est pas défini, de nouvelles valeurs d'identités sont générées pour les lignes insérées.  
  
    -   BCPHINTS  
  
         Spécifie diverses optimisations de copie en bloc. Cette option ne peut pas être utilisée sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 6.5 ou antérieure.  
  
    -   BCPFILECP  
  
         Spécifie la page de codes du fichier de copie en bloc.  
  
    -   BCPUNICODEFILE  
  
         Spécifie qu'un fichier de copie en bloc en mode caractère est un fichier Unicode.  
  
-   La fonction **BCP_COLFMT** ODBC ne prend pas en charge l’indicateur *file_type* de SQLCHAR, car elle est en conflit avec le typedef ODBC SQLCHAR. Utilisez SQLCHARACTER à la place pour **bcp_colfmt**.  
  
-   Dans les versions ODBC des fonctions de copie en bloc, le format d’utilisation des valeurs **DateTime** et **smalldatetime** dans les chaînes de caractères est le format ODBC aaaa-mm-jj hh : mm : SS. sss ; les valeurs **smalldatetime** utilisent le format ODBC aaaa-mm-jj hh : mm : SS.  
  
     Les versions DB-Library des fonctions de copie en bloc acceptent les valeurs **DateTime** et **smalldatetime** dans les chaînes de caractères à l’aide de plusieurs formats :  
  
    -   Le format par défaut est *mmm jj aaaa hh : mmxx* , où *XX* est AM ou PM.  
  
    -   chaînes de caractères **DateTime** et **smalldatetime** dans n’importe quel format pris en charge par la fonction **DBConvert** de la bibliothèque DB-Library.  
  
    -   Lorsque la case **utiliser les paramètres internationaux** est cochée sous l’onglet **options** de la bibliothèque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de bases de l’utilitaire réseau client, les fonctions de copie en bloc de la bibliothèque de bases de la bibliothèque acceptent également les dates au format de date régional défini pour les paramètres régionaux du registre de l’ordinateur client.  
  
     Les fonctions de copie en bloc de DB-Library n’acceptent pas les formats **DateTime** et **smalldatetime** ODBC.  
  
     Si l'attribut d'instruction SQL_SOPT_SS_REGIONALIZE a la valeur SQL_RE_ON, les fonctions de copie en bloc ODBC acceptent les dates au format de date régional défini pour les paramètres régionaux du Registre de l'ordinateur client.  
  
-   Lorsque vous générez des valeurs **monétaires** au format caractère, les fonctions de copie en bloc ODBC fournissent quatre chiffres de précision et aucun séparateur de virgule. Les versions de DB-Library fournissent uniquement deux chiffres de précision et incluent les séparateurs de virgule.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution d’opérations de copie en bloc &#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)   
 [Bulk Copy Functions](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
