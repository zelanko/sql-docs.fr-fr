---
title: "MODIFIER la base de données de base de données mise en miroir (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- witness [SQL Server], establishing
- manual failover [SQL Server]
- ALTER DATABASE statement, database mirroring
- database mirroring [SQL Server], Transact-SQL
ms.assetid: 27a032ef-1cf6-4959-8e67-03d28c4b3465
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 96ac469df9660e29c0394226cf7199e451df9d8c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-transact-sql-database-mirroring"></a>ALTER DATABASE (Transact-SQL) base de données mise en miroir 
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez plutôt [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].  
  
 Contrôle la mise en miroir d'une base de données. Les valeurs spécifiées avec les options de mise en miroir de bases de données s'appliquent aux deux copies de la base de données et à l'ensemble de la session de mise en miroir de bases de données. Seul \<database_mirroring_option > est autorisée par instruction ALTER DATABASE.  
  
> [!NOTE]  
>  Nous vous recommandons de configurer de base de données mise en miroir durant les heures creuses, car la configuration peut affecter les performances.  
  
 Pour plus d’options ALTER DATABASE, consultez [ALTER DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql.md). Pour plus d’options ALTER DATABASE SET, consultez [Options ALTER DATABASE SET &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ALTER DATABASE database_name   
SET { <partner_option> | <witness_option> }  
  <partner_option> ::=  
    PARTNER { = 'partner_server'   
            | FAILOVER   
            | FORCE_SERVICE_ALLOW_DATA_LOSS  
            | OFF  
            | RESUME   
            | SAFETY { FULL | OFF }  
            | SUSPEND   
            | TIMEOUT integer  
            }  
  <witness_option> ::=  
    WITNESS { = 'witness_server'   
            | OFF   
            }  
  
```  
  
## <a name="arguments"></a>Arguments  
  
> [!IMPORTANT]  
>  Une commande SET PARTNER ou SET WITNESS peut se dérouler normalement lorsqu'elle est entrée, mais échouer ensuite.  
  
> [!NOTE]  
>  Les options de mise en miroir de bases de données ALTER DATABASE ne sont pas disponibles pour une base de données à relation contenant-contenu.  
  
 *database_name*  
 Nom de la base de données à modifier.  
  
 PARTENAIRE \<partner_option >  
 Contrôle les propriétés de base de données qui définissent les partenaires de basculement d'une session de mise en miroir de bases de données ainsi que leur comportement. Certaines options de SET PARTNER peuvent être définies sur l'un et l'autre des serveurs partenaires tandis que d'autres sont réservées au serveur principal ou au serveur miroir. Pour plus d'informations, consultez les options PARTNER individuelles décrites ci-dessous. Une clause SET PARTNER affecte les deux copies de la base de données, indépendamment du serveur partenaire sur lequel elle est spécifiée.  
  
 Pour exécuter une instruction SET PARTNER, le paramètre STATE des points de terminaison des deux partenaires doit avoir la valeur STARTED. Notez par ailleurs que l'option ROLE du point de terminaison de mise en miroir de chaque instance de serveur partenaire doit avoir la valeur PARTNER ou ALL. Pour plus d’informations sur la spécification d’un point de terminaison, consultez [créer une base de données mise en miroir de point de terminaison pour l’authentification Windows &#40; Transact-SQL &#41; ](../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md). Pour connaître le rôle et l'état du point de terminaison de mise en miroir de bases de données d'une instance de serveur, utilisez l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante sur cette instance :  
  
```  
SELECT role_desc, state_desc FROM sys.database_mirroring_endpoints  
```  
  
 **\<partner_option > :: =**  
  
> [!NOTE]  
>  Seul \<partner_option > est autorisée par clause SET PARTNER.  
  
 **'** *serveur_partenaire* **'**  
 Spécifie l'adresse réseau de serveur d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sélectionnée comme partenaire de basculement dans une nouvelle session de mise en miroir de bases de données. Chaque session requiert deux serveurs partenaires : l'un démarre comme serveur principal et l'autre démarre comme serveur miroir. Les deux serveurs partenaires doivent de préférence résider sur des ordinateurs différents.  
  
 Cette option est spécifiée une seule fois par session sur chaque serveur partenaire. Lancer une session de mise en miroir de base de données requiert deux ALTER DATABASE *base de données* SET PARTNER **='***serveur_partenaire***'** instructions. Leur ordre est important. Tout d’abord, se connecter au serveur miroir et spécifiez l’instance de serveur principal en tant que *serveur_partenaire* (SET PARTNER **='***principal_server***'**). Ensuite, vous connecter au serveur principal et spécifiez l’instance de serveur miroir en tant que *serveur_partenaire* (SET PARTNER **='***mirror_server***'**) ; cette opération démarre une session entre ces deux serveurs partenaires de mise en miroir de base de données. Pour plus d'informations, consultez [Configuration de la mise en miroir d’une base de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md).  
  
 La valeur de *serveur_partenaire* est une adresse réseau du serveur. La syntaxe est la suivante :  
  
 TCP**://***\<adresse-système>***:***\<port>*  
  
 où  
  
-   *\<adresse-système >* est une chaîne, comme un nom système, un nom de domaine complet ou une adresse IP, qui identifie sans ambiguïté le système d’ordinateur de destination.  
  
-   *\<port >* est un numéro de port qui est associé au point de terminaison de mise en miroir de l’instance de serveur partenaire.  
  
 Pour plus d’informations, consultez [Spécifier une adresse réseau de serveur &#40;mise en miroir de bases de données&#41;](../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md).  
  
 L’exemple suivant illustre la SET PARTNER **='***serveur_partenaire***'** clause :  
  
```  
'TCP://MYSERVER.mydomain.Adventure-Works.com:7777'  
```  
  
> [!IMPORTANT]  
>  Si une session est configurée à l'aide de l'instruction ALTER DATABASE au lieu de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], la session est définie par défaut avec l'option de sécurité la plus élevée pour les transactions (SAFETY a la valeur FULL) et s'exécute en mode haute sécurité sans basculement automatique. Pour autoriser le basculement automatique, configurez un témoin et pour le mode hautes performances, désactivez la sécurité des transactions (SAFETY OFF).  
  
 FAILOVER  
 Bascule manuellement le serveur principal vers le serveur miroir. Vous ne pouvez spécifier l'option FAILOVER que sur le serveur principal. Cette option est valide dans le seul cas où le paramètre SAFETY a la valeur FULL (valeur par défaut).  
  
 L’option FAILOVER requiert **master** comme contexte de base de données.  
  
 FORCE_SERVICE_ALLOW_DATA_LOSS  
 Force le service de base de données vers la base de données miroir après la défaillance du serveur principal avec la base de données dans un état non synchronisé ou dans un état synchronisé si le basculement automatique ne se produit pas.  
  
 Il est vivement conseillé de ne forcer le service que si le serveur principal n'est plus en cours d'exécution. Sinon, certains clients peuvent continuer à accéder la base de données principale d'origine au lieu de la nouvelle base de données principale.  
  
 FORCE_SERVICE_ALLOW_DATA_LOSS est disponible uniquement sur le serveur miroir et seulement dans les circonstances suivantes :  
  
-   Le serveur principal est hors service.  
  
-   WITNESS a la valeur OFF ou le témoin est connecté au serveur miroir.  
  
 Forcez le service uniquement si vous pouvez prendre le risque de perdre des données afin de restaurer immédiatement le service à la base de données.  
  
 Lorsque vous forcez le service, la session est interrompue ; toutes les données sont conservées temporairement dans la base de données principale d'origine. Une fois que le principal d'origine est en service et en mesure de communiquer avec le nouveau serveur principal, l'administrateur de base de données peut réactiver le service. Lors d'une reprise de la session, tous les enregistrements de journal non envoyés et les mises à jour correspondantes sont perdus.  
  
 OFF  
 Supprime une session de mise en miroir de bases de données et supprime la mise en miroir de la base de données. Vous pouvez définir la valeur OFF sur l'un et l'autre des serveurs partenaires. Pour plus d’informations, sur l’impact de la suppression de la mise en miroir, consultez [suppression de la mise en miroir de la base de données &#40; SQL Server &#41; ](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md).  
  
 RESUME  
 Reprend une session de mise en miroir de bases de données interrompue. Vous ne pouvez spécifier l'option RESUME que sur le serveur principal.  
  
 SAFETY { FULL | OFF }  
 Définit le niveau de sécurité des transactions. Vous ne pouvez spécifier l'option SAFETY que sur le serveur principal.  
  
 La valeur par défaut est FULL. Avec la sécurité complète, la session de mise en miroir de base de données exécute de façon synchrone (dans *mode haute sécurité*). Si la sécurité est définie sur OFF, la session de mise en miroir de base de données s’exécute de façon asynchrone (dans *mode hautes performances*).  
  
 Le comportement du mode haute sécurité dépend en partie du témoin :  
  
-   Lorsque SAFETY a la valeur FULL et qu'un témoin est défini pour la session, la session s'exécute en mode haute sécurité avec basculement automatique. En cas de perte du serveur principal, la session bascule automatiquement si la base de données est synchronisée et si l'instance du serveur miroir et le témoin sont toujours connectés l'un à l'autre (en d'autres termes, ils ont un quorum). Pour plus d’informations, consultez [Quorum : effets d’un témoin sur la disponibilité de la base de données &#40;mise en miroir de bases de données&#41;](../../database-engine/database-mirroring/quorum-how-a-witness-affects-database-availability-database-mirroring.md).  
  
     Si un témoin est défini pour la session mais qu'il est déconnecté à ce moment-là, la perte du serveur miroir provoque l'arrêt du serveur principal.  
  
-   Lorsque SAFETY prend la valeur FULL et que le témoin a la valeur OFF, la session s'exécute en mode haute sécurité sans basculement automatique. L'arrêt éventuel de l'instance de serveur miroir n'a aucune incidence sur l'instance de serveur principal. Par contre, si l'instance de serveur principal s'arrête, le service peut être forcé (avec perte de données, le cas échéant) sur l'instance de serveur miroir.  
  
 Si SAFETY a la valeur OFF, la session s'exécute en mode hautes performances et les basculements manuel et automatique ne sont pas pris en charge. Toutefois, les problèmes survenant sur le miroir n'ont pas d'incidence sur l'instance de serveur principal qui, si elle s'arrête, peut être, si nécessaire, relayée par l'instance de serveur miroir dont vous forcez le service (avec une perte possible des données). Pour cela, WITNESS doit avoir la valeur OFF, ou le témoin être connecté à ce moment-là au miroir. Pour plus d'informations sur le service forcé, consultez « FORCE_SERVICE_ALLOW_DATA_LOSS » plus haut dans cette section.  
  
> [!IMPORTANT]  
>  Le mode hautes performances n'a pas été prévu pour utiliser un témoin. Toutefois, il est vivement recommandé de vérifier que WITNESS a la valeur OFF chaque fois que l'option SAFETY est désactivée (OFF).  
  
 SUSPEND  
 Suspend une session de mise en miroir de bases de données.  
  
 Vous pouvez définir la valeur SUSPEND sur l'un et l'autre des serveurs partenaires.  
  
 Délai d’attente *entier*  
 Spécifie le délai d'attente en secondes. Le délai d'attente est la durée maximale pendant laquelle une instance de serveur attend de recevoir un message PING d'une autre instance de la session de mise en miroir avant de considérer que cette dernière est déconnectée.  
  
 Vous ne pouvez spécifier l'option TIMEOUT que sur le serveur principal. Si vous ne précisez pas de valeur, le délai défini par défaut est 10 secondes. Si vous spécifiez 5 ou une valeur supérieure, le délai d'attente correspond au nombre de secondes indiqué. Si vous spécifiez une valeur comprise entre 0 et 4 secondes, le délai d'attente est automatiquement de 5 secondes.  
  
> [!IMPORTANT]  
>  Le temps d'attente recommandé est de 10 secondes minimum. En définissant une valeur inférieure à 10 secondes, vous créez la possibilité qu'un système surchargé soit à court de PING et qu'il déclare à tort une défaillance.  
  
 Pour plus d’informations, consultez [Défaillances possibles pendant la mise en miroir d’une base de données](../../database-engine/database-mirroring/possible-failures-during-database-mirroring.md).  
  
 TÉMOIN \<witness_option >  
 Contrôle les propriétés de base de données qui définissent un témoin de mise en miroir de bases de données. Une clause SET WITNESS affecte les deux copies de la base de données, mais vous ne pouvez la spécifier que sur le serveur principal. Si un témoin est défini pour une session, le quorum est requis pour traiter la base de données, quel que soit le paramètre de sécurité ; Pour plus d’informations, consultez [Quorum : effets d’un témoin affecte la base de données de disponibilité &#40; mise en miroir de base de données &#41;](../../database-engine/database-mirroring/quorum-how-a-witness-affects-database-availability-database-mirroring.md).  
  
 Les partenaires de basculement et témoins doivent de préférence résider sur des ordinateurs différents. Pour plus d’informations sur le serveur témoin, consultez [témoin de mise en miroir de base de données](../../database-engine/database-mirroring/database-mirroring-witness.md).  
  
 Pour exécuter une instruction SET WITNESS, l'option STATE des points de terminaison des instances de serveur principal et de serveur témoin doit avoir la valeur STARTED. Notez par ailleurs que l'option ROLE du point de terminaison de mise en miroir de bases de données d'une instance de serveur témoin doit avoir la valeur WITNESS ou ALL. Pour plus d’informations sur la spécification d’un point de terminaison, consultez [la terminaison de mise en miroir de base de données &#40; SQL Server &#41; ](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md).  
  
 Pour connaître le rôle et l'état du point de terminaison de mise en miroir de bases de données d'une instance de serveur, utilisez l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante sur cette instance :  
  
```  
SELECT role_desc, state_desc FROM sys.database_mirroring_endpoints  
```  
  
> [!NOTE]  
>  Les propriétés de base de données ne peuvent pas être définies sur le témoin.  
  
 **\<witness_option > :: =**  
  
> [!NOTE]  
>  Seul \<witness_option > est autorisée par clause SET WITNESS.  
  
 **'** *witness_server* **'**  
 Spécifie une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui doit servir de serveur témoin pour une session de mise en miroir de bases de données. Vous ne pouvez spécifier d'instructions SET WITNESS que sur le serveur principal.  
  
 Dans une commande SET WITNESS **='***witness_server***'** instruction, la syntaxe de *witness_server* est identique à la syntaxe de *serveur_partenaire*.  
  
 OFF  
 Supprime le témoin d'une session de mise en miroir de bases de données. Si le témoin a la valeur OFF, le basculement automatique est désactivé. Lorsque la base de données est configurée avec l'option FULL SAFETY et le témoin avec la valeur OFF, une défaillance du serveur miroir conduit le serveur principal à rendre la base de données inaccessible.  
  
## <a name="remarks"></a>Notes  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-a-database-mirroring-session-with-a-witness"></a>A. Création d'une session de mise en miroir de bases de données avec un témoin  
 Pour configurer la mise en miroir de bases de données avec un témoin, vous devez configurer la sécurité, préparer la base de données miroir et utiliser ALTER DATABASE pour définir les serveurs partenaires. Pour obtenir un exemple de la procédure d’installation complète, consultez [paramètre de base de données mise en miroir &#40; SQL Server &#41; ](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md).  
  
### <a name="b-manually-failing-over-a-database-mirroring-session"></a>B. Basculement manuel d'une session de mise en miroir de bases de données  
 Le basculement manuel peut être débuté par l'un ou l'autre des serveurs partenaires de mise en miroir de bases de données. Avant le basculement, assurez-vous que le serveur considéré comme serveur principal est effectivement le serveur principal. Par exemple, pour la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], sur l'instance de serveur représentant, selon vous, le serveur principal, exécutez la requête suivante :  
  
```  
SELECT db.name, m.mirroring_role_desc   
FROM sys.database_mirroring m   
JOIN sys.databases db  
ON db.database_id = m.database_id  
WHERE db.name = N'AdventureWorks2012';   
GO  
```  
  
 Si l'instance de serveur est effectivement le principal, la valeur de `mirroring_role_desc` est `Principal`. Si cette instance de serveur est le serveur miroir, l'instruction `SELECT` retourne `Mirror`.  
  
 L'exemple suivant suppose que le serveur est le principal actuel.  
  
1.  Basculez manuellement vers le serveur partenaire de mise en miroir de bases de données :  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER FAILOVER;  
    GO  
    ```  
  
2.  Pour vérifier les résultats du basculement sur le nouveau miroir, exécutez la requête suivante :  
  
    ```  
    SELECT db.name, m.mirroring_role_desc   
    FROM sys.database_mirroring m   
    JOIN sys.databases db  
    ON db.database_id = m.database_id  
    WHERE db.name = N'AdventureWorks2012';   
    GO  
    ```  
  
     La valeur actuelle de `mirroring_role_desc` est désormais `Mirror`.  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [Sys.database_mirroring_witnesses &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)  
  
  

