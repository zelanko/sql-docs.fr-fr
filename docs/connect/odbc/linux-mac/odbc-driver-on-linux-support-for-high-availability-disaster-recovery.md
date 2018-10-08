---
title: Pilote ODBC sur Linux et macOS - Haute disponibilité et reprise d’activité | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: fa656c5b-a935-40bf-bc20-e517ca5cd0ba
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5922753b28c401312f917ce662b56c7378634a77
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687038"
---
# <a name="odbc-driver-on-linux-and-macos-support-for-high-availability-and-disaster-recovery"></a>Pilote ODBC sur Linux et macOS - Haute disponibilité et reprise d’activité
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Les pilotes ODBC pour la prise en charge de Linux et macOS [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]. Pour plus d’informations sur [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)], consultez :  
  
-   [Écouteurs de groupe de disponibilité, connectivité client et basculement d’application (SQL Server)](http://msdn.microsoft.com/library/hh213417.aspx)  
  
-   [Création et configuration des groupes de disponibilité (SQL Server)](http://msdn.microsoft.com/library/ff878265.aspx)  
  
-   [Clustering de basculement et groupes de disponibilité AlwaysOn (SQL Server)](http://msdn.microsoft.com/library/ff929171.aspx)  
  
-   [Secondaires actifs : réplicas secondaires lisibles (groupes de disponibilité d’AlwaysOn)](http://msdn.microsoft.com/library/ff878253.aspx)  
  
Vous pouvez spécifier l’écouteur d’un groupe de disponibilité donné dans la chaîne de connexion. Si une application ODBC sur Linux ou macOS est connectée à une base de données dans un groupe de disponibilité qui bascule, la connexion d’origine est rompue et l’application doit ouvrir une nouvelle connexion pour reprendre le travail après le basculement.

Les pilotes ODBC sur Linux et macOS itérer séquentiellement dans toutes les adresses IP associés à un nom d’hôte DNS si vous n’êtes pas connecté à un écouteur de groupe de disponibilité, et plusieurs adresses IP sont associées avec le nom d’hôte.

Si la première adresse IP retournée du serveur DNS n’est pas connectable, ces itérations peuvent prendre du temps. Quand vous vous connectez à un écouteur de groupe de disponibilité, le pilote tente d’établir des connexions à toutes les adresses IP en parallèle. Si une tentative de connexion réussit, le pilote ignore toutes les tentatives de connexion en attente.

> [!NOTE]  
> En raison du risque d’échec de connexion en cas de basculement d’un groupe de disponibilité, implémentez une logique de déclenchement de nouvelles tentatives de connexion et multipliez les tentatives jusqu’à ce qu’une connexion soit établie. L’augmentation du délai de connexion et l’implémentation de la logique déclenchement de nouvelles tentatives de connexion augmentent le risque de connexion à un groupe de disponibilité.

## <a name="connecting-with-multisubnetfailover"></a>Connexion à MultiSubnetFailover

Spécifiez toujours **MultiSubnetFailover=Yes** en cas de connexion à un écouteur de groupe de disponibilité [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ou à une instance de cluster de basculement [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]. **MultiSubnetFailover** permet un basculement plus rapide pour tous les groupes de disponibilité et l’instance de cluster de basculement dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]. **MultiSubnetFailover** réduit également sensiblement le temps de basculement pour les topologies AlwaysOn de sous-réseaux uniques et multiples. Pendant un basculement de sous-réseaux multiples, le client tente des connexions en parallèle. Lors d’un basculement de sous-réseau, le pilote retente agressivement la connexion TCP.

La propriété de connexion **MultiSubnetFailover** indique que l’application est déployée dans un groupe de disponibilité ou une instance de cluster de basculement. Le pilote tente de se connecter à la base de données sur l’instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] principale en essayant de se connecter à toutes les adresses IP. Dans une connexion avec **MultiSubnetFailover=Yes**, le client retente la connexion TCP à un intervalle plus court que l’intervalle de retransmission TCP par défaut du système d’exploitation. **MultiSubnetFailover=Yes** permet une reconnexion plus rapide après un basculement d’un groupe de disponibilité AlwaysOn ou d’une instance de cluster de basculement AlwaysOn. **MultiSubnetFailover=Yes** s’applique à la fois aux groupes de disponibilité de sous-réseaux et aux instances de cluster de basculement uniques et multiples.  

Utilisez **MultiSubnetFailover=Yes** en cas de connexion à un écouteur de groupe de disponibilité ou à une instance de cluster de basculement. Sinon, les performances de votre application peuvent être impactées négativement.

Notez ceci lors de la connexion à un serveur dans un groupe de disponibilité ou dans une instance de cluster de basculement :
  
-   Spécifiez **MultiSubnetFailover = Yes** pour améliorer les performances lors de la connexion à un sous-réseau unique ou un groupe de disponibilité de sous-réseaux multiples.

-   Spécifier l’écouteur de groupe de disponibilité du groupe de disponibilité que le serveur dans votre chaîne de connexion.
  
-   Vous ne pouvez pas vous connecter à une instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] configurée avec plus de 64 adresses IP.

-   Les deux [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] l’authentification ou l’authentification Kerberos peut être utilisée avec **MultiSubnetFailover = Yes** sans affecter le comportement de l’application.

-   Vous pouvez augmenter la valeur de **loginTimeout** pour tenir compte du temps de basculement et réduire les nouvelles tentatives de connexion de l’application.

-   Les transactions distribuées ne sont pas prises en charge.  
  
Si le routage en lecture seule n’est pas effectif, la connexion à un emplacement de réplica secondaire dans un groupe de disponibilité échoue dans les situations suivantes :  
  
1.  Si l'emplacement du réplica secondaire n'est pas configuré pour accepter des connexions.  
  
2.  Si une application utilise **ApplicationIntent=ReadWrite** et si l’emplacement de réplica secondaire est configuré pour un accès en lecture seule.  
  
Une connexion échoue si un réplica principal est configuré pour rejeter des charges de travail en lecture seule et si la chaîne de connexion contient **ApplicationIntent=ReadOnly**.  


[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


## <a name="odbc-syntax"></a>Syntaxe ODBC

Deux mots clés de chaîne de connexion ODBC prennent en charge [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)] :  
  
-   **ApplicationIntent**  
  
-   **MultiSubnetFailover**  
  
Pour plus d’informations sur les mots clés de chaîne de connexion ODBC, consultez [Utilisation de mots clés de chaîne de connexion avec SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
Les attributs de connexion équivalentes sont :
  
-   **SQL_COPT_SS_APPLICATION_INTENT**  
  
-   **SQL_COPT_SS_MULTISUBNET_FAILOVER**  
  
Pour plus d’informations sur les attributs de connexion ODBC, consultez [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
Une application qui utilise [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)] peut utiliser une des deux fonctions pour établir la connexion :  
  
|Fonction|Description|  
|------------|---------------|  
|[SQLConnect, fonction](../../../odbc/reference/syntax/sqlconnect-function.md)|**SQLConnect** prend en charge **ApplicationIntent** et **MultiSubnetFailover** via un nom de source de données ou un attribut de connexion.|  
|[SQLDriverConnect, fonction](../../../odbc/reference/syntax/sqldriverconnect-function.md)|**SQLDriverConnect** prend en charge **ApplicationIntent** et **MultiSubnetFailover** via DSN, un mot clé de chaîne de connexion ou un attribut de connexion.|
  
## <a name="see-also"></a> Voir aussi  

[Mots clés de chaîne de connexion et noms de source de données](../../../connect/odbc/linux-mac/connection-string-keywords-and-data-source-names-dsns.md)

[Instructions de programmation](../../../connect/odbc/linux-mac/programming-guidelines.md)

[Notes de publication](../../../connect/odbc/linux-mac/release-notes.md)  
