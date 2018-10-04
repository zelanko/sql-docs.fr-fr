---
title: La mise à niveau d’un pilote 3.5 vers un pilote 3.8 | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: df2fa8df9af317bd76b2d7f10e50f7cc937e4660
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47731037"
---
# <a name="upgrading-a-35-driver-to-a-38-driver"></a>Mise à niveau d’un pilote 3.5 vers un pilote 3.8
Cette rubrique fournit des instructions et des considérations relatives à la mise à niveau d’un pilote ODBC 3.5 à un pilote ODBC 3.8.  
  
##### <a name="version-numbers"></a>Numéros de versions  
 Les instructions suivantes se rapportent aux numéros de version :  
  
-   Un pilote doit prendre en charge SQL_OV_ODBC3_80 pour SQL_ATTR_ODBC_VERSION, retour SQL_ERROR pour les valeurs autres que SQL_OV_ODBC2, SQL_OV_ODBC3 et SQL_OV_ODBC3_80. Les versions futures du Gestionnaire de pilotes partirons du principe qu’un pilote prend en charge un niveau de conformité ODBC si le pilote retourne SQL_SUCCESS à partir de [SQLSetEnvAttr, fonction](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
-   Un pilote de la version 3.8 doit retourner 03.80 de **SQLGetInfo** lorsque SQL_DRIVER_ODBC_VER est transmise à *InfoType*. Toutefois, les gestionnaires de pilotes plus anciens, qui ont été inclus dans les versions antérieures de Microsoft Windows, traiter le pilote comme un pilote de la version 3.5 et émet un avertissement.  
  
     Dans Windows 7, la version du Gestionnaire de pilotes est 03.80. Dans Windows 8, la version du Gestionnaire de pilotes est 03.81 via la SQL_DM_VER SQLGetInfo (*InfoType* paramètre). SQL_ODBC_VER indique la version en tant que 03.80 dans Windows 7 et Windows 8.  
  
##### <a name="driver-specific-c-data-types"></a>Types de données spécifiques au pilote C  
 Un pilote peut avoir personnalisé les types de données C quand il fonctionne avec une application de ODBC version 3.8. (Pour plus d’informations, consultez [des Types de données C dans ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).) Toutefois, il n’est pas obligatoire pour un pilote 3.8 implémenter tous les types C spécifiques au pilote. Mais le pilote doit toujours effectuer la vérification de plage de types C ; le Gestionnaire de pilotes n’effectue que des 3,8 pilotes. Pour faciliter le développement de pilotes, la valeur du type de données C spécifique, pilote peut être définie dans le format suivant :  
  
```  
SQL_DRIVER_C_TYPE_BASE+0, SQL_DRIVER_C_TYPE_BASE+1  
```  
  
##### <a name="driver-specific-data-types-descriptor-types-information-types-diagnostic-types-and-attributes"></a>Types de données spécifique au pilote, Types de descripteurs, Types d’informations, Types de diagnostics et attributs  
 Lorsque vous développez un nouveau pilote, vous devez utiliser la plage spécifiques au pilote pour les types de données, types de descripteurs, types d’informations, types de diagnostics et attributs. Les plages spécifiques au pilote et leurs valeurs de type de base sont décrits dans [les Types de données spécifiques au pilote, Types de descripteurs, Types d’informations, Types de diagnostics et attributs](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
##### <a name="connection-pooling"></a>Regroupement de connexions  
 Pour une meilleure gestion du regroupement de connexions, ODBC 3.8 introduit l’attribut de connexion SQL_ATTR_RESET_CONNECTION dans **SQLSetConnectAttr**. SQL_RESET_CONNECTION_YES est la seule valeur valide pour cet attribut. SQL_ATTR_RESET_CONNECTION est définie juste avant que le Gestionnaire de pilotes place une connexion dans le pool de connexions, permettre au pilote réinitialiser les autres attributs de connexion à leurs valeurs par défaut.  
  
 Pour éviter les communications inutiles avec le serveur, un pilote peut différer de l’attribut de connexion réinitialisée jusqu'à la prochaine communication avec le serveur distant, une fois la connexion est réutilisée à partir du pool.  
  
 Notez que SQL_ATTR_RESET_CONNECTION est uniquement utilisé dans la communication entre le Gestionnaire de pilotes et d’un pilote. Une application ne peut pas définir cet attribut directement. Tous les pilotes de la version 3.8 doivent implémenter cet attribut de connexion.  
  
##### <a name="streamed-output-parameters"></a>Paramètres de sortie diffusées en continu  
 ODBC version 3.8 introduit des paramètres de sortie diffusées en continu, un moyen plus évolutif pour récupérer les paramètres de sortie. (Pour plus d’informations, consultez [récupération des paramètres de sortie à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).) Pour prendre en charge cette fonctionnalité, un pilote doit définir SQL_GD_OUTPUT_PARAMS dans la valeur de retour lorsque SQL_GETDATA_EXTENSIONS est la *InfoType* dans un **SQLGetInfo** appeler. Prise en charge pour un type SQL avec des paramètres de sortie diffusées en continu doit être implémentée dans le pilote. Le Gestionnaire de pilotes ne génère pas d’une erreur pour un type SQL non valide. Les types SQL qui prennent en charge les paramètres de sortie diffusées en continu est défini dans le pilote.  
  
 Un pilote doit retourner SQL_ERROR si l’application utilisée **SQLGetData** pour récupérer un paramètre qui n’est pas le même que le paramètre retourné par **SQLParamData**.  
  
##### <a name="asynchronous-execution-for-connection-operations-polling-method"></a>Exécution asynchrone pour les opérations de connexion (méthode d’interrogation)  
 Un pilote peut activer la prise en charge asynchrone pour diverses opérations de connexion.  
  
 À compter de Windows 7, ODBC prend en charge la méthode d’interrogation (pour plus d’informations, consultez [exécution asynchrone (méthode d’interrogation)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md). Il n’existe aucune configuration requise pour un version 3.8 du pilote ODBC implémenter des opérations asynchrones sur les handles de connexion. Même si un pilote n’implémente pas les opérations asynchrones sur les handles de connexion, le pilote doit toujours implémenter la SQL_ASYNC_DBC_FUNCTIONS *InfoType* et retourner **SQL_ASYNC_DBC_NOT_CAPABLE**.  
  
 Lorsque les opérations de connexion asynchrone sont activées, le temps d’exécution d’une opération de connexion est la durée totale de tous les appels répétés. Si le dernier répété appel se produit une fois que la durée totale a dépassé la valeur définie par l’attribut de connexion SQL_ATTR_CONNECTION_TIMEOUT et l’opération n’a pas terminé, le pilote retourne SQL_ERROR et consigne un enregistrement de diagnostic avec SQLState HYT01 et le message « délai de connexion expiré ». Il n’existe aucun délai d’expiration si l’opération terminée.  
  
##### <a name="sqlcancelhandle-function"></a>SQLCancelHandle, fonction  
 Prend en charge par ODBC 3.8 [sqlcancelhandle, fonction](../../../odbc/reference/syntax/sqlcancelhandle-function.md), qui est utilisé pour annuler les opérations de connexion et d’instruction. Un pilote qui prend en charge **SQLCancelHandle** devez exporter la fonction. Un pilote ne doit pas annuler n’importe quelle fonction de connexion synchrone ou asynchrone est en cours si l’application appelle **SQLCancel** ou **SQLCancelHandle** sur un descripteur d’instruction. De même, un pilote ne doit pas annuler n’importe quelle fonction d’instruction synchrone ou asynchrone est en cours d’exécution si une application appelle **SQLCancelHandle** sur le handle de connexion. En outre, un pilote ne doit pas annuler l’opération de navigation (**SQLBrowseConnect** retourne SQL_NEED_DATA) si l’application appelle **SQLCancelHandle** sur le handle de connexion. Dans ce cas, un pilote doit retourner HY010, « erreur de séquence de fonction ».  
  
 Il n’est pas nécessaire prendre en charge les deux **SQLCancelHandle** et les opérations de connexion asynchrone en même temps. Un pilote peut prendre en charge les opérations de connexion asynchrone, mais pas **SQLCancelHandle**, ou vice versa.  
  
##### <a name="suspended-connections"></a>Connexions suspendues  
 Le Gestionnaire de pilote de ODBC 3.8 peut mettre une connexion en état suspendu. Une application appellera **SQLDisconnect** pour libérer les ressources associées à la connexion. Dans ce cas, un pilote doit tenter de libérer des ressources autant que possible sans vérifier l’état de la connexion. Pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
##### <a name="driver-aware-connection-pooling"></a>Regroupement de connexions prenant en charge les pilotes  
 ODBC dans Windows 8 permet aux pilotes personnaliser le comportement de pool de connexion. Pour plus d’informations, consultez [Driver-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
##### <a name="asynchronous-execution-notification-method"></a>Exécution asynchrone (méthode de notification)  
 ODBC 3.8 prend en charge la méthode de notification pour les opérations asynchrones, disponibles à partir de Windows 8. Pour plus d’informations, consultez [exécution asynchrone (méthode de Notification)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Pilotes ODBC fournis par Microsoft](../../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)   
 [Nouveautés d’ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
