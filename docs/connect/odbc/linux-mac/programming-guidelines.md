---
title: Instructions de programmation | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2e3aac41bd87f52998edf366d7c3da2326de3f26
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="programming-guidelines"></a>Instructions de programmation
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)] Les fonctionnalités de programmation de la [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 et 13.1 pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] sur macOS et Linux sont basées sur ODBC dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client ([SQL Server Native Client (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151)). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Native Client est basé sur ODBC dans Windows Data Access Components ([de référence du programmeur ODBC](http://go.microsoft.com/fwlink/?LinkID=45250)).  

Une application ODBC peut utiliser Multiple Active Result Sets (MARS) et autres [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] des fonctionnalités spécifiques en incluant `/usr/local/include/msodbcsql.h` après avoir inclus les en-têtes unixODBC (`sql.h`, `sqlext.h`, `sqltypes.h`, et `sqlucode.h`). Puis utilisez les mêmes noms symboliques pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]-des éléments spécifiques que vous le feriez dans vos applications Windows ODBC.  

## <a name="available-features"></a>Fonctionnalités disponibles  
Les sections suivantes à partir de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] documentation Native Client pour ODBC ([SQL Server Native Client (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151)) sont valides lors de l’utilisation du pilote ODBC sur macOS et Linux :  

-   [Communication avec SQL Server (ODBC)](http://msdn.microsoft.com/library/ms131692.aspx)  
-   [Connexion et la requête prise en charge de délai d’attente](http://msdn.microsoft.com/library/ms130822.aspx)  
-   [Curseurs](http://msdn.microsoft.com/library/ms130794(SQL.110).aspx)  
-   [Date/heure améliorations (ODBC)](http://msdn.microsoft.com/library/bb677319.aspx)  
-   [L’exécution de requêtes (ODBC)](http://msdn.microsoft.com/library/ms131677.aspx)  
-   [Gestion des erreurs et des Messages](http://msdn.microsoft.com/library/ms131289.aspx)  
-   [Authentification Kerberos](http://msdn.microsoft.com/library/cc280459.aspx)  
-   [Types définis par l’utilisateur CLR volumineux (ODBC)](http://msdn.microsoft.com/library/bb677316.aspx)  
-   [Exécution de Transactions (ODBC) (à l’exception des transactions distribuées)](http://msdn.microsoft.com/library/ms131706.aspx)  
-   [Traitement des résultats (ODBC)](http://msdn.microsoft.com/library/ms130812.aspx)  
-   [Exécution de procédures stockées](http://msdn.microsoft.com/library/ms131440.aspx)
-   [Prise en charge des colonnes éparses (ODBC)](http://msdn.microsoft.com/library/cc280357.aspx)
-   [Chiffrement SSL](http://msdn.microsoft.com/library/ms131691.aspx)
-   [Tableau des paramètres table](https://docs.microsoft.com/en-us/sql/relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc)
-   [UTF-8 et UTF-16 pour l’API de commande et de données](http://msdn.microsoft.com/library/ff878241.aspx)
-   [À l’aide des fonctions de catalogue](http://msdn.microsoft.com/library/ms131490.aspx)  

## <a name="unsupported-features"></a>Fonctions non prises en charge

Les fonctionnalités suivantes n’ont pas été vérifiées fonctionne correctement dans cette version du pilote ODBC sur macOS et Linux :

-   Connexion de Cluster de basculement
-   [Résolution IP de réseau transparent](https://docs.microsoft.com/en-us/sql/connect/odbc/linux/using-transparent-network-ip-resolution)
-   [Suivi de pilote avancées](https://blogs.msdn.microsoft.com/mattn/2012/05/15/enabling-advanced-driver-tracing-for-the-sql-native-client-odbc-drivers/)

Les fonctionnalités suivantes ne sont pas disponibles dans cette version du pilote ODBC sur macOS et Linux : 

-   Les Transactions distribuées (attribut SQL_ATTR_ENLIST_IN_DTC n’est pas prise en charge)  
-   Mise en miroir de bases de données  
-   FILESTREAM  
-   Profilage des performances du pilote ODBC, présentés dans [SQLSetConnectAttr](http://go.microsoft.com/fwlink/?LinkId=234099)et les attributs de connexion liés aux performances suivants :  
    -   SQL_COPT_SS_PERF_DATA  
    -   SQL_COPT_SS_PERF_DATA_LOG  
    -   SQL_COPT_SS_PERF_DATA_LOG_NOW  
    -   SQL_COPT_SS_PERF_QUERY  
    -   SQL_COPT_SS_PERF_QUERY_INTERVAL  
    -   SQL_COPT_SS_PERF_QUERY_LOG  
-   SQLBrowseConnect  
-   Types d’intervalle C comme SQL_C_INTERVAL_YEAR_TO_MONTH (documentées dans [les identificateurs de Type de données et les descripteurs de](http://msdn.microsoft.com/library/ms716351(VS.85).aspx))
-   La valeur SQL_CUR_USE_ODBC de l’attribut SQL_ATTR_ODBC_CURSORS de la fonction SQLSetConnectAttr.

## <a name="character-set-support"></a>Prise en charge du jeu de caractères

Le client de codage peut être une des opérations suivantes :
  -  UTF-8
  -  ISO-8859-1.
  -  ISO-8859-2
  -  ISO-8859-3
  -  ISO-8859-4
  -  ISO-8859-5
  -  ISO-8859-6
  -  ISO-8859-7
  -  ISO-8859-8
  -  ISO-8859-9
  -  ISO-8859-13.
  -  ISO-8859-15
  
Les données SQLCHAR doivent être un des jeux de caractères pris en charge. Les données SQLWCHAR doivent être au format UTF-16LE (Little Endian).  

Si SQLDescribeParameter ne spécifie pas de type SQL sur le serveur, le pilote utilise le type SQL spécifié dans le paramètre *ParameterType* de SQLBindParameter. Si un type SQL de caractère étroit, comme SQL_VARCHAR, est spécifié dans SQLBindParameter, le pilote convertit les données fournies à partir de la page de codes du client à la valeur par défaut [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] page de codes. (La valeur par défaut [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] est généralement : page de codes 1252.) Si la page de codes du client n’est pas pris en charge, elle est définie au format UTF-8. Dans ce cas, le pilote convertit ensuite les données UTF-8 à la page de codes par défaut. Toutefois, une perte de données est possible. Si la page de codes 1252 ne peut pas représenter un caractère, le pilote le convertit en point d’interrogation (« ? »). Pour éviter cette perte de données, spécifiez un type de caractère SQL Unicode, comme SQL_NVARCHAR, dans SQLBindParameter. Dans ce cas, le pilote convertit les données Unicode fournies dans l’encodage UTF-8 en UTF-16 sans perte de données.

Il existe une différence de conversion de codage de texte entre Windows et de plusieurs versions de la bibliothèque iconv sur Linux et macOS. Les données de texte sont encodées dans la page de codes 1255 (hébreu) ont un seul point de code (0xCA) qui se comporte différemment lors de la conversion. Conversion de ce caractère en Unicode sur Windows génère un point de code UTF-16 de 0x05BA. La conversion au format Unicode sur macOS et Linux avec libiconv les versions antérieures à 1.15 génère un point de code UTF-16 de 0x00CA.

Quand des caractères multi-octets UTF-8 ou des substituts UTF-16 sont répartis entre les mémoires tampons SQLPutData, les données sont altérées. Utilisez des mémoires tampons pour diffuser en continu les SQLPutData qui ne se terminent pas dans des encodages de caractères partiels.  

## <a name="additional-notes"></a>Remarques supplémentaires  

1.  Vous pouvez effectuer une connexion administrateur dédiée (DAC) à l’aide de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] l’authentification et **hôte, port**. Un membre du rôle Sysadmin doit d’abord découvrir le port DAC. Consultez [connexion de Diagnostic pour les administrateurs de base de données](https://docs.microsoft.com/en-us/sql/database-engine/configure-windows/diagnostic-connection-for-database-administrators#dac-port) pour découvrir comment. Par exemple, si le port DAC était 33000, vous pouvez connecter à l’aide de `sqlcmd` comme suit :  

    ```
    sqlcmd –U <user> -P <pwd> -S <host>,33000
    ```

    > [!NOTE]  
    > Connexions DAC doivent utiliser [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] l’authentification.  
    
2.  Le Gestionnaire de pilotes UnixODBC retourne « Identificateur d’option/d’attribut non valide » pour tous les attributs d’instruction quand ils sont passés par le biais de SQLSetConnectAttr. Sous Windows, quand SQLSetConnectAttr reçoit une valeur d’attribut instruction, elle entraîne le pilote définir cette valeur sur toutes les instructions actives qui sont des enfants du handle de connexion.  

## <a name="see-also"></a>Voir aussi  
[Forum aux Questions](../../../connect/odbc/linux-mac/frequently-asked-questions-faq-for-odbc-linux.md)

[Problèmes connus dans cette version du pilote](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)

[Notes de publication](../../../connect/odbc/linux-mac/release-notes.md)

