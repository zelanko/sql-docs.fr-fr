---
title: Forum aux Questions (FAQ) pour le pilote JDBC | Documents Microsoft
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: cbc0e397-ecf2-4494-87b2-a492609bceae
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2ebe12966a73d5944c2cfb6eb1a2328e27a5385e
ms.sourcegitcommit: 73ca0313b185e730579f09f9bc32a852c9dd2ef4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2018
ms.locfileid: "35452159"
---
# <a name="frequently-asked-questions-faq-for-jdbc-driver"></a>Forum aux Questions (FAQ) pour le pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Cette page fournit des réponses aux questions fréquemment posées sur le pilote JDBC de Microsoft pour SQL Server.  
  
## <a name="frequently-asked-questions"></a>Forum Aux Questions (FAQ)  
**Comment puis-je les aider à améliorer le pilote JDBC ?**  
Le pilote JDBC est open source et le code source se trouve sur [GitHub](https://github.com/microsoft/mssql-jdbc). Vous pouvez améliorer le pilote par les problèmes de classement et de contribuer à la base de code.

**Les versions de SQL Server et effectuez le Java la prise en charge du pilote ?**  
 Consultez le [Microsoft JDBC Driver pour SQL Server Support Matrix](../../connect/jdbc/microsoft-jdbc-driver-for-sql-server-support-matrix.md) page pour plus d’informations.  
  
**Quelle est la différence entre les packages de pilotes JDBC disponibles sur du Microsoft Download Center et le pilote JDBC disponible sur GitHub ?**  
 JDBC fichiers de pilote disponibles sur le référentiel GitHub pour le pilote Microsoft JDBC sont au cœur du pilote JDBC et sous la licence open source répertoriée dans le référentiel. Les packages de pilotes sur du Microsoft Download Center incluent des bibliothèques supplémentaires pour l’authentification Windows intégrée et l’activation des transactions XA avec le pilote JDBC. Ces bibliothèques supplémentaires sont sous licence incluse avec le package téléchargeable.

 **Que dois-je savoir lors de la mise à niveau mon pilote ?**  
 Le prend en charge le pilote Microsoft JDBC 6.4 le JDBC 4.1, 4.2 et 4.3 spécifications (partiellement) et inclut trois bibliothèques de classes JAR dans le package d’installation comme suit :  
  
|JAR|Spécification JDBC|Version du JDK|  
|-|-|-|  
|mssql-jdbc-6.4.0.jre9.jar|JDBC 4.3 (partiellement), 4.2 et 4.1|JDK 9.0|  
|mssql-jdbc-6.4.0.jre8.jar|JDBC 4.2 et 4.1|JDK 8.0|  
|mssql-jdbc-6.4.0.jre7.jar|JDBC 4.1|JDK 7.0|  

 Le Microsoft JDBC Driver 6.2 prend en charge les spécifications de JDBC 4.0, 4.1 et 4.2 et comprend deux bibliothèques de classes JAR dans le package d’installation comme suit :  
  
|JAR|Spécification JDBC|Version du JDK|  
|-|-|-|  
|mssql-jdbc-6.2.1.jre8.jar|JDBC 4.2, 4.1 et 4.0|JDK 8.0|  
|mssql-jdbc-6.2.1.jre7.jar|JDBC 4.1 et 4.0|JDK 7.0|  
 
 Les pilotes Microsoft JDBC 6.0 et 4.2 pour SQL Server prend en charge les spécifications de JDBC 4.0, 4.1 et 4.2 et inclure les deux bibliothèques de classes JAR dans le package d’installation comme suit :  
  
|JAR|Spécification JDBC|Version du JDK|   
|-|-|-|  
|sqljdbc42.jar|JDBC 4.2, 4.1 et 4.0|JDK 8.0|  
|sqljdbc41.jar|JDBC 4.1 et 4.0|JDK 7.0|  
  
 Le Microsoft JDBC Driver 4.1 pour SQL Server prend en charge la spécification JDBC 4.0 et inclut une bibliothèque de classes JAR dans le package d’installation comme suit :  
  
|JAR|Spécification JDBC|Version du JDK|    
|-|-|-|  
|sqljdbc41.jar|JDBC 4.0|JDK 7.0 et 6.0|
  
 **Je dois modifier le code de mon application pour utiliser le pilote le plus récent avec ma version existante de SQL Server**  
 En général, le pilote est conçu pour offrir une compatibilité descendante afin que vous n’avez pas besoin de modifier les applications existantes lors de la mise à niveau le pilote. Dans le cas où une nouvelle version du pilote introduit une modification avec rupture, les [Notes de publication pour le pilote JDBC](../../connect/jdbc/release-notes-for-the-jdbc-driver.md) section fournit des informations claires sur la modification et l’impact sur les applications existantes. Vous pouvez également consulter les notes de publication fournies avec le pilote pour obtenir la liste des bogues corrigés dans cette version et les problèmes connus.  
  
 **Combien coûte le pilote ?**  
 Le pilote Microsoft JDBC Driver pour SQL Server est disponible gratuitement.  
  
 **Puis-je redistribuer le pilote ?** Les pilotes JDBC 4.1, 4.2, 6.0, 6.2 et 6.4 sont redistribuables. Passez en revue la clause « Code distribuable » dans les contrats de licence. 
   
 **Puis-je utiliser le pilote pour accéder à Microsoft SQL Server à partir d’un ordinateur Linux ?** Oui. Le pilote vous permet d’accéder à SQL Server à partir de Linux, d’Unix et d’autres plateformes non-Windows. Pour plus d’informations, consultez [Microsoft JDBC Driver pour SQL Server Support Matrix](../../connect/jdbc/microsoft-jdbc-driver-for-sql-server-support-matrix.md).
  
 **Le pilote prend en charge le chiffrement Secure Sockets Layer (SSL) ?** Le pilote prend en charge le chiffrement SSL à compter de la version 1.2. Pour plus d’informations, consultez [le chiffrement SSL à l’aide de](../../connect/jdbc/using-ssl-encryption.md).  
  
 **Les types d’authentification sont pris en charge par le pilote JDBC de Microsoft pour SQL Server ?**  
 Le tableau ci-dessous répertorie les options d’authentification disponibles. Une authentification Kerberos en Java pure est disponible à partir de la version 4.0 du pilote.  
  
|||  
|-|-|  
|Plateforme|Authentification|  
|Non-Windows|Kerberos en Java pur|  
|Non-Windows|SQL Server|  
|Non-Windows|Authentification Azure Active Directory|
|Windows|Kerberos en Java pur|  
|Windows|SQL Server|
|Windows|Kerberos avec sauvegarde NTLM|  
|Windows|NTLM|  
|Windows|Authentification Azure Active Directory|  
  
**Le pilote prend-il en charge Internet Protocol version 6 (IPv6) des adresses ?**  
 Oui. Le pilote prend en charge l’utilisation d’adresses IPv6. Utilisez la collection de propriétés de connexion et la propriété de chaîne de connexion serverName. Pour plus d’informations, consultez [générer l’URL de connexion](../../connect/jdbc/building-the-connection-url.md).  
  
**Quelle est la mise en mémoire tampon adaptative ?**  
 Mise en mémoire tampon adaptative a été introduite avec Microsoft SQL Server 2005 JDBC Driver version 1.2. Il est conçu pour récupérer tout type de données de grande valeur sans la surcharge des curseurs côté serveur. La fonctionnalité de mise en mémoire tampon adaptative du pilote JDBC Driver pour Microsoft SQL Server fournit une propriété de chaîne de connexion, responseBuffering, qui peut avoir la valeur « adaptive » ou « full ». Dans la version 1.2, le mode de mise en mémoire tampon est « complète » par défaut et l’application doit définir le mode de mise en mémoire tampon adaptative explicitement. À compter de la version 2.0 du pilote JDBC Driver, le comportement par défaut du pilote est « adaptive ». Par conséquent, votre application n’a pas demander le comportement adaptative explicitement pour obtenir le comportement de mise en mémoire tampon adaptative. Pour plus d’informations, consultez [à l’aide de mise en mémoire tampon adaptative](../../connect/jdbc/using-adaptive-buffering.md) et le blog de [qu’adaptiveresponse en mémoire tampon et pourquoi dois-je l’utiliser ?](http://go.microsoft.com/fwlink/?LinkId=111575).
  
**Est le pilote prise en charge le regroupement de connexions ?**  
 Le pilote prend en charge le regroupement de connexions Java EE 5 (Java Platform, Enterprise Edition 5). Le pilote implémente les interfaces JDBC 3.0 nécessaires pour qu’il puisse participer aux implémentations de regroupements de connexions fournies par des fournisseurs de serveurs d’applications intergicielles (middleware). Le pilote participe à des connexions regroupées dans ces environnements. Pour plus d’informations, consultez [le regroupement de connexions à l’aide de](../../connect/jdbc/using-connection-pooling.md). Le pilote ne fournit pas sa propre implémentation de regroupement, mais il s’appuie sur des serveurs d’applications Java tiers.  
  
**Prise en charge n’est disponible pour le pilote ?**  
 Plusieurs options de support technique sont disponibles. Vous pouvez poser votre question ou problème à notre [référentiel GitHub](https://github.com/microsoft/mssql-jdbc) qui est surveillé par Microsoft. [Forums](http://go.microsoft.com/fwlink/?LinkID=246673) sont contrôlés par Microsoft, des MVP et la Communauté. Vous pouvez aussi contacter le support technique Microsoft. L’équipe de développement peut vous demander de reproduire le problème à l’extérieur de tous les serveurs d’applications tierces. Si le problème ne peut pas être reproduit en dehors de l’environnement conteneur Java hôte, vous devez impliquer le tiers associé afin que l’équipe peut continuer à vous aider. L’équipe peut également vous demander de reproduire le problème sur un système d’exploitation, tels que les fenêtres donc le problème peut être mieux pris en charge.  
  
**Le pilote est certifié pour une utilisation avec des serveurs d’applications tierces ?**
Le pilote a été testé sur divers serveurs d’applications, notamment IBM WebSphere et SAP Netweaver.  
  
**Comment faire pour activer le suivi ?**  
 Le pilote JDBC Driver prend en charge l’utilisation du suivi (ou journalisation) pour faciliter la résolution des problèmes liés à son utilisation dans votre application. Pour activer l’utilisation du suivi JAR côté client, le pilote JDBC Driver utilise les API de journalisation dans java.util.logging. Pour plus d’informations, consultez [fonctionnement du pilote de traçage](../../connect/jdbc/tracing-driver-operation.md). Pour le suivi XA côté serveur, consultez [Suivi de l’accès aux données dans SQL Server](http://go.microsoft.com/fwlink/?LinkId=248705).  
  
**Où puis-je télécharger des versions antérieures du pilote tels que le pilote JDBC de SQL Server 2000, 2005 pilote, 1.0, 1.1 et 1.2 du pilote ?**  
 Ces versions du pilote ne sont pas disponibles en téléchargement, car elles ne sont plus prises en charge. Nous améliorons constamment la prise en charge de la connectivité Java. Par conséquent, nous vous recommandons vivement de que vous travaillez avec la dernière version du pilote JDBC de Microsoft.  
  
**J’utilise JRE 1.4. Le pilote est compatible avec JRE 1.4 ?**  
 Si vous utilisez des produits SAP et que vous devez assurer la prise en charge de JRE 1.4, contactez le [SAPService Marketplace](http://service.sap.com/) pour obtenir la version 1.2 du pilote Microsoft JDBC Driver.  
  
**Le pilote peut-il communiquer à l’aide d’algorithmes validés FIPS ?**  
 Le pilote Microsoft JDBC Driver ne contient aucun algorithme de chiffrement. Si un client s’appuie sur le système d’exploitation, des applications et des algorithmes JVM jugés par traitement aux normes FIPS (Federal Information) et configure le pilote pour utiliser ces algorithmes le pilote utilise uniquement les algorithmes désignés pour communications.  
  
 ## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
