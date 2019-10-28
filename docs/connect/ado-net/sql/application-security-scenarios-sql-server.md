---
title: Scénarios de sécurité des applications dans SQL Server
description: Contient des rubriques présentant différents scénarios de sécurité pour les applications ADO.NET et SQL Server.
ms.date: 09/26/2019
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 711086e881951d9e82fd34851c451e5472e49d7e
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452343"
---
# <a name="application-security-scenarios-in-sql-server"></a>Scénarios de sécurité des applications dans SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Il n’existe pas de méthode correcte pour créer une application cliente SQL Server sécurisée. Chaque application est unique dans ses exigences, son environnement de déploiement et son remplissage utilisateur. Une application qui est raisonnablement sécurisée lors du déploiement initial peut devenir moins sécurisée au fil du temps. Il est impossible de prédire avec précision quelles menaces peuvent émerger à l’avenir.  
  
SQL Server, en tant que produit, a évolué sur de nombreuses versions pour incorporer les fonctionnalités de sécurité les plus récentes permettant aux développeurs de créer des applications de base de données sécurisées. Toutefois, la sécurité n’entre pas dans le cadre ; elle nécessite une surveillance et une mise à jour continues.  
  
## <a name="common-threats"></a>Menaces courantes  
Les développeurs doivent comprendre les menaces de sécurité, les outils fournis pour les éliminer et comment éviter les brèches de sécurité. La sécurité peut être considérée comme une chaîne, où une rupture d’un lien compromet la force de l’ensemble. La liste suivante présente certaines menaces de sécurité courantes qui sont abordées plus en détail dans les rubriques de cette section.  
  
### <a name="sql-injection"></a>injection SQL  
L’injection SQL est le processus par lequel un utilisateur malveillant entre des instructions Transact-SQL au lieu d’une entrée valide. Si l’entrée est transmise directement au serveur sans validation et si l’application exécute par inadvertance le code injecté, l’attaque risque d’endommager ou de détruire des données. Vous pouvez déjouer les attaques par injection SQL Server en utilisant des procédures stockées et des commandes paramétrées, en évitant les instructions SQL dynamiques et en limitant les autorisations de l’ensemble des utilisateurs.  
  
### <a name="elevation-of-privilege"></a>Élévation de privilège  
Les attaques par élévation de privilèges se produisent lorsqu’un utilisateur est en mesure de supposer les privilèges d’un compte approuvé, tel qu’un propriétaire ou un administrateur. Exécutez toujours sous les comptes d’utilisateur dotés de privilèges minimum et attribuez uniquement les autorisations nécessaires. Évitez d’utiliser des comptes d’administration ou de propriétaire pour exécuter du code. Cela limite le nombre de dommages qui peuvent se produire si une attaque réussit. Lorsque vous effectuez des tâches qui nécessitent des autorisations supplémentaires, utilisez la signature de procédure ou l’emprunt d’identité uniquement pour la durée de la tâche. Vous pouvez signer les procédures stockées à l’aide de certificats ou utiliser l’emprunt d’identité pour affecter des autorisations de manière temporaire.  
  
### <a name="probing-and-intelligent-observation"></a>Détection et observation intelligente  
Une attaque par sondage peut utiliser des messages d’erreur générés par une application pour rechercher des failles de sécurité. Implémentez la gestion des erreurs dans tout le code procédural pour empêcher SQL Server informations d’erreur d’être renvoyées à l’utilisateur final.  
  
### <a name="authentication"></a>Authentification  
Une attaque par injection de chaîne de connexion peut se produire lors de l’utilisation de SQL Server connexions si une chaîne de connexion basée sur l’entrée d’utilisateur est construite au moment de l’exécution. Si la chaîne de connexion n’est pas vérifiée pour les paires de mots clés valides, une personne malveillante peut insérer des caractères supplémentaires, en accédant potentiellement à des données sensibles ou à d’autres ressources sur le serveur. Utilisez l’authentification Windows dans la mesure du possible. Si vous devez utiliser des connexions SQL Server, utilisez la <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder> pour créer et valider des chaînes de connexion au moment de l’exécution.  
  
### <a name="passwords"></a>Mots de passe  
De nombreuses attaques réussissent parce qu’un intrus a pu obtenir ou deviner un mot de passe pour un utilisateur privilégié. Les mots de passe constituant votre première ligne de défense contre les intrus, le choix de mots de passe forts est essentiel à la sécurité de votre système. À partir de SQL Server 2005, créez et appliquez des stratégies de mot de passe pour l'authentification en mode mixte.  
  
Affectez toujours un mot de passe fort au compte `sa`, même si vous utilisez l’authentification Windows.  
  
## <a name="in-this-section"></a>Contenu de cette section  
[Écriture d’une instruction SQL dynamique sécurisée dans SQL Server](writing-secure-dynamic-sql.md)  
Décrit les techniques d’écriture de SQL dynamique sécurisé à l’aide de procédures stockées.  

## <a name="next-steps"></a>Étapes suivantes
- [Sécurité de SQL Server](sql-server-security.md)
