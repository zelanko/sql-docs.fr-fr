---
title: Instructions de programmation (pilote ODBC pour SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 01/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9a8fa77ed1819d22eb90ea4fb0a7308122f708e1
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52522954"
---
# <a name="programming-guidelines"></a>Instructions de programmation

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Les fonctionnalités de programmation de [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur macOS et Linux reposent sur ODBC dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ([SQL Server Native Client (ODBC)](https://go.microsoft.com/fwlink/?LinkID=134151)). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client se base sur ODBC dans Windows Data Access Components ([Guide de référence du programmeur ODBC](https://go.microsoft.com/fwlink/?LinkID=45250)).  

Une application ODBC peut utiliser Multiple Active Result Sets (MARS) et autres [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] des fonctionnalités spécifiques en incluant `/usr/local/include/msodbcsql.h` après avoir inclus les en-têtes unixODBC (`sql.h`, `sqlext.h`, `sqltypes.h`, et `sqlucode.h`). Utilisez alors les mêmes noms symboliques pour les éléments spécifiques à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que dans vos applications ODBC Windows.

## <a name="available-features"></a>Fonctionnalités disponibles  
Les sections suivantes de la documentation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client pour ODBC ([SQL Server Native Client (ODBC)](https://go.microsoft.com/fwlink/?LinkID=134151)) sont valides quand vous utilisez le pilote ODBC sur macOS et Linux :  

-   [Communication avec SQL Server (ODBC)](https://msdn.microsoft.com/library/ms131692.aspx)  
-   [Prise en charge des connexions et délais de requête](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
-   [Curseurs](../../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
-   [Améliorations des types de données date et heure (ODBC)](https://msdn.microsoft.com/library/bb677319.aspx)  
-   [Exécution de requêtes (ODBC)](https://msdn.microsoft.com/library/ms131677.aspx)  
-   [Gestion des erreurs et des messages](../../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
-   [Authentification Kerberos](../../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md)  
-   [Types CLR volumineux définis par l’utilisateur (ODBC)](https://msdn.microsoft.com/library/bb677316.aspx)  
-   [Exécution de transactions (ODBC) (à l’exception des transactions distribuées)](https://msdn.microsoft.com/library/ms131706.aspx)  
-   [Traitement des résultats (ODBC)](https://msdn.microsoft.com/library/ms130812.aspx)  
-   [Exécution de procédures stockées](../../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)
-   [Prise en charge des colonnes éparses (ODBC)](https://msdn.microsoft.com/library/cc280357.aspx)
-   [Chiffrement SSL](../../../relational-databases/native-client/features/using-encryption-without-validation.md)
-   [Paramètres table](https://docs.microsoft.com/sql/relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc)
-   [API de commandes et données UTF-8 et UTF-16](https://msdn.microsoft.com/library/ff878241.aspx)
-   [Utilisation des fonctions de catalogue](../../../relational-databases/native-client/odbc/using-catalog-functions.md)  

## <a name="unsupported-features"></a>Fonctions non prises en charge

Les fonctionnalités suivantes n’ont pas été vérifiées pour fonctionner correctement dans cette version du pilote ODBC sur macOS et Linux :

-   Connexion de Cluster de basculement
-   [Résolution d’adresses IP réseau transparent](https://docs.microsoft.com/sql/connect/odbc/linux/using-transparent-network-ip-resolution) (avant le pilote ODBC 17)
-   [Suivi de pilote avancées](https://blogs.msdn.microsoft.com/mattn/2012/05/15/enabling-advanced-driver-tracing-for-the-sql-native-client-odbc-drivers/)

Les fonctionnalités suivantes ne sont pas disponibles dans cette version du pilote ODBC sur macOS et Linux : 

-   Transactions distribuées (attribut SQL_ATTR_ENLIST_IN_DTC non pris en charge)  
-   Mise en miroir de bases de données  
-   FILESTREAM  
-   Profilage des performances du pilote ODBC, décrit dans [SQLSetConnectAttr](https://go.microsoft.com/fwlink/?LinkId=234099) et attributs de connexion liés aux performances suivants :  
    -   SQL_COPT_SS_PERF_DATA  
    -   SQL_COPT_SS_PERF_DATA_LOG  
    -   SQL_COPT_SS_PERF_DATA_LOG_NOW  
    -   SQL_COPT_SS_PERF_QUERY  
    -   SQL_COPT_SS_PERF_QUERY_INTERVAL  
    -   SQL_COPT_SS_PERF_QUERY_LOG  
-   SQLBrowseConnect  
-   Types d’intervalle C comme SQL_C_INTERVAL_YEAR_TO_MONTH (décrits dans [Identificateurs et descripteurs des types de données](https://msdn.microsoft.com/library/ms716351(VS.85).aspx))
-   Valeur SQL_CUR_USE_ODBC de l’attribut SQL_ATTR_ODBC_CURSORS de la fonction SQLSetConnectAttr.

## <a name="character-set-support"></a>Prise en charge du jeu de caractères

Pour ODBC Driver 13 et 13.1, les données SQLCHAR doivent être UTF-8. Aucun autres encodages ne sont pris en charge.

17 du pilote ODBC, les données SQLCHAR dans un des jeux de caractères suivants/encodages sont pris en charge :

|Nom   |Description|
|-|-|
|UTF-8|Unicode|
|CP437|MS-DOS Latin des États-Unis|
|CP850|MS-DOS Latin 1|
|CP874|Latin/thaï|
|CP932|Japonais, Shift-JIS|
|CP936|Chinois simplifié, GBK|
|CP949|Coréen, EUC-KR|
|CP950|Chinois traditionnel, Big5|
|CP1251|Cyrillique|
|CP1253|Greek|
|CP1256|Arabe|
|CP1257|Balte|
|CP1258|Vietnamien|
|ISO-8859-1 / CP1252|Latin-1|
|ISO-8859-2 / CP1250|Latin-2|
|ISO-8859-3|Latin-3|
|ISO-8859-4|Latin-4|
|ISO-8859-5|Latin/cyrillique|
|ISO-8859-6|Latin/arabe|
|ISO-8859-7|Latin/grec|
|ISO-8859-8 / CP1255|Hébreu|
|ISO-8859-9 / CP1254|Turc|
|ISO-8859-13|Latin-7|
|ISO-8859-15|Latin-9|

Lors de la connexion, le pilote détecte les paramètres régionaux actuels du processus, dans qu'il est chargé. Si elle utilise un des encodages ci-dessus, le pilote utilise cet encodage pour les données SQLCHAR (caractère étroits) ; Sinon, il est par défaut UTF-8. Dans la mesure où tous les processus Démarrer dans les paramètres régionaux « C » par défaut (et donc que le conducteur par défaut au format UTF-8), si une application doit utiliser un des encodages ci-dessus, il doit utiliser le **setlocale** fonction permettant de définir les paramètres régionaux de façon appropriée avant connexion ; en spécifiant les paramètres régionaux souhaités explicitement, ou à l’aide d’une chaîne vide par exemple `setlocale(LC_ALL, "")` à utiliser les paramètres régionaux de l’environnement.

Par conséquent, dans un Linux ou Mac environnement standard où l’encodage est UTF-8, les utilisateurs de la mise à niveau de version 17 du pilote ODBC à partir de 13 ou 13.1 observera pas toutes les différences. Toutefois, les applications qui utilisent un codage non-UTF-8 dans la liste ci-dessus par le biais de `setlocale()` devez utiliser cet encodage de données vers/depuis le pilote au lieu d’UTF-8.

Les données SQLWCHAR doivent être au format UTF-16LE (Little Endian).

Lors de la liaison des paramètres d’entrée avec SQLBindParameter, si un caractère étroit SQL type tel que SQL_VARCHAR est spécifié, le pilote convertit les données fournies à partir du client d’encodage à la valeur par défaut (en général, page de codes 1252) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encodage. Pour les paramètres de sortie, le pilote convertit à partir de l’encodage spécifié dans les informations de classement associées aux données au client d’encodage. Toutefois, une perte de données est possible---convertit des caractères dans l’encodage de la source n’est pas représentables dans l’encodage cible à un point d’interrogation (« ? »).

Pour éviter cette perte de données lors de la liaison des paramètres d’entrée, spécifiez un type de caractère SQL Unicode comme SQL_NVARCHAR. Dans ce cas, le pilote convertit à partir du client d’encodage UTF-16, ce qui peut représenter tous les caractères Unicode. En outre, la colonne cible ou du paramètre sur le serveur doit également être un type Unicode (**nchar**, **nvarchar**, **ntext**) ou l’autre avec un classement/encodage, qui peut représenter tous les caractères des données sources d’origine. Pour éviter la perte de données avec les paramètres de sortie, spécifiez un type SQL d’Unicode et soit un Unicode C type (SQL_C_WCHAR), et que le pilote retourner des données au format UTF-16 ; ou un C étroit tapez et vous assurer que le client de codage peut représenter tous les caractères des données source (il est toujours possible avec UTF-8.)

Pour plus d’informations sur les classements et les codages, voir [Prise en charge d’Unicode et des classements](../../../relational-databases/collations/collation-and-unicode-support.md).

Il existe certaines différences de conversion encodage entre Windows et de plusieurs versions de la bibliothèque iconv sur Linux et macOS. Données de texte dans la page de codes 1255 (hébreu) ont un seul point de code (0xCA) qui se comporte différemment lors de la conversion au format Unicode. Sur Windows, ce caractère convertit le point de code UTF-16 de 0x05BA. Sur macOS et Linux avec libiconv les versions antérieures à 1.15, il convertit en 0x00CA. Sur Linux avec les bibliothèques iconv ne prenant pas en charge la version 2003 de Big5/CP950 (nommé `BIG5-2003`), les caractères ajoutés à cette révision ne convertira pas correctement. Dans la page de codes 932 (japonais, Shift-JIS), le résultat du décodage de caractères pas initialement définis dans la norme de codage est également différente. Par exemple, l’octet 0 x 80 convertit à U + 0080 sur Windows, mais peut devenir 30FB U + sur Linux et macOS, en fonction de la version d’iconv.

Dans ODBC Driver 13 et 13.1, quand des caractères multioctets UTF-8 ou des substituts UTF-16 sont répartis entre les mémoires tampons SQLPutData, les données sont altérées. Utilisez des mémoires tampons pour diffuser en continu les SQLPutData qui ne se terminent pas dans des encodages de caractères partiels. Cette limitation a été supprimée avec la version 17 du pilote ODBC.

## <a name="additional-notes"></a>Remarques supplémentaires  

1.  Vous pouvez établir une connexion administrateur dédiée (DAC) à l’aide de l’authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et de **port,hôte**. Un membre du rôle Sysadmin doit d’abord découvrir le port DAC. Consultez [connexion de Diagnostic pour les administrateurs de base de données](https://docs.microsoft.com/sql/database-engine/configure-windows/diagnostic-connection-for-database-administrators#dac-port) pour découvrir comment. Par exemple, si le port DAC était 33000, vous pourriez vous y connecter avec `sqlcmd` comme suit :  

    ```
    sqlcmd -U <user> -P <pwd> -S <host>,33000
    ```

    > [!NOTE]  
    > Les connexions DAC doivent utiliser l’authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
    
2.  Le Gestionnaire de pilotes UnixODBC retourne « Identificateur d’option/d’attribut non valide » pour tous les attributs d’instruction quand ils sont passés par le biais de SQLSetConnectAttr. Sur Windows, quand SQLSetConnectAttr reçoit une valeur d’attribut d’instruction, le pilote est amené à définir cette valeur sur toutes les instructions actives qui sont des enfants du handle de connexion.  

## <a name="see-also"></a> Voir aussi  
[Questions fréquentes (FAQ)](../../../connect/odbc/linux-mac/frequently-asked-questions-faq-for-odbc-linux.md)

[Problèmes connus dans cette version du pilote](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)

[Notes de publication](../../../connect/odbc/linux-mac/release-notes.md)
