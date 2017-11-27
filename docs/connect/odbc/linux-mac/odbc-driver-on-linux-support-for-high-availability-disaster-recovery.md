---
title: "Pilote ODBC sur Linux et macOS - haute disponibilité et récupération d’urgence | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa656c5b-a935-40bf-bc20-e517ca5cd0ba
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 53553cc88d771aeb7ef7d537309583fb49e1aaa6
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="odbc-driver-on-linux-and-macos-support-for-high-availability-and-disaster-recovery"></a>Pilote ODBC sur Linux et macOS prise en charge de la haute disponibilité et récupération d’urgence
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Les pilotes ODBC pour la prise en charge de Linux et macOS [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]. Pour plus d’informations sur [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)], consultez :  
  
-   [Écouteurs de groupe de disponibilité, connectivité Client et basculement d’Application (SQL Server)](http://msdn.microsoft.com/library/hh213417.aspx)  
  
-   [Création et Configuration des groupes de disponibilité (SQL Server)](http://msdn.microsoft.com/library/ff878265.aspx)  
  
-   [Clustering de basculement et groupes de disponibilité AlwaysOn (SQL Server)](http://msdn.microsoft.com/library/ff929171.aspx)  
  
-   [Secondaires actifs : Réplicas secondaires lisibles (groupes de disponibilité AlwaysOn)](http://msdn.microsoft.com/library/ff878253.aspx)  
  
Vous pouvez spécifier l’écouteur d’un groupe de disponibilité donné dans la chaîne de connexion. Si une application ODBC sur Linux ou macOS est connectée à une base de données dans un groupe de disponibilité qui bascule, la connexion d’origine est rompue et l’application doit ouvrir une nouvelle connexion pour continuer à fonctionner après le basculement.

Les pilotes ODBC sur Linux et macOS itérer séquentiellement toutes les adresses IP si vous ne vous connectez pas à un écouteur de groupe de disponibilité, et plusieurs adresses IP sont associés avec le nom d’hôte associés à un nom d’hôte DNS.

Si la première adresse IP retournée du serveur DNS n’est pas connectable, ces itérations peuvent prendre beaucoup de temps. Lors de la connexion à un écouteur de groupe de disponibilité, le pilote tente d’établir des connexions à toutes les adresses IP en parallèle. Si une tentative de connexion réussit, le pilote ignore toutes les tentatives de connexion en attente.

> [!NOTE]  
> Car une connexion peut échouer en raison d’un basculement du groupe de disponibilité, implémenter la logique de nouvelle tentative de connexion ; Réessayez un échec de connexion jusqu'à ce qu’il se reconnecte. L’augmentation du délai de connexion et l’implémentation de la logique déclenchement de nouvelles tentatives de connexion augmentent le risque de connexion à un groupe de disponibilité.

## <a name="connecting-with-multisubnetfailover"></a>Connexion à MultiSubnetFailover

Spécifiez toujours **MultiSubnetFailover = Yes** (ou **= True**) lors de la connexion à un [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] écouteur du groupe de disponibilité ou [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] Instance de Cluster de basculement. **MultiSubnetFailover** permet un basculement plus rapide pour tous les groupes de disponibilité et une instance de cluster de basculement dans [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)]. **MultiSubnetFailover** réduit également sensiblement le temps de basculement pour les topologies AlwaysOn de sous-réseaux uniques et multiples. Pendant un basculement de sous-réseaux multiples, le client tente des connexions en parallèle. Lors d’un basculement de sous-réseau, le pilote a retente agressivement la connexion TCP.

La propriété de connexion **MultiSubnetFailover** indique que l’application est déployée dans un groupe de disponibilité ou une instance de cluster de basculement. Le pilote essaie de se connecter à la base de données sur le serveur principal [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] traite de l’instance en essayant de se connecter à tous les l’adresse IP. Lorsque vous vous connectez avec **MultiSubnetFailover = Yes**, le client tente de tentatives de connexion TCP plus rapidement que les intervalles de retransmission TCP par défaut du système d’exploitation. **MultiSubnetFailover=Yes** permet une reconnexion plus rapide après un basculement d’un groupe de disponibilité AlwaysOn ou d’une instance de cluster de basculement AlwaysOn. **MultiSubnetFailover = Yes** s’applique à la fois unique et à plusieurs sous-réseaux groupes de disponibilité et Instances de Cluster de basculement.  

Utilisez **MultiSubnetFailover=Yes** en cas de connexion à un écouteur de groupe de disponibilité ou à une instance de cluster de basculement. Dans le cas contraire, les performances de votre application peuvent se dégrader.

Notez les points suivants lors de la connexion à un serveur dans un groupe de disponibilité ou d’une Instance de Cluster de basculement :
  
-   Spécifiez **MultiSubnetFailover = Yes** pour améliorer les performances lors de la connexion à un sous-réseau unique ou un groupe de disponibilité de sous-réseaux multiples.

-   Spécifiez l’écouteur du groupe de disponibilité que le serveur dans votre chaîne de connexion.
  
-   Vous ne pouvez pas vous connecter à un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] instance configurée avec plus de 64 adresses IP.

-   Les deux [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] l’authentification ou l’authentification Kerberos peut être utilisée avec **MultiSubnetFailover = Yes** sans affecter le comportement de l’application.

-   Vous pouvez augmenter la valeur de **loginTimeout** pour tenir compte du temps de basculement et réduire les nouvelles tentatives de connexion de l’application.

-   Les transactions distribuées ne sont pas prises en charge.  
  
Si le routage en lecture seule n’est pas effectif, la connexion à un emplacement de réplica secondaire dans un groupe de disponibilité échoue dans les situations suivantes :  
  
1.  Si l'emplacement du réplica secondaire n'est pas configuré pour accepter des connexions.  
  
2.  Si une application utilise **ApplicationIntent=ReadWrite** et si l’emplacement de réplica secondaire est configuré pour un accès en lecture seule.  
  
Une connexion échoue si un réplica principal est configuré pour rejeter des charges de travail en lecture seule et si la chaîne de connexion contient **ApplicationIntent=ReadOnly**.  
  
## <a name="specifying-application-intent"></a>Spécification de l'intention d'application  
Quand **ApplicationIntent=ReadOnly**, le client demande une charge de travail en lecture lors de la connexion à une base de données prenant en charge AlwaysOn. Le serveur applique l’intention au moment de la connexion et pendant une instruction de base de données USE mais uniquement à une base de données AlwaysOn est activé.

Le mot clé **ApplicationIntent** ne fonctionne pas avec les bases de données en lecture seule existantes.  

Une base de données peut autoriser ou interdire les charges de travail en lecture sur la base de données AlwaysOn ciblée. (Utilisez la **ALLOW_CONNECTIONS** clause de la **PRIMARY_ROLE** et **SECONDARY_ROLE** [!INCLUDE[tsql](../../../includes/tsql_md.md)] instructions.)  
  
Le mot clé **ApplicationIntent** est utilisé pour activer le routage en lecture seule.  
  
## <a name="read-only-routing"></a>Routage en lecture seule  
Le routage en lecture seule est une fonctionnalité qui permet de garantir la disponibilité d'un réplica de base de données en lecture seule. Pour activer le routage en lecture seule :  
  
1.  Connectez-vous à un écouteur de groupe de disponibilité AlwaysOn.  
  
2.  Dans la chaîne de connexion, le mot clé **ApplicationIntent** doit avoir la valeur **ReadOnly**.  
  
3.  L’administrateur de base de données doit configurer le groupe de disponibilité pour activer le routage en lecture seule.  
  
Il est possible que plusieurs connexions utilisent le routage en lecture seule pour se connecter à différents réplicas en lecture seule. Les modifications apportées à la synchronisation de base de données ou à la configuration du routage du serveur peuvent entraîner des connexions clientes à différents réplicas en lecture seule. Pour vérifier que toutes les requêtes en lecture seule se connectent au même réplica en lecture seule, ne transmettez pas d’écouteur de groupe de disponibilité au mot clé de connexion **Server** . Au lieu de cela, spécifiez le nom de l'instance en lecture seule.  
  
Attendez-vous à des temps de connexion plus longs avec un routage en lecture seule qu’avec une connexion à la base de données principale. Par conséquent, augmentez le délai de connexion. Le routage en lecture seule se connecte d’abord à la base de données principale, puis recherche la meilleure base de données secondaire lisible disponible.  
  
## <a name="odbc-syntax"></a>Syntaxe ODBC

Prend en charge les deux mots de clés de la chaîne de connexion ODBC [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]:  
  
-   **ApplicationIntent**  
  
-   **MultiSubnetFailover**  
  
Pour plus d’informations sur les mots clés de chaîne de connexion ODBC, consultez [Utilisation de mots clés de chaîne de connexion avec SQL Server Native Client](http://msdn.microsoft.com/library/ms130822.aspx).  
  
Les attributs de connexion équivalentes sont :
  
-   **SQL_COPT_SS_APPLICATION_INTENT**  
  
-   **SQL_COPT_SS_MULTISUBNET_FAILOVER**  
  
Pour plus d’informations sur les attributs de connexion ODBC, consultez [SQLSetConnectAttr](http://msdn.microsoft.com/library/ms131709.aspx).  
  
Une application ODBC qui utilise [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)] peut utiliser une des deux fonctions pour établir la connexion :  
  
|Fonction| Description|  
|------------|---------------|  
|[SQLConnect, fonction](../../../odbc/reference/syntax/sqlconnect-function.md)|**SQLConnect** prend en charge les **ApplicationIntent** et **MultiSubnetFailover** via un attribut de connexion ou un nom de source de données (DSN).|  
|[SQLDriverConnect, fonction](../../../odbc/reference/syntax/sqldriverconnect-function.md)|**SQLDriverConnect** prend en charge **ApplicationIntent** et **MultiSubnetFailover** via DSN, mot clé de chaîne de connexion ou attribut de connexion.|
  
## <a name="see-also"></a>Voir aussi  

[Mots clés de chaîne de connexion et noms de source de données](../../../connect/odbc/linux-mac/connection-string-keywords-and-data-source-names-dsns.md)

[Instructions de programmation](../../../connect/odbc/linux-mac/programming-guidelines.md)

[Notes de publication](../../../connect/odbc/linux-mac/release-notes.md)  
