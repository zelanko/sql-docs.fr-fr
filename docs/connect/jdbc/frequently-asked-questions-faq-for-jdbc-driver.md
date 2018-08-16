---
title: Questions fréquentes (FAQ) sur le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 07/19/2018
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
ms.openlocfilehash: 43fccc172756b8e7afdb4522c53693915be0f23c
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39662331"
---
# <a name="frequently-asked-questions-faq-for-jdbc-driver"></a>Questions fréquentes (FAQ) sur le pilote JDBC

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Cette page fournit des réponses aux questions fréquemment posées sur le pilote Microsoft JDBC Driver pour SQL Server.

## <a name="frequently-asked-questions"></a>Forum Aux Questions (FAQ)

**Comment puis-je améliorer le pilote JDBC ?**  
Le pilote JDBC est open source et vous trouverez le code source sur [GitHub](https://github.com/microsoft/mssql-jdbc). Vous pouvez aider à améliorer le pilote en soumettant des problèmes et en contribuant à la base de code.

**Quelles sont les versions de SQL Server et de Java prises en charge par le pilote ?**  
Pour obtenir des détails, consultez la page [Matrice de prise en charge de Microsoft JDBC Driver pour SQL Server](../../connect/jdbc/microsoft-jdbc-driver-for-sql-server-support-matrix.md).

**Quelle est la différence entre les packages de pilotes JDBC disponibles sur du Microsoft Download Center et le pilote JDBC disponible sur GitHub ?**  
JDBC driver fichiers disponibles sur le référentiel GitHub pour le pilote JDBC de Microsoft sont au cœur du pilote JDBC et sous la licence open source répertoriée dans le référentiel. Les packages de pilotes sur du Microsoft Download Center incluent des bibliothèques supplémentaires pour l’authentification Windows intégrée et l’activation des transactions XA avec le pilote JDBC. Ces bibliothèques supplémentaires sont sous la licence incluse avec le package téléchargeable.

**Que faut-il savoir avant la mise à niveau du pilote ?**  
 Microsoft JDBC Driver 7.0 prend en charge JDBC 4.2 et 4.3 spécifications (partiellement) et inclut deux bibliothèques de classes JAR dans le package d’installation comme suit :

| JAR                        | Spécification JDBC            | Version du JDK |
| -------------------------- | ----------------------------- | ----------- |
| mssql-jdbc-7.0.0.jre10.jar | JDBC 4.3 (partiellement) et 4.2 | JDK 10.0    |
| mssql-jdbc-7.0.0.jre8.jar  | JDBC 4.2                      | JDK 8.0     |

Le prend en charge de Microsoft JDBC Driver 6.4 le JDBC 4.1, 4.2 et 4.3 spécifications (partiellement) et inclut trois bibliothèques de classes JAR dans le package d’installation comme suit :

| JAR                       | Spécification JDBC                 | Version du JDK |
| ------------------------- | ---------------------------------- | ----------- |
| mssql-jdbc-6.4.0.jre9.jar | JDBC 4.3 (partiellement), 4.2 et 4.1 | JDK 9.0     |
| mssql-jdbc-6.4.0.jre8.jar | JDBC 4.2 et 4.1                  | JDK 8.0     |
| mssql-jdbc-6.4.0.jre7.jar | JDBC 4.1                           | JDK 7.0     |

Microsoft JDBC Driver 6.2 prend en charge les spécifications de JDBC 4.0, 4.1 et 4.2 et inclut deux bibliothèques de classes JAR dans le package d’installation comme suit :

| JAR                       | Spécification JDBC     | Version du JDK |
| ------------------------- | ---------------------- | ----------- |
| MSSQL-jdbc-6.2.2.jre8.jar | JDBC 4.2, 4.1 et 4.0 | JDK 8.0     |
| MSSQL-jdbc-6.2.2.jre7.jar | JDBC 4.1 et 4.0       | JDK 7.0     |

Les pilotes Microsoft JDBC 6.0 et 4.2 pour SQL Server prend en charge les spécifications de JDBC 4.0, 4.1 et 4.2 et inclure deux bibliothèques de classes JAR dans le package d’installation comme suit :

| JAR           | Spécification JDBC     | Version du JDK |
| ------------- | ---------------------- | ----------- |
| sqljdbc42.jar | JDBC 4.2, 4.1 et 4.0 | JDK 8.0     |
| sqljdbc41.jar | JDBC 4.1 et 4.0       | JDK 7.0     |

Le Microsoft JDBC Driver 4.1 pour SQL Server prend en charge la spécification JDBC 4.0 et inclut une bibliothèque de classes JAR dans le package d’installation comme suit :

| JAR           | Spécification JDBC | Version JDK     |
| ------------- | ------------------ | --------------- |
| sqljdbc41.jar | JDBC 4.0           | JDK 7.0 et 6.0 |

**Dois-je modifier le code de mon application pour pouvoir utiliser le pilote le plus récent avec ma version existante de SQL Server ?**  
En règle générale, le pilote est conçu pour assurer une compatibilité descendante. Il est donc inutile de modifier les applications existantes quand vous mettez à niveau le pilote. Dans le cas où une nouvelle version du pilote introduit une modification avec rupture, les [Notes de publication pour le pilote JDBC](../../connect/jdbc/release-notes-for-the-jdbc-driver.md) section fournit des informations claires sur la modification et l’impact sur les applications existantes. Vous pouvez également consulter les notes de publication fournies avec le pilote pour obtenir la liste des bogues corrigés dans cette version et les problèmes connus.

**Combien coûte le pilote ?**  
Le pilote Microsoft JDBC Driver pour SQL Server est disponible gratuitement.

**Puis-je redistribuer le pilote ?**
Les pilotes JDBC 4.1, 4.2, 6.0, 6.2, 6.4 et 7.0 sont redistribuables. Passez en revue la clause « Code distribuable » dans les contrats de licence.

**Puis-je utiliser le pilote pour accéder à Microsoft SQL Server à partir d’un ordinateur Linux ?**
Oui. Le pilote vous permet d’accéder à SQL Server à partir de Linux, d’Unix et d’autres plateformes non-Windows. Pour plus d’informations, consultez [Microsoft JDBC Driver pour SQL Server Support Matrix](../../connect/jdbc/microsoft-jdbc-driver-for-sql-server-support-matrix.md).

**Le pilote prend-il en charge le chiffrement SSL (Secure Sockets Layer) ?**
Le pilote prend en charge le chiffrement SSL à compter de la version 1.2. Pour plus d’informations, consultez [Utilisation du chiffrement SSL](../../connect/jdbc/using-ssl-encryption.md).

**Quels sont les types d’authentification pris en charge par le pilote Microsoft JDBC Driver pour SQL Server ?**  
Le tableau ci-dessous répertorie les options d’authentification disponibles. Une authentification Kerberos en Java pur est disponible à compter de la version 4.0 du pilote.

|             |                                       |
| ----------- | ------------------------------------- |
| Plateforme    | Authentification                        |
| Non-Windows | Kerberos en Java pur                    |
| Non-Windows | SQL Server                            |
| Non-Windows | Authentification Azure Active Directory |
| Windows     | Kerberos en Java pur                    |
| Windows     | SQL Server                            |
| Windows     | Kerberos avec sauvegarde NTLM             |
| Windows     | NTLM                                  |
| Windows     | Authentification Azure Active Directory |

**Le pilote prend-il en charge les adresses IPv6 (Internet Protocol version 6) ?**  
Oui. Le pilote prend en charge l’utilisation d’adresses IPv6. Utilisez la collection de propriétés de connexion et la propriété de chaîne de connexion serverName. Pour plus d’informations, consultez [Création de l’URL de connexion](../../connect/jdbc/building-the-connection-url.md).

**Qu’est-ce que la mise en mémoire tampon adaptative ?**  
Mise en mémoire tampon adaptative a été introduite avec Microsoft SQL Server 2005 JDBC Driver version 1.2. Elle est conçue pour récupérer tout type de données de valeur élevée sans la charge mémoire associée aux curseurs côté serveur. La fonctionnalité de mise en mémoire tampon adaptative du pilote JDBC Driver pour Microsoft SQL Server fournit une propriété de chaîne de connexion, responseBuffering, qui peut avoir la valeur « adaptive » ou « full ». Dans la version 1.2, le mode de mise en mémoire tampon est « full » par défaut ; par ailleurs, l’application doit définir explicitement le mode de mise en mémoire tampon adaptative. À compter de la version 2.0 du pilote JDBC Driver, le comportement par défaut du pilote est « adaptive ». Par conséquent, votre application n’a pas besoin de requérir explicitement le comportement de la mise en mémoire tampon adaptative pour l’obtenir. Pour plus d’informations, consultez [Utilisation de la mise en mémoire tampon adaptative](../../connect/jdbc/using-adaptive-buffering.md) et le blog [What is adaptiveresponse buffering and why should I use it?](http://go.microsoft.com/fwlink/?LinkId=111575).

**Le pilote prend-il en charge le regroupement de connexions ?**  
Le pilote prend en charge le regroupement de connexions Java EE 5 (Java Platform, Enterprise Edition 5). Le pilote implémente les interfaces JDBC 3.0 nécessaires pour qu’il puisse participer aux implémentations de regroupements de connexions fournies par des fournisseurs de serveurs d’applications intergicielles (middleware). Le pilote participe à des connexions regroupées dans ces environnements. Pour plus d’informations, consultez [Utilisation d’un regroupement de connexions](../../connect/jdbc/using-connection-pooling.md). Le pilote ne fournit pas sa propre implémentation de regroupement, mais il s’appuie sur des serveurs d’applications Java tiers.

**Le pilote bénéficie-t-il des services du support technique ?**  
Plusieurs options de support technique sont disponibles. Vous pouvez publier votre question ou problème à notre [référentiel GitHub](https://github.com/microsoft/mssql-jdbc) qui est surveillé par Microsoft. [Forums](http://go.microsoft.com/fwlink/?LinkID=246673) sont gérés par Microsoft, MVP et la Communauté. Vous pouvez aussi contacter le support technique Microsoft. L’équipe de développement peut vous demander de reproduire le problème en dehors de tout serveur d’applications tiers. Si le problème ne peut pas être reproduit en dehors de l’environnement conteneur Java hôte, vous devez impliquer le tiers associé pour que l’équipe puisse continuer à vous aider. L’équipe peut également vous demander de reproduire le problème sur un système d’exploitation tels que Windows pour le problème peut être mieux pris en charge.

**Le pilote est-il certifié dans le cadre d’une utilisation avec des serveurs d’applications tiers ?**
Le pilote a été testé sur divers serveurs d’applications, notamment IBM WebSphere et SAP Netweaver.

**Comment activer le suivi ?**  
Le pilote JDBC Driver prend en charge l’utilisation du suivi (ou journalisation) pour faciliter la résolution des problèmes liés à son utilisation dans votre application. Pour activer l’utilisation du suivi JAR côté client, le pilote JDBC Driver utilise les API de journalisation dans java.util.logging. Pour plus d’informations, consultez [Suivi du fonctionnement du pilote](../../connect/jdbc/tracing-driver-operation.md). Pour le suivi XA côté serveur, consultez [Suivi de l’accès aux données dans SQL Server](http://go.microsoft.com/fwlink/?LinkId=248705).

**Où puis-je télécharger les anciennes versions du pilote, notamment le pilote JDBC pour SQL Server 2000, 2005 ou encore les versions 1.0, 1.1 ou 1.2 du pilote ?**  
Ces versions du pilote ne sont pas disponibles en téléchargement, car elles ne sont plus prises en charge. Nous améliorons constamment la prise en charge de la connectivité Java. Nous vous recommandons donc vivement d’utiliser la dernière version du pilote Microsoft JDBC Driver.

**J’utilise JRE 1.4. Quel est le pilote compatible avec JRE 1.4 ?**  
Si vous utilisez des produits SAP et que vous devez assurer la prise en charge de JRE 1.4, contactez le [SAPService Marketplace](http://service.sap.com/) pour obtenir la version 1.2 du pilote Microsoft JDBC Driver.

**Le pilote peut-il communiquer à l’aide d’algorithmes validés par FIPS ?**  
Le pilote Microsoft JDBC Driver ne contient aucun algorithme de chiffrement. Si un client exploite des algorithmes du système d’exploitation, d’applications et JVM jugés conformes aux normes FIPS (Federal Information Processing Standards) et qu’il configure le pilote de telle sorte qu’il utilise ces algorithmes, le pilote utilise uniquement les algorithmes désignés pour la communication.

## <a name="see-also"></a> Voir aussi

[Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)
