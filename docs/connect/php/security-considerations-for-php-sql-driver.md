---
title: "Considérations de sécurité pour le pilote SQL PHP | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security considerations
ms.assetid: a8c1a570-9204-454f-b94c-ba34f54d487c
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2a7423bcfcfd28073840ad7f8c9ee2e7424507bc
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="security-considerations-for-php-sql-driver"></a>Considérations sur la sécurité à prendre en compte pour le pilote SQL Server pour PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette rubrique décrit les considérations de sécurité propres au développement, au déploiement et à l’exécution d’applications qui utilisent le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Pour plus d’informations sur la sécurité de SQL Server, consultez [Sécurité et conformité des données](http://go.microsoft.com/fwlink/?LinkId=129225).  
  
## <a name="connect-using-windows-authentication"></a>Se connecter avec l’authentification Windows  
Vous devez utiliser l’authentification Windows pour la connexion à SQL Server dans la mesure du possible pour les raisons suivantes :  
  
-   **Aucune information d’identification n’est transmise sur le réseau pendant l’authentification.** Les noms d’utilisateur et les mots de passe ne sont pas incorporés dans la chaîne de connexion de base de données. Cela signifie qu’aucun utilisateur malveillant ne peut obtenir des informations d’identification en surveillant le réseau ou en consultant des chaînes de connexion dans des fichiers de configuration.  
  
-   **Les utilisateurs sont soumis à une gestion centralisée des comptes.** Des stratégies de sécurité sont appliquées, telles que des mots de passe avec un délai d’expiration et un nombre minimal de caractères à respecter, ou encore le verrouillage des comptes après plusieurs tentatives de connexion non valides.  
  
Pour plus d’informations sur la façon de se connecter à un serveur avec l’authentification Windows, consultez [Procédure : se connecter à l’aide de l’authentification Windows](../../connect/php/how-to-connect-using-windows-authentication.md).  
  
Quand vous vous connectez à l’aide de l’authentification Windows, nous vous recommandons de configurer votre environnement pour que SQL Server puisse utiliser le protocole d’authentification Kerberos. Pour plus d’informations, consultez [Comment vous assurer que vous utilisez l’authentification Kerberos lorsque vous créez une connexion distante à une instance de SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=121862) ou [Authentification Kerberos et SQL Server](http://go.microsoft.com/fwlink/?LinkId=129226).  
  
## <a name="use-encrypted-connections-when-transferring-sensitive-data"></a>Utiliser des connexions chiffrées lors du transfert de données sensibles  
Vous devez utiliser des connexions chiffrées chaque fois que des données sensibles sont envoyées à SQL Server ou récupérées depuis SQL Server. Pour plus d’informations sur la façon d’activer des connexions chiffrées, consultez [comment activer les connexions chiffrées dans le moteur de base de données (Gestionnaire de Configuration SQL Server)](http://go.microsoft.com/fwlink/?LinkId=121864). Pour établir une connexion sécurisée avec le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], utilisez l’attribut de connexion Encrypt lors de la connexion au serveur. Pour plus d’informations sur les attributs de connexion, consultez [Connection Options](../../connect/php/connection-options.md).  
  
## <a name="use-parameterized-queries"></a>Utiliser des requêtes paramétrables  
Utilisez des requêtes paramétrables pour réduire le risque d’attaques par injection SQL. Pour obtenir des exemples d’exécution de requêtes paramétrables, consultez [How to: Perform Parameterized Queries](../../connect/php/how-to-perform-parameterized-queries.md).  
  
Pour plus d’informations sur les attaques par injection SQL et sur les considérations de sécurité associées, consultez [Injection SQL](http://go.microsoft.com/fwlink/?LinkId=104224).  
  
## <a name="do-not-accept-server-or-connection-string-information-from-end-users"></a>Ne pas accepter d’informations de chaîne de connexion ou de serveur de la part des utilisateurs finaux  
Écrivez vos applications de sorte que les utilisateurs finaux ne puissent pas envoyer d’informations de chaîne de connexion ou de serveur à l’application. Le fait de maintenir un contrôle strict sur les informations de chaîne de connexion et de serveur permet de réduire la surface d’exposition aux activités malveillantes.  
  
## <a name="turn-warningsaserrors-on-during-application-development"></a>Activer WarningsAsErrors pendant le développement d’applications  
Développez vos applications avec le paramètre **WarningsAsErrors** défini sur **true** pour que les avertissements émis par le pilote soient considérés comme des erreurs. Cela vous permettra de traiter les avertissements avant de déployer votre application. Pour plus d’informations, consultez [Handling Errors and Warnings](../../connect/php/handling-errors-and-warnings.md).  
  
## <a name="secure-logs-for-deployed-application"></a>Sécuriser les journaux pour l’application déployée  
Pour les applications déployées, assurez-vous que les journaux sont écrits dans un emplacement sécurisé ou que la journalisation est désactivée. Vous éviterez ainsi que les utilisateurs finaux accèdent aux informations qui ont été écrites dans les fichiers journaux. Pour plus d’informations, consultez [Logging Activity](../../connect/php/logging-activity.md).  
  
## <a name="see-also"></a>Voir aussi  
[Guide de programmation pour le pilote SQL Server pour PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
  

