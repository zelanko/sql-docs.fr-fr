---
title: Instructions de programmation (ODBC Driver for SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 01/12/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 591c0cc47a4f807172cbfd24b91f465144faae09
ms.sourcegitcommit: 3cfedfeba377560d460ca3e42af1e18824988c07
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59042368"
---
# <a name="programming-guidelines"></a>Instructions de programmation

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Les fonctionnalités de programmation de [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur macOS et Linux reposent sur ODBC dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ([SQL Server Native Client (ODBC)](https://go.microsoft.com/fwlink/?LinkID=134151)). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client se base sur ODBC dans Windows Data Access Components ([Référence du programmeur ODBC](https://go.microsoft.com/fwlink/?LinkID=45250)).  

Une application ODBC peut utiliser MARS (Multiple Active Result Sets) et d’autres fonctionnalités spécifiques [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en incluant `/usr/local/include/msodbcsql.h` après avoir inclus les en-têtes unixODBC (`sql.h`, `sqlext.h`, `sqltypes.h` et `sqlucode.h`). Utilisez alors les mêmes noms symboliques pour les éléments spécifiques à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que dans vos applications ODBC Windows.

## <a name="available-features"></a>Fonctionnalités disponibles  
Les sections suivantes de la documentation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client pour ODBC ([SQL Server Native Client (ODBC)](https://go.microsoft.com/fwlink/?LinkID=134151)) sont valides quand vous utilisez le pilote ODBC sur macOS et Linux :  

-   [Communication avec SQL Server (ODBC)](https://msdn.microsoft.com/library/ms131692.aspx)  
-   [Prise en charge des connexions et délais de requête](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
-   [Curseurs](../../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
-   [Améliorations de la date et de l’heure (ODBC)](https://msdn.microsoft.com/library/bb677319.aspx)  
-   [Exécution de requêtes (ODBC)](https://msdn.microsoft.com/library/ms131677.aspx)  
-   [Gestion des erreurs et des messages](../../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
-   [Authentification Kerberos](../../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md)  
-   [Types CLR volumineux définis par l’utilisateur (ODBC)](https://msdn.microsoft.com/library/bb677316.aspx)  
-   [Exécution de transactions (ODBC) (à l’exception des transactions distribuées)](https://msdn.microsoft.com/library/ms131706.aspx)  
-   [Traitement des résultats (ODBC)](https://msdn.microsoft.com/library/ms130812.aspx)  
-   [Exécution des procédures stockées](../../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)
-   [Prise en charge des colonnes éparses (ODBC)](https://msdn.microsoft.com/library/cc280357.aspx)
-   [Chiffrement SSL](../../../relational-databases/native-client/features/using-encryption-without-validation.md)
-   [Paramètres table](https://docs.microsoft.com/sql/relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc)
-   [API de commandes et données UTF-8 et UTF-16](https://msdn.microsoft.com/library/ff878241.aspx)
-   [Utilisation des fonctions de catalogue](../../../relational-databases/native-client/odbc/using-catalog-functions.md)  

## <a name="unsupported-features"></a>Fonctions non prises en charge

Le fonctionnement correct des fonctionnalités suivantes dans cette version du pilote ODBC sur macOS et Linux n’a pas été vérifié :

-   Connexion de cluster de basculement
-   [Résolution d’adresses IP réseau transparente](https://docs.microsoft.com/sql/connect/odbc/linux/using-transparent-network-ip-resolution) (avant ODBC Driver 17)
-   [Suivi de pilote avancé](https://blogs.msdn.microsoft.com/mattn/2012/05/15/enabling-advanced-driver-tracing-for-the-sql-native-client-odbc-drivers/)

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

Pour ODBC Driver 13 et 13.1, les données SQLCHAR doivent être au format UTF-8. Aucun autre encodage n’est pris en charge.

Pour ODBC Driver 17, les données SQLCHAR dans un des jeux de caractères/encodages suivants sont prises en charge :

|Créer une vue d’abonnement|Description|
|-|-|
|UTF-8|Unicode|
|CP437|MS-DOS Latin US|
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

Au moment de la connexion, le pilote détecte les paramètres régionaux actuels du processus dans lequel il est chargé. S’il utilise un des encodages ci-dessus, le pilote s’en sert pour les données SQLCHAR (caractères étroits) ; sinon, il utilise par défaut l’encodage UTF-8. Dans la mesure où tous les processus démarrent dans les paramètres régionaux « C » par défaut (amenant le pilote à utiliser par défaut le format UTF-8), si une application doit utiliser un des encodages ci-dessus, elle doit recourir à la fonction **setlocale** pour définir les paramètres régionaux de façon appropriée avant la connexion, soit en spécifiant les paramètres régionaux souhaités explicitement, soit en utilisant une chaîne vide, par exemple `setlocale(LC_ALL, "")`, pour utiliser les paramètres régionaux de l’environnement.

Ainsi, dans un environnement Linux ou Mac standard où l’encodage est UTF-8, les utilisateurs d’ODBC Driver 17 qui effectuent une mise à niveau à partir de la version 13 ou 13.1 ne constatent aucune différence. Toutefois, les applications qui utilisent un codage non-UTF-8 dans la liste ci-dessus par le biais de `setlocale()` doivent recourir à cet encodage pour les données vers et depuis le pilote au lieu d’UTF-8.

Les données SQLWCHAR doivent être au format UTF-16LE (Little Endian).

Au moment de la liaison des paramètres d’entrée avec SQLBindParameter, si un type SQL à caractères étroits tel que SQL_VARCHAR est spécifié, le pilote convertit les données fournies depuis l’encodage client vers l’encodage [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] par défaut (en général, la page de codes 1252). Pour les paramètres de sortie, le pilote effectue une conversion depuis l’encodage spécifié dans les informations de classement associées aux données vers l’encodage client. Toutefois, une perte de données est possible : les caractères dans l’encodage source qui ne sont pas représentables dans l’encodage cible sont convertis en point d’interrogation (« ? »).

Pour éviter cette perte de données au moment de la liaison des paramètres d’entrée, spécifiez un type de caractère SQL Unicode, comme SQL_NVARCHAR. Dans ce cas, le pilote effectue une conversion depuis l’encodage client vers le format UTF-16, qui peut représenter tous les caractères Unicode. En outre, la colonne ou paramètre cible sur le serveur doit également être un type Unicode (**nchar**, **nvarchar**, **ntext**) ou doté d’un classement/encodage pouvant représenter tous les caractères des données sources d’origine. Pour éviter la perte de données avec les paramètres de sortie, spécifiez un type SQL Unicode et soit un type C Unicode (SQL_C_WCHAR), afin que le pilote retourne les données au format UTF-16, soit un type C à caractères étroits, et assurez-vous que l’encodage client peut représenter tous les caractères des données sources (ce qui est toujours possible avec le format UTF-8.)

Pour plus d’informations sur les classements et les codages, voir [Prise en charge d’Unicode et des classements](../../../relational-databases/collations/collation-and-unicode-support.md).

Il existe certaines différences de conversion d’encodage entre Windows et plusieurs versions de la bibliothèque iconv sur Linux et macOS. Les données texte dans la page de codes 1255 (hébreu) ont un seul point de code (0xCA) qui se comporte différemment au moment de la conversion en Unicode. Sur Windows, ce caractère est converti dans le point de code UTF-16 0x05BA. Sur macOS et Linux avec versions de libiconv antérieures à 1.15, il est converti dans le point de code 0x00CA. Sur Linux avec les bibliothèques iconv qui ne prennent pas en charge la révision 2003 de Big5/CP950 (nommée `BIG5-2003`), les caractères ajoutés à cette révision ne sont pas convertis correctement. Dans la page de codes 932 (japonais, Shift-JIS), le résultat du décodage de caractères qui ne sont pas initialement définis dans le standard d’encodage est également différent. Par exemple, l’octet 0x80 est converti en U+0080 sur Windows, mais peut devenir U+30FB sur Linux et macOS, suivant la version d’iconv.

Dans ODBC Driver 13 et 13.1, quand des caractères multioctets UTF-8 ou des substituts UTF-16 sont répartis entre les mémoires tampons SQLPutData, les données sont altérées. Utilisez des mémoires tampons pour diffuser en continu les SQLPutData qui ne se terminent pas dans des encodages de caractères partiels. Cette restriction a été supprimée avec ODBC Driver 17.

## <a name="additional-notes"></a>Remarques supplémentaires  

1.  Vous pouvez établir une connexion administrateur dédiée (DAC) à l’aide de l’authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et de **port,hôte**. Un membre du rôle Sysadmin doit d’abord découvrir le port DAC. Consultez [Connexion de diagnostic pour les administrateurs de base de données](https://docs.microsoft.com/sql/database-engine/configure-windows/diagnostic-connection-for-database-administrators#dac-port) pour découvrir la procédure à suivre. Par exemple, si le port DAC était 33000, vous pourriez vous y connecter avec `sqlcmd` comme suit :  

    ```
    sqlcmd -U <user> -P <pwd> -S <host>,33000
    ```

    > [!NOTE]  
    > Les connexions DAC doivent utiliser l’authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
    
2.  Le Gestionnaire de pilotes UnixODBC retourne « Identificateur d’option/d’attribut non valide » pour tous les attributs d’instruction quand ils sont passés par le biais de SQLSetConnectAttr. Sur Windows, quand SQLSetConnectAttr reçoit une valeur d’attribut d’instruction, le pilote est amené à définir cette valeur sur toutes les instructions actives qui sont des enfants du handle de connexion.  

## <a name="see-also"></a> Voir aussi  
[Forum Aux Questions (FAQ)](../../../connect/odbc/linux-mac/frequently-asked-questions-faq-for-odbc-linux.md)

[Problèmes connus dans cette version du pilote](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)

[Notes de publication](../../../connect/odbc/linux-mac/release-notes-odbc-sql-server-linux-mac.md)
