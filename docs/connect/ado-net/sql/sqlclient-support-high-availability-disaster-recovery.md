---
title: Prise en charge par SqlClient des fonctionnalités de haute disponibilité et de reprise d’activité
description: Décrit le support SqlClient pour des groupes de disponibilité de haute disponibilité et récupération d’urgence (AlwaysOn).
ms.date: 08/15/2019
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 841e5e1caf4594c519b44e5813688761838247b0
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80918748"
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a>Prise en charge par SqlClient des fonctionnalités de haute disponibilité et de reprise d’activité

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Cette rubrique présente le Fournisseur de données Microsoft SqlClient pour le support SQL Server de la haute disponibilité et de la récupération d’urgence -- groupes de disponibilité AlwaysOn.  La fonctionnalité Groupes de disponibilité AlwaysOn a été ajoutée à SQL Server 2012. Pour plus d’informations sur les groupes de disponibilité AlwaysOn, consultez la documentation en ligne de SQL Server.  
  
Vous pouvez à présent spécifier l’écouteur du groupe de disponibilité (haute disponibilité, reprise d’activité) ou une instance de cluster de basculement SQL Server 2012 dans la propriété de connexion. Si une application SqlClient est connectée à une base de données AlwaysOn sur laquelle un basculement est effectué, la connexion d’origine sera interrompue. L’application devra alors établir une nouvelle connexion pour poursuivre la tâche après le basculement.  
  
Si vous ne vous connectez pas à un écouteur du groupe de disponibilité ou à une instance de cluster de basculement SQL Server 2012, et si plusieurs adresses IP sont associées à un nom d’hôte, SqlClient itèrera de manière séquentielle au sein de toutes les adresses IP associées aux entrées DNS. Cette opération peut prendre du temps si la première adresse IP retournée par le serveur DNS n'est liée à aucune carte d'interface réseau (NIC). Lors de la connexion à un écouteur du groupe de disponibilité ou une instance de cluster de basculement SQL Server 2012, SqlClient tente d’établir des connexions à toutes les adresses IP en parallèle, et si une tentative de connexion réussit, le pilote ignore toutes les tentatives de connexion en attente.  
  
> [!NOTE]
>  L'augmentation du délai de connexion et l'implémentation de la logique de tentative de connexion augmente la probabilité qu'une application se connecte à un groupe de disponibilité. En raison du risque d’échec de connexion en cas de basculement, il est également nécessaire d’implémenter une logique de déclenchement de nouvelles tentatives de connexion, afin de multiplier les tentatives jusqu’à ce qu’une connexion soit établie.  
  
Les propriétés de connexion suivantes sont prises en charge dans le Fournisseur de données Microsoft SqlClient pour SQL Server :  
  
- `ApplicationIntent`  
  
- `MultiSubnetFailover`  
  
Vous pouvez modifier par programmation ces mots clés de chaîne de connexion avec :  
  
- <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  
  
## <a name="connecting-with-multisubnetfailover"></a>Connexion à MultiSubnetFailover  
Spécifiez toujours `MultiSubnetFailover=True` lors de la connexion à un écouteur du groupe de disponibilité SQL Server 2012 ou à une instance de cluster de basculement SQL Server 2012. `MultiSubnetFailover` permet un basculement plus rapide pour tous les groupes de disponibilité et l’instance de cluster de basculement dans SQL Server 2012, et réduit considérablement le temps de basculement pour les topologies AlwaysOn mono- ou multi-sous-réseaux. Lors d'un basculement de sous-réseaux multiples, le client tente les connexions en parallèle. Lors d’un basculement de sous-réseau, il retente de façon intensive la connexion TCP.  
  
La propriété de connexion `MultiSubnetFailover` indique que l’application est déployée dans un groupe de disponibilité ou une instance de cluster de basculement SQL Server 2012 et que SqlClient tente de se connecter à la base de données sur l’instance SQL Server principale quand vous essayez de vous connecter à toutes les adresses IP. Quand `MultiSubnetFailover=True` est spécifié dans le cadre d’une connexion, le client retente d’établir une connexion TCP plus rapidement que les intervalles de retransmission TCP par défaut du système d’exploitation. Cela permet une reconnexion plus rapide après le basculement d'un groupe de disponibilité AlwaysOn ou d'une instance de cluster de basculement AlwaysOn et s'applique aux groupes de disponibilité et aux instances de cluster de basculement uniques et à plusieurs sous-réseaux.  
  
Pour plus d’informations sur les mots clés de chaînes de connexion dans SqlClient, consultez <xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
La spécification de `MultiSubnetFailover=True` lors de la connexion à un élément autre qu’un écouteur du groupe de disponibilité ou une instance de cluster de basculement SQL Server 2012 peut provoquer une diminution des performances, et n’est pas prise en charge.  
  
Utilisez les instructions suivantes pour la connexion à un serveur dans un groupe de disponibilité ou dans une instance de cluster de basculement SQL Server 2012 :  
  
- Utilisez la propriété de connexion `MultiSubnetFailover` lors de la connexion à un seul réseau ou à plusieurs réseau car elle optimise les performances dans les deux cas de figure.  
  
- Pour vous connecter à un groupe de disponibilité, spécifiez l'écouteur du groupe de disponibilité en tant que serveur dans votre chaîne de connexion.  
  
- La connexion à une instance SQL Server configurée avec plus de 64 adresses IP provoque un échec de connexion.  
  
