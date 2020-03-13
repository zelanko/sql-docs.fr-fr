---
title: Mise à niveau d’un pilote 3,5 vers un pilote 3,8 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ffba36ac-d22e-40b9-911a-973fa9e10bd3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 97b100b1ade97e1e88cf1421f09a7723412c8b76
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79289797"
---
# <a name="upgrading-a-35-driver-to-a-38-driver"></a>Mise à niveau d’un pilote 3.5 vers un pilote 3.8
Cette rubrique fournit des instructions et des considérations relatives à la mise à niveau d’un pilote ODBC 3,5 vers un pilote ODBC 3,8.  
  
##### <a name="version-numbers"></a>Numéros de versions  
 Les indications suivantes se rapportent aux numéros de version :  
  
-   Un pilote doit prendre en charge SQL_OV_ODBC3_80 pour SQL_ATTR_ODBC_VERSION, en retournant SQL_ERROR pour les valeurs autres que SQL_OV_ODBC2, SQL_OV_ODBC3 et SQL_OV_ODBC3_80. Les versions ultérieures du gestionnaire de pilotes supposent qu’un pilote prend en charge un niveau de compatibilité ODBC si le pilote retourne SQL_SUCCESS à partir de la [fonction SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
-   Un pilote version 3,8 doit retourner 03,80 à partir de **SQLGetInfo** quand SQL_DRIVER_ODBC_VER est passé à *infotype*. Toutefois, les anciens gestionnaires de pilotes, qui étaient inclus dans les versions antérieures de Microsoft Windows, traiteront le pilote comme un pilote de version 3,5 et produiront un avertissement.  
  
     Dans Windows 7, la version du gestionnaire de pilotes est 03,80. Dans Windows 8, la version du gestionnaire de pilotes est 03,81 via le SQL_DM_VER SQLGetInfo (paramètre*infotype* ). SQL_ODBC_VER signale la version de 03,80 dans Windows 7 et Windows 8.  
  
##### <a name="driver-specific-c-data-types"></a>Types de données C spécifiques au pilote  
 Un pilote peut avoir des types de données C personnalisés lorsqu’il fonctionne avec une application ODBC de version 3,8. (Pour plus d’informations, consultez [types de données C dans ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).) Toutefois, il n’est pas nécessaire qu’un pilote 3,8 implémente des types C spécifiques au pilote. Mais le pilote doit toujours effectuer la vérification de plage des types C ; le gestionnaire de pilotes ne le fera pas pour les pilotes 3,8. Pour faciliter le développement de pilotes, la valeur du type de données C spécifique au pilote peut être définie dans le format suivant :  
  
```  
SQL_DRIVER_C_TYPE_BASE+0, SQL_DRIVER_C_TYPE_BASE+1  
```  
  
##### <a name="driver-specific-data-types-descriptor-types-information-types-diagnostic-types-and-attributes"></a>Types de données spécifiques au pilote, types de descripteurs, types d’informations, types de diagnostics et attributs  
 Lorsque vous développez un nouveau pilote, vous devez utiliser la plage spécifique au pilote pour les types de données, les types de descripteurs, les types d’informations, les types de diagnostic et les attributs. Les plages spécifiques au pilote et leurs valeurs de type de base sont abordées dans les [types de données spécifiques au pilote, les types de descripteurs, les types d’informations, les types de diagnostic et les attributs](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
##### <a name="connection-pooling"></a>Regroupement de connexions  
 Pour une meilleure gestion du regroupement de connexions, ODBC 3,8 introduit l’attribut de connexion SQL_ATTR_RESET_CONNECTION dans **SQLSetConnectAttr**. SQL_RESET_CONNECTION_YES est la seule valeur valide pour cet attribut. SQL_ATTR_RESET_CONNECTION sera définie juste avant que le gestionnaire de pilotes ne mette une connexion dans le pool de connexions, ce qui permet au pilote de réinitialiser les autres attributs de connexion à leurs valeurs par défaut.  
  
 Pour éviter toute communication inutile avec le serveur, un pilote peut différer la réinitialisation de l’attribut de connexion jusqu’à la communication suivante avec le serveur distant, après que la connexion a été réutilisée à partir du pool.  
  
 Notez que SQL_ATTR_RESET_CONNECTION est utilisé uniquement pour la communication entre le gestionnaire de pilotes et un pilote. Une application ne peut pas définir cet attribut directement. Tous les pilotes de la version 3,8 doivent implémenter cet attribut de connexion.  
  
##### <a name="streamed-output-parameters"></a>Paramètres de sortie diffusés en continu  
 La version 3,8 de ODBC introduit les paramètres de sortie diffusés en continu, une méthode plus évolutive pour récupérer les paramètres de sortie. (Pour plus d’informations, consultez [récupération des paramètres de sortie à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).) Pour prendre en charge cette fonctionnalité, un pilote doit définir SQL_GD_OUTPUT_PARAMS dans la valeur de retour lorsque SQL_GETDATA_EXTENSIONS est l' *infotype* dans un appel **SQLGetInfo** . La prise en charge d’un type SQL avec des paramètres de sortie diffusés en continu doit être implémentée dans le pilote. Le gestionnaire de pilotes ne génère pas d’erreur pour un type SQL non valide. Les types SQL qui prennent en charge les paramètres de sortie en diffusion en continu sont définis dans le pilote.  
  
 Un pilote doit retourner SQL_ERROR si l’application a utilisé **SQLGetData** pour récupérer un paramètre qui n’est pas le même que le paramètre retourné par **SQLParamData**.  
  
##### <a name="asynchronous-execution-for-connection-operations-polling-method"></a>Exécution asynchrone pour les opérations de connexion (méthode d’interrogation)  
 Un pilote peut activer la prise en charge asynchrone de diverses opérations de connexion.  
  
 À compter de Windows 7, ODBC prend en charge la méthode d’interrogation (pour plus d’informations, consultez [exécution asynchrone (méthode d’interrogation)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md). Il n’est pas nécessaire pour un pilote ODBC de version 3,8 d’implémenter des opérations asynchrones sur des handles de connexion. Même si un pilote n’implémente pas d’opérations asynchrones sur des handles de connexion, le pilote doit toujours implémenter l' *InfoType* SQL_ASYNC_DBC_FUNCTIONS et retourner **SQL_ASYNC_DBC_NOT_CAPABLE**.  
  
 Lorsque les opérations de connexion asynchrones sont activées, le temps d’exécution d’une opération de connexion correspond à la durée totale de tous les appels répétés. Si le dernier appel répété se produit après que le temps total a dépassé la valeur définie par l’attribut de connexion SQL_ATTR_CONNECTION_TIMEOUT, et que l’opération n’est pas terminée, le pilote retourne SQL_ERROR et enregistre un enregistrement de diagnostic avec SQLState HYT01 et le message « expiration de la connexion ». Il n’y a pas de délai d’expiration si l’opération est terminée.  
  
##### <a name="sqlcancelhandle-function"></a>SQLCancelHandle, fonction  
 ODBC 3,8 prend en charge la [fonction SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md), qui est utilisée pour annuler les opérations de connexion et d’instruction. Un pilote qui prend en charge **SQLCancelHandle** doit exporter la fonction. Un pilote ne doit pas annuler une fonction de connexion synchrone ou asynchrone en cours si l’application appelle **SQLCancel** ou **SQLCancelHandle** sur un descripteur d’instruction. De même, un pilote ne doit pas annuler une fonction d’instruction synchrone ou asynchrone en cours si une application appelle **SQLCancelHandle** sur le handle de connexion. En outre, un pilote ne doit pas annuler l’opération de navigation (**SQLBrowseConnect** retourne SQL_NEED_DATA) si l’application appelle **SQLCancelHandle** sur le handle de connexion. Dans ce cas, un pilote doit retourner HY010, « erreur de séquence de fonction ».  
  
 Il n’est pas nécessaire de prendre en charge à la fois les opérations de connexion **SQLCancelHandle** et asynchrones. Un pilote peut prendre en charge des opérations de connexion asynchrones, mais pas **SQLCancelHandle**, ou vice versa.  
  
##### <a name="suspended-connections"></a>Connexions suspendues  
 Le gestionnaire de pilotes ODBC 3,8 peut mettre une connexion en état suspendu. Une application appellera **SQLDisconnect** pour libérer les ressources associées à la connexion. Dans ce cas, un pilote doit tenter de libérer autant de ressources que possible sans vérifier l’état de la connexion. Pour plus d’informations sur l’état suspendu, consultez [fonction SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
##### <a name="driver-aware-connection-pooling"></a>Regroupement de connexions prenant en charge les pilotes  
 ODBC dans Windows 8 permet aux pilotes de personnaliser le comportement du pool de connexions. Pour plus d’informations, consultez [regroupement de connexions prenant en charge les pilotes](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
##### <a name="asynchronous-execution-notification-method"></a>Exécution asynchrone (méthode de notification)  
 ODBC 3,8 prend en charge la méthode de notification pour les opérations asynchrones, disponible à partir de Windows 8. Pour plus d’informations, consultez [exécution asynchrone (méthode de notification)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Pilotes ODBC fournis par Microsoft](../../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)   
 [Nouveautés d’ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
