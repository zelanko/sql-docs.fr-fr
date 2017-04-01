---
title: "R&#233;plication vers une base de donn&#233;es SQL | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Réplication de base de données SQL"
  - "réplication, base de données SQL"
ms.assetid: e8484da7-495f-4dac-b38e-bcdc4691f9fa
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# R&#233;plication vers une base de donn&#233;es SQL
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la réplication peut être configurée pour [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)].  
  
 **Configurations prises en charge :**  
  
-   Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en cours d’exécution en local ou à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en cours d’exécution dans une machine virtuelle dans le cloud. Pour plus d’informations, consultez [Vue d’ensemble de SQL Server sur les machines virtuelles Azure](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/).  
  
-   [!INCLUDE[ssSDS](../../includes/sssds-md.md)] doit être un abonné par émission de données d’un serveur de publication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   La base de données de distribution et les agents de réplication ne peut pas être placés sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
-   Seules les réplications d’instantané et les réplications transactionnelles monodirectionnelles sont prises en charge. Les réplications transactionnelles d’égal à égal et les réplications de fusion ne sont pas prises en charge.  
  
## Versions  
 Le serveur de publication et le serveur de distribution doivent exécuter l’une des versions suivantes ou une version ultérieure :  
  
-   [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP1 CU3  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] RTM CU10  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 CU8  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] attendu pour SP3  
  
 Tente de configurer la réplication à l’aide d’une version antérieure peut provoquer erreur numéro MSSQL_REPL20084 (le processus pas pu se connecter à l’abonné.) et MSSQL_REPL40532 (Impossible d’ouvrir le serveur \< nom> demandée par la connexion. The login failed. (Impossible d’ouvrir le serveur <nom> requis pour la connexion. La connexion a échoué.)).  
  
 l’abonné [!INCLUDE[ssSDS](../../includes/sssds-md.md)] doit exécuter la version V12 ou une version ultérieure et peut être situé dans n’importe quelle région.  
  
 Pour utiliser toutes les fonctionnalités de [!INCLUDE[ssSDS](../../includes/sssds-md.md)] vous devez utiliser les dernières versions de [SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx) et [SQL Server Data Tools](https://msdn.microsoft.com/library/mt204009.aspx).  
  
## Notes  
 La réplication peut être configurée à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou en exécutant des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] sur le serveur de publication. Vous ne pouvez pas configurer la réplication à l’aide du portail [!INCLUDE[ssSDS](../../includes/sssds-md.md)] .  
  
 La réplication peut uniquement utiliser des connexions d’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour se connecter à [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 La table répliquée doit disposer d’une clé primaire.  
  
 Vous devez disposer d’un abonnement Azure et de [!INCLUDE[ssSDS](../../includes/sssds-md.md)] V12.  
  
 Une seule publication sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut prendre en charge à la fois [!INCLUDE[ssSDS](../../includes/sssds-md.md)] et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (local et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans une machine virtuelle) abonnés.  
  
 Gestion de la réplication, surveillance et résolution des problèmes doivent être effectuée à partir du site [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Seuls les abonnements par émission de données à [!INCLUDE[ssSDS](../../includes/sssds-md.md)] sont pris en charge.  
  
 Seulement `@subscriber_type = 0` est pris en charge dans **sp_addsubscription** pour la base de données SQL.  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ne prend pas en charge la réplication bidirectionnelle, immédiate, mettre à jour ou pair à pair.  
  
## Architecture de réplication  
 ![replication-to-sql-database](../../relational-databases/replication/media/replication-to-sql-database.png "replication-to-sql-database")  
  
## Scénarios  
  
#### Scénario de réplication classique  
  
1.  Créer une publication de réplication transactionnelle dans un local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données.  
  
2.  Dans les locaux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utiliser le **Assistant Nouvel abonnement** ou [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions pour créer une campagne d’abonnement [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
3.  Le jeu de données initial est généralement un instantané créé par l’Agent d’instantané puis distribué et appliqué par l’Agent de distribution. Le jeu de données initial peut être fourni par une sauvegarde ou un autre moyen, par exemple [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
#### Scénario de migration de données  
  
1.  Utilisez la réplication transactionnelle pour répliquer des données depuis un site local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] une base de données [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
2.  Rediriger les applications clientes ou de niveau intermédiaire pour mettre à jour le [!INCLUDE[ssSDS](../../includes/sssds-md.md)] copie.  
  
3.  Arrêtez la mise à jour de la version [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la table et supprimez la publication.  
  
## Limitations  
 Les options suivantes ne sont pas prises en charge pour les abonnements [!INCLUDE[ssSDS](../../includes/sssds-md.md)] :  
  
-   Copier l’association de groupes de fichiers  
  
-   Copier les schémas de partition de table  
  
-   Copier les schémas de partition d’index  
  
-   Copier les statistiques définies par l’utilisateur  
  
-   Copier les liaisons par défaut  
  
-   Copier les liaisons de règle  
  
-   Copier les index de texte intégral  
  
-   Copier le schéma XSD XML  
  
-   Copier les index XML  
  
-   Copier les autorisations  
  
-   Copier les index spatiaux  
  
-   Copier les index filtrés  
  
-   Copier l’attribut de compression de données  
  
-   Copier l’attribut de colonne éparse  
  
-   Convertir filestream en types de données MAX  
  
-   Convertir hierarchyId en types de données MAX  
  
-   Convertir le type spatial en types de données MAX  
  
-   Copier les propriétés étendues  
  
-   Copier les autorisations  
  
 Limitations à déterminer :  
  
-   Copier le classement  
  
-   Exécution de la procédure stockée dans une transaction sérialisée  
  
## Exemples  
 Créer une publication et un abonnement par émission de données. Pour plus d'informations, consultez :  
  
-   [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)  
  
-   [Créer un abonnement Push](../../relational-databases/replication/create-a-push-subscription.md) à l’aide de la [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] nom du serveur logique en tant que l’abonné (par exemple **N'azuresqldbdns.database.windows.net'**) et le [!INCLUDE[ssSDS](../../includes/sssds-md.md)] nom de la base de données de destination (par exemple **AdventureWorks**).  
  
## Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Types de réplication](../../relational-databases/replication/types-of-replication.md)   
 [Analyse & #40 ; Réplication & #41 ;](../../relational-databases/replication/monitor/monitoring-replication.md)   
 [Initialiser un abonnement](../../relational-databases/replication/initialize-a-subscription.md)  
  
  