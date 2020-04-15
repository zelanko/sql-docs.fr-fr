---
title: Mise à niveau d’un pilote 3.5 à un pilote 3.8 Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ffba36ac-d22e-40b9-911a-973fa9e10bd3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dcd01d050e806b733d75c54058945d367a33d6a7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294430"
---
# <a name="upgrading-a-35-driver-to-a-38-driver"></a>Mise à niveau d’un pilote 3.5 vers un pilote 3.8
Ce sujet fournit des lignes directrices et des considérations pour la mise à niveau d’un conducteur ODBC 3.5 à un conducteur ODBC 3.8.  
  
##### <a name="version-numbers"></a>Numéros de versions  
 Les lignes directrices suivantes se rapportent aux numéros de version :  
  
-   Un conducteur doit soutenir SQL_OV_ODBC3_80 pour SQL_ATTR_ODBC_VERSION, en retournant SQL_ERROR pour des valeurs autres que les SQL_OV_ODBC2, les SQL_OV_ODBC3 et les SQL_OV_ODBC3_80. Les versions futures du gestionnaire de conducteur supposeront qu’un conducteur prend en charge un niveau de conformité ODBC si le conducteur retourne SQL_SUCCESS de [SQLSetEnvAttr Fonction](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
-   Un pilote de version 3.8 devrait retourner 03.80 de **SQLGetInfo** quand SQL_DRIVER_ODBC_VER est passé à *InfoType*. Cependant, les gestionnaires de pilotes plus âgés, qui ont été inclus dans les anciennes versions de Microsoft Windows, traitera le pilote comme une version 3.5 pilote, et émettra un avertissement.  
  
     Dans Windows 7, la version Driver Manager est 03.80. Dans Windows 8, la version Driver Manager est 03.81 via le SQL_DM_VER SQLGetInfo (paramètre*InfoType).* SQL_ODBC_VER signale la version comme 03.80 dans Windows 7 et Windows 8.  
  
##### <a name="driver-specific-c-data-types"></a>Types de données C spécifiques au conducteur  
 Un pilote peut avoir des types de données C personnalisés lorsqu’il fonctionne avec une application ODBC version 3.8. (Pour plus d’informations, voir [C Data Types in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).) Cependant, il n’est pas nécessaire pour un conducteur de 3,8 de mettre en œuvre des types C spécifiques au conducteur. Mais le conducteur doit toujours effectuer la vérification de la plage des types C; le gestionnaire de conducteur ne le fera pas pour 3,8 conducteurs. Pour faciliter le développement du conducteur, la valeur du type de données C spécifique au conducteur peut être définie dans le format suivant :  
  
```  
SQL_DRIVER_C_TYPE_BASE+0, SQL_DRIVER_C_TYPE_BASE+1  
```  
  
##### <a name="driver-specific-data-types-descriptor-types-information-types-diagnostic-types-and-attributes"></a>Types de données spécifiques au conducteur, types descripteurs, types d’information, types de diagnostic et attributs  
 Lors du développement d’un nouveau pilote, vous devez utiliser la gamme spécifique au conducteur pour les types de données, les types descripteurs, les types d’information, les types de diagnostic et les attributs. Les plages spécifiques au conducteur et leurs valeurs de type de base sont discutées dans [les types de données spécifiques au conducteur, les types descripteurs, les types d’information, les types diagnostiques et les attributs.](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md)  
  
##### <a name="connection-pooling"></a>Regroupement de connexions  
 Pour une meilleure gestion de la mise en commun des connexions, ODBC 3.8 introduit l’attribut de connexion SQL_ATTR_RESET_CONNECTION dans **SQLSetConnectAttr**. SQL_RESET_CONNECTION_YES est la seule valeur valable pour cet attribut. SQL_ATTR_RESET_CONNECTION sera définie juste avant que le Driver Manager ne mette une connexion dans le pool de connexion, ce qui permettra au pilote de réinitialiser les autres attributs de connexion à leurs valeurs par défaut.  
  
 Pour éviter toute communication inutile avec le serveur, un pilote peut reporter la réinitialisation de l’attribut de connexion jusqu’à la prochaine communication avec le serveur distant, après que la connexion a été réutilisée à partir de la piscine.  
  
 Notez que SQL_ATTR_RESET_CONNECTION n’est utilisé que dans la communication entre le gestionnaire de conducteur et un conducteur. Une application ne peut pas définir cet attribut directement. Tous les pilotes de la version 3.8 doivent implémenter cet attribut de connexion.  
  
##### <a name="streamed-output-parameters"></a>Paramètres de sortie en streaming  
 La version 3.8 d’ODBC introduit des paramètres de sortie en streaming, un moyen plus évolutif de récupérer les paramètres de sortie. (Pour plus d’informations, voir [Paramètres de sortie de récupération à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).) Pour prendre en charge cette fonctionnalité, un pilote doit définir SQL_GD_OUTPUT_PARAMS dans la valeur de retour lorsque SQL_GETDATA_EXTENSIONS est *l’InfoType* dans un appel **SQLGetInfo.** La prise en charge d’un type SQL avec paramètres de sortie en continu doit être mise en œuvre dans le conducteur. Le gestionnaire de conducteur ne générera pas d’erreur pour un type SQL invalide. Les types SQL qui prennent en charge les paramètres de sortie en continu sont définis dans le conducteur.  
  
 Un conducteur doit retourner SQL_ERROR si l’application a utilisé **SQLGetData** pour récupérer un paramètre qui n’est pas le même que le paramètre retourné par **SQLParamData**.  
  
##### <a name="asynchronous-execution-for-connection-operations-polling-method"></a>Exécution asynchrone pour les opérations de connexion (méthode de sondage)  
 Un conducteur peut activer un support asynchrone pour diverses opérations de connexion.  
  
 À partir de Windows 7, ODBC prend en charge la méthode de vote (pour plus d’informations, voir [Asynchrone Execution (Méthode de sondage)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md). Il n’est pas nécessaire qu’un pilote de la version 3.8 ODBC implémente des opérations asynchrones sur les poignées de connexion. Même si un pilote ne met pas en œuvre des opérations asynchrones sur les poignées de connexion, le conducteur doit toujours mettre en œuvre le SQL_ASYNC_DBC_FUNCTIONS *InfoType* et retourner **SQL_ASYNC_DBC_NOT_CAPABLE**.  
  
 Lorsque des opérations de connexion asynchrone sont activées, le temps de fonctionnement d’une opération de connexion est le temps total de tous les appels répétés. Si le dernier appel répété a lieu après que le temps total a dépassé la valeur fixée par l’attribut de connexion SQL_ATTR_CONNECTION_TIMEOUT, et que l’opération n’est pas terminée, le conducteur retourne SQL_ERROR et enregistre un dossier de diagnostic avec SQLState HYT01 et le message « Délai de connexion expiré ». Il n’y a pas de délai si l’opération est terminée.  
  
##### <a name="sqlcancelhandle-function"></a>SQLCancelHandle, fonction  
 ODBC 3.8 prend en charge [SQLCancelHandle Function](../../../odbc/reference/syntax/sqlcancelhandle-function.md), qui est utilisé pour annuler à la fois les opérations de connexion et de déclaration. Un conducteur qui prend en charge **SQLCancelHandle** doit exporter la fonction. Un conducteur ne doit pas annuler la fonction de connexion synchrone ou asynchrone en cours si l’application appelle **SQLCancel** ou **SQLCancelHandle** sur une poignée de déclaration. De même, un conducteur ne doit pas annuler la fonction de déclaration synchrone ou asynchrone qui est en cours si une application appelle **SQLCancelHandle** sur la poignée de connexion. De plus, un conducteur ne devrait pas annuler l’opération de navigation **(SQLBrowseConnect** retourne SQL_NEED_DATA) si l’application appelle **SQLCancelHandle** sur la poignée de connexion. Dans ces cas, un conducteur doit retourner HY010, "erreur de séquence de fonction".  
  
 Il n’est pas nécessaire de soutenir à la fois **SQLCancelHandle** et les opérations de connexion asynchrones en même temps. Un conducteur peut supporter les opérations de connexion asynchrone, mais pas **SQLCancelHandle**, ou vice versa.  
  
##### <a name="suspended-connections"></a>Connexions suspendues  
 L’ODBC 3.8 Driver Manager peut mettre une connexion en état de suspension. Une application appellera **SQLDisconnect** pour libérer les ressources associées à la connexion. Dans ce cas, un conducteur doit essayer de libérer autant de ressources que possible sans vérifier l’état de la connexion. Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
##### <a name="driver-aware-connection-pooling"></a>Regroupement de connexions prenant en charge les pilotes  
 ODBC dans Windows 8 permet aux conducteurs de personnaliser le comportement de la piscine de connexion. Pour plus d’informations, voir [Driver-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
##### <a name="asynchronous-execution-notification-method"></a>Exécution asynchrone (méthode de notification)  
 ODBC 3.8 prend en charge la méthode de notification pour les opérations asynchrones, disponibles à partir de Windows 8. Pour plus d’informations, voir [Asynchrone Execution (Méthode de notification)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Développer un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Pilotes ODBC fournis par Microsoft](../../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)   
 [Nouveautés d’ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
