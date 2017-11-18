---
title: Forum aux Questions (FAQ) pour le pilote JDBC | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbc0e397-ecf2-4494-87b2-a492609bceae
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 508f8526ed13af3f7f92aa500b182e077f5bb23d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="frequently-asked-questions-faq-for-jdbc-driver"></a>Forum aux Questions (FAQ) pour le pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Cet article fournit des réponses aux questions fréquemment posées sur le pilote Microsoft JDBC Driver pour SQL Server.  
  
## <a name="frequently-asked-questions"></a>Forum Aux Questions (FAQ)  
**Comment puis-je les aider à améliorer le pilote JDBC ?**  
Le pilote JDBC est open source et le code source se trouve sur [GitHub](https://github.com/microsoft/mssql-jdbc). Vous pouvez améliorer le pilote par les problèmes de classement et de contribuer à la base de code.

**Les versions de SQL Server et de Java prises en charge par le pilote ?**  
 Consultez le [Microsoft JDBC Driver pour SQL Server Support Matrix](../../connect/jdbc/microsoft-jdbc-driver-for-sql-server-support-matrix.md) page pour plus d’informations.  
  
 **Que dois-je savoir lors de la mise à niveau mon pilote ?**  
 Le Microsoft JDBC Driver 6.2 prend en charge les spécifications de JDBC 4.0, 4.1 et 4.2 et comprend deux bibliothèques de classes JAR dans le package d’installation comme suit :  
  
|JAR|Spécification JDBC|Version du JDK|  
|-|-|-|  
|MSSQL-jdbc-6.2.1.jre8.jar|JDBC 4.2, 4.1 et 4.0|JDK 8.0|  
|MSSQL-jdbc-6.2.1.jre7.jar|JDBC 4.1 et 4.0|JDK 7.0|  
 
 Les pilotes Microsoft JDBC 6.0 et 4.2 pour SQL Server prend en charge les spécifications de JDBC 4.0, 4.1 et 4.2 et inclure les deux bibliothèques de classes JAR dans le package d’installation comme suit :  
  
|JAR|Spécification JDBC|Version du JDK|   
|-|-|-|  
|sqljdbc42.jar|JDBC 4.2, 4.1 et 4.0|JDK 8.0|  
|sqljdbc41.jar|JDBC 4.1 et 4.0|JDK 7.0|  
  
 Le Microsoft JDBC Driver 4.1 pour SQL Server prend en charge la spécification JDBC 4.0 et inclut une bibliothèque de classes JAR dans le package d’installation comme suit :  
  
|JAR|Spécification JDBC|Version du JDK|    
|-|-|-|  
|sqljdbc41.jar|JDBC 4.0|JDK 7.0 et 6.0|
  
 Le pilote Microsoft JDBC Driver 4.0 pour SQL Server prend en charge les spécifications JDBC 3.0 et JDBC 4.0. Le package d’installation comprend deux bibliothèques de classes JAR pour chaque spécification : sqljdbc.jar et sqljdbc4.jar.  
  
|JAR|Spécification JDBC|Version du JDK|   
|-|-|-|  
|sqljdbc4.jar|JDBC 4.0|JDK 6.0 et 5.0|  
|sqljdbc.jar|JDBC 3.0|JDK 6.0 et 5.0|  
  
 **Je dois modifier le code de mon application pour utiliser le pilote le plus récent avec ma version existante de SQL Server**  
 En règle générale, le pilote est conçu pour assurer une compatibilité descendante. Il est donc inutile de modifier les applications existantes quand vous mettez à niveau le pilote. Dans le cas où une nouvelle version du pilote introduit une modification avec rupture, les [Notes de publication pour le pilote JDBC](../../connect/jdbc/release-notes-for-the-jdbc-driver.md) section donne des informations claires sur la modification et l’impact sur les applications existantes. Vous pouvez également consulter les notes de publication fournies avec le pilote pour obtenir la liste des bogues corrigés dans cette version et les problèmes connus.  
  
 **Combien coûte le pilote ?**  
 Le pilote Microsoft JDBC Driver pour SQL Server est disponible gratuitement.  
  
 **Puis-je redistribuer le pilote ?** Les pilotes JDBC 4.1, 4.2, 6.0 et 6.2 sont redistribuables. Passez en revue la clause « Code distribuable » dans les contrats de licence.
 
 Le pilote JDBC 4.0 est redistribuable librement sous une licence de Redistribution distincte qui nécessite une inscription. Pour inscrire ou pour plus d’informations, consultez notre [redistribution du pilote JDBC Microsoft](../../connect/jdbc/redistributing-the-microsoft-jdbc-driver.md). 
 
   
 **Puis-je utiliser le pilote pour accéder à Microsoft SQL Server à partir d’un ordinateur Linux ?** Oui. Le pilote vous permet d’accéder à SQL Server à partir de Linux, d’Unix et d’autres plateformes non-Windows. Consultez notre [Microsoft JDBC Driver pour SQL Server Support Matrix](../../connect/jdbc/microsoft-jdbc-driver-for-sql-server-support-matrix.md) pour plus d’informations.  
  
 **Le pilote prend en charge le chiffrement Secure Sockets Layer (SSL) ?** Le pilote prend en charge le chiffrement SSL à compter de la version 1.2. Pour plus d’informations, consultez [le chiffrement SSL à l’aide de](../../connect/jdbc/using-ssl-encryption.md).  
  
 **Les types d’authentification sont pris en charge par le pilote JDBC de Microsoft pour SQL Server ?**  
 Le tableau ci-dessous répertorie les options d’authentification disponibles. Notez que l’authentification Kerberos en Java pur est disponible à compter de la version 4.0 du pilote.  
  
|||  
|-|-|  
|Plateforme|Authentification|  
|Non-Windows|Kerberos en Java pur|  
|Non-Windows|SQL Server|  
|Windows|Kerberos en Java pur|  
|Windows|SQL Server|  
|Windows|Kerberos avec sauvegarde NTLM|  
|Windows|NTLM|  
  
**Le pilote prend-il en charge Internet Protocol version 6 (IPv6) des adresses ?**  
 Oui. Le pilote JDBC prend en charge l’utilisation d’adresses IPv6 avec la collection de propriétés de connexion et la propriété de chaîne de connexion serverName. Pour plus d’informations, consultez [générer l’URL de connexion](../../connect/jdbc/building-the-connection-url.md).  
  
**Quelle est la mise en mémoire tampon adaptative ?**  
 Introduite dans la version 1.2 du pilote JDBC Driver pour Microsoft SQL Server 2005, la mise en mémoire tampon adaptative permet de récupérer n’importe quel volume de données de grande valeur sans occasionner la surcharge des curseurs côté serveur. La fonctionnalité de mise en mémoire tampon adaptative du pilote JDBC Driver pour Microsoft SQL Server fournit une propriété de chaîne de connexion, responseBuffering, qui peut avoir la valeur « adaptive » ou « full ». À compter de la version 2.0 du pilote JDBC Driver, le comportement par défaut du pilote est « adaptive ». En d'autres termes, pour pouvoir obtenir le comportement de mise en mémoire tampon adaptative, votre application n'a pas besoin de requérir explicitement le mode de mise en mémoire tampon adaptative. Toutefois, dans la version 1.2, le mode de mise en mémoire tampon était « full » par défaut, et l’application devait demander explicitement le mode de mise en mémoire tampon adaptative. Pour plus d’informations, consultez [à l’aide de mise en mémoire tampon adaptative](../../connect/jdbc/using-adaptive-buffering.md) rubrique et le blog de [qu’adaptiveresponse en mémoire tampon et pourquoi dois-je l’utiliser ?](http://go.microsoft.com/fwlink/?LinkId=111575).  
  
**Est le pilote prise en charge le regroupement de connexions ?**  
 Le pilote prend en charge le regroupement de connexions Java EE 5 (Java Platform, Enterprise Edition 5). Le pilote implémente les interfaces JDBC 3.0 nécessaires pour qu’il puisse participer aux implémentations de regroupements de connexions fournies par des fournisseurs de serveurs d’applications intergicielles (middleware). Le pilote participe à des connexions regroupées dans ces environnements. Pour plus d’informations, consultez [le regroupement de connexions à l’aide de](../../connect/jdbc/using-connection-pooling.md). Le pilote ne fournit pas sa propre implémentation de regroupement, mais il s’appuie sur des serveurs d’applications Java tiers.  
  
**Prise en charge n’est disponible pour le pilote ?**  
 Plusieurs options de support technique sont disponibles. Vous pouvez poser votre question ou problème à notre [référentiel GitHub](https://github.com/microsoft/mssql-jdbc) qui est surveillé par Microsoft. [Forums](http://go.microsoft.com/fwlink/?LinkID=246673) sont contrôlés par Microsoft, MVP et la Communauté. Vous pouvez aussi contacter le support technique Microsoft. Nous vous demanderons peut-être de reproduire le problème en dehors de tout serveur d’applications tiers. Si le problème ne peut pas être reproduit en dehors de l’environnement conteneur Java hôte, vous devez impliquer le tiers associé pour que nous puissions continuer à vous aider. Nous vous demanderons peut-être de reproduire le problème sur un système d’exploitation tel que Windows pour mieux vous aider.  
  
**Le pilote est certifié pour une utilisation avec des serveurs d’applications tierces ?**
Le pilote a été testé sur divers serveurs d’applications, notamment IBM WebSphere et SAP Netweaver.  
  
**Comment faire pour activer le suivi ?**  
 Le pilote JDBC Driver prend en charge l’utilisation du suivi (ou journalisation) pour faciliter la résolution des problèmes liés à son utilisation dans votre application. Pour activer l’utilisation du suivi JAR côté client, le pilote JDBC Driver utilise les API de journalisation dans java.util.logging. Pour plus d’informations, consultez [fonctionnement du pilote de traçage](../../connect/jdbc/tracing-driver-operation.md). Pour le suivi XA côté serveur, consultez [Suivi de l’accès aux données dans SQL Server](http://go.microsoft.com/fwlink/?LinkId=248705).  
  
**Où puis-je télécharger des versions antérieures du pilote tels que le pilote JDBC de SQL Server 2000, 2005 pilote, 1.0, 1.1 et 1.2 du pilote ?**  
 Ces versions du pilote ne sont pas disponibles en téléchargement, car elles ne sont plus prises en charge. Nous améliorons constamment la prise en charge de la connectivité Java. Nous vous recommandons donc vivement d’utiliser la dernière version de notre pilote JDBC.  
  
 **J’utilise JRE 1.4. Quel est le pilote compatible avec JRE 1.4** pour les clients qui utilisent les produits SAP et requièrent la prise en charge JRE 1.4, vous pouvez contacter [SAPService Marketplace](http://service.sap.com/) pour obtenir le pilote Microsoft JDBC 1.2.  
  
**Le pilote peut-il communiquer à l’aide d’algorithmes validés FIPS ?** Le pilote Microsoft JDBC Driver ne contient aucun algorithme de chiffrement. Si un client exploite des algorithmes du système d’exploitation, d’applications et JVM jugés conformes aux normes FIPS (Federal Information Processing Standards) et qu’il configure le pilote de telle sorte qu’il utilise ces algorithmes, le pilote utilise uniquement les algorithmes désignés pour la communication.  
  
  