- Le comportement d’une application qui utilise la propriété de connexion `MultiSubnetFailover` n’est pas affecté en fonction du type d’authentification : authentification SQL Server, authentification Kerberos ou authentification Windows.  
  
- Augmentez la valeur de la propriété `Connect Timeout` pour permettre le basculement de serveur et réduire le nombre de tentatives de connexion d’une application.  
  
- Les transactions distribuées ne sont pas prises en charge.  
  
 Si le routage en lecture seule n’est pas appliqué, la connexion à un emplacement de réplica secondaire échoue dans les situations suivantes :  
  
- Si l'emplacement du réplica secondaire n'est pas configuré pour accepter des connexions.  
  
- Si une application utilise `ApplicationIntent=ReadWrite` (voir ci-dessous) et si l'emplacement de réplica secondaire est configuré pour un accès en lecture seule.  
  
<xref:Microsoft.Data.SqlClient.SqlDependency> n’est pas pris en charge sur les réplicas secondaires en lecture seule.  
  
Une connexion échoue si un réplica principal est configuré pour rejeter des charges de travail en lecture seule et si la chaîne de connexion contient `ApplicationIntent=ReadOnly`.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Mise à niveau pour utiliser des clusters multi-sous-réseaux à partir de la mise en miroir de bases de données  
Une erreur de connexion (<xref:System.ArgumentException>) se produit si les mots clés de connexion `MultiSubnetFailover` et `Failover Partner` sont présents dans la chaîne de connexion ou si `MultiSubnetFailover=True` et un protocole autre que TCP est utilisé. Une erreur (<xref:Microsoft.Data.SqlClient.SqlException>) se produit également si `MultiSubnetFailover` est utilisé et que SQL Server retourne une réponse de partenaire de basculement qui indique qu’il fait partie d’une paire de mise en miroir de bases de données.  
  
Si vous faites passer une application SqlClient qui utilise actuellement la mise en miroir de bases de données à un scénario multi-sous-réseau, vous devez supprimer la propriété de connexion `Failover Partner` et la remplacer par `MultiSubnetFailover` avec la valeur `True`, et remplacer le nom du serveur dans la chaîne de connexion par un écouteur du groupe de disponibilité. Si une chaîne de connexion utilise `Failover Partner` et `MultiSubnetFailover=True`, le pilote génère une erreur. Toutefois, si une chaîne de connexion utilise `Failover Partner` et `MultiSubnetFailover=False` (ou `ApplicationIntent=ReadWrite`), l'application utilise la mise en miroir de bases de données.  
  
Le pilote retourne une erreur si la mise en miroir de bases de données est utilisée pour la base de données principale au sein du groupe de disponibilité, et si `MultiSubnetFailover=True` est utilisé dans la chaîne de connexion qui établit une connexion avec une base de données principale au lieu d’un écouteur de groupe de disponibilité.  
  
## <a name="specifying-application-intent"></a>Spécification de l’intention d’application  
Lorsque `ApplicationIntent=ReadOnly`, le client demande une charge de travail en lecture lors de la connexion à une base de données prenant en charge AlwaysOn. Le serveur applique l'intention au moment de la connexion et pendant une instruction de base de données USE mais uniquement sur une base de données prenant en charge AlwaysOn.  
  
Le mot clé `ApplicationIntent` ne fonctionne pas avec les bases de données en lecture seule existantes.  
  
Une base de données peut autoriser ou interdire les charges de travail en lecture sur la base de données AlwaysOn ciblée. (Pour cela, utilisez la clause `ALLOW_CONNECTIONS` des instructions SQL-Transact `PRIMARY_ROLE` et `SECONDARY_ROLE`.)  
  
Le mot clé `ApplicationIntent` est utilisé pour activer le routage en lecture seule.  
  
## <a name="read-only-routing"></a>Routage en lecture seule  
Le routage en lecture seule est une fonctionnalité qui peut garantir la disponibilité d'un réplica en lecture seule d'une base de données. Pour activer le routage en lecture seule :  
  
- Vous devez vous connecter à un écouteur du groupe de disponibilité Always On.  
  
- Le mot clé de chaîne de connexion `ApplicationIntent` doit avoir la valeur `ReadOnly`.  
  
- Le groupe de disponibilité doit être configuré par l'administrateur de base de données pour activer le routage en lecture seule.  
  
Il est possible que plusieurs connexions utilisant le routage en lecture seule ne se connectent pas toutes au même réplica en lecture seule. Les modifications apportées à la synchronisation de base de données ou à la configuration du routage du serveur peuvent entraîner des connexions clientes à différents réplicas en lecture seule. Pour vérifier que toutes les demandes en lecture seule se connectent au même réplica en lecture seule, ne transmettez pas d'écouteur du groupe de disponibilité au mot clé de chaîne de connexion `Data Source`. Au lieu de cela, spécifiez le nom de l'instance en lecture seule.  
  
Le routage en lecture seule peut prendre plus de temps que la connexion au réplica primaire car le routage en lecture seule se connecte d'abord au réplica primaire, puis recherche le meilleur réplica secondaire lisible disponible. Pour cette raison, vous devez augmenter le délai de connexion.  
  
## <a name="next-steps"></a>Étapes suivantes
- [Fonctionnalités de SQL Server et ADO.NET](sql-server-features-adonet.md)
