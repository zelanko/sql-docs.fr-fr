---
title: "Abonn&#233;s non-SQL&#160;Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "abonnements [réplication SQL Server], abonnés non-SQL Server"
  - "sources de données hétérogènes, abonnés non-SQL Server"
  - "sources de données hétérogènes"
  - "réplication de bases de données hétérogènes, abonnés non-SQL Server"
  - "abonnés non-SQL Server, à propos"
  - "abonnés hétérogènes"
  - "abonnés hétérogènes, à propos"
  - "abonnés [réplication SQL Server], abonnés non-SQL Server"
  - "Abonnés non-SQL Server"
ms.assetid: 831e7586-2949-4b9b-a2f3-7b0b699b23ff
caps.latest.revision: 55
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 55
---
# Abonn&#233;s non-SQL&#160;Server
  Les abonnés non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] suivants peuvent s'abonner aux publications d'instantané et transactionnelle à l'aide d'abonnements par envoi de données (push). Les abonnements sont pris en charge pour les deux versions les plus récentes de chaque base de données listée, à l'aide de la version la plus récente du fournisseur OLE DB listé.  
  
 La réplication hétérogène sur les abonnés non SQL Server est déconseillée. La publication Oracle est déconseillée. Pour déplacer des données, créez des solutions à l'aide de la Capture de données modifiées et [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
|Base de données|Système d'exploitation|Fournisseur|  
|--------------|----------------------|--------------|  
|Oracle|Toute plateforme prenant en charge Oracle|Fournisseur OLE DB Oracle (fourni par Oracle)|  
|IBM DB2|MVS, AS400, Unix, Linux, Windows sauf 9.x|Fournisseur OLE DB du serveur HIS Microsoft (Host Integration Server)|  
  
 Pour plus d’informations sur la création des abonnements à Oracle et IBM DB2, consultez [abonnés Oracle](../../../relational-databases/replication/non-sql/oracle-subscribers.md) et [des abonnés IBM DB2](../../../relational-databases/replication/non-sql/ibm-db2-subscribers.md).  
  
## Règles des abonnés non-SQL Server  
 Retenez les règles suivantes lors de la réplication sur des abonnés non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
### Considérations générales  
  
-   La réplication prend en charge la publication des tables et des vues indexées vers des Abonnées non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (les vues indexées ne peuvent pas être répliquées en tant que telles).  
  
-   Lorsque la création d’une publication dans l’Assistant Nouvelle Publication et puis l’activer pour non abonnés non-SQL Server à l’aide de la boîte de dialogue Propriétés de la Publication, le propriétaire de tous les objets dans la base de données d’abonnement n’est pas spécifié pour les non -[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] abonnés, tandis que pour [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] abonnés, il est défini pour le propriétaire de l’objet correspondant dans la base de données de publication.  
  
-   Si une publication a des abonnés [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], la publication doit être activée pour les abonnés non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avant qu'un abonnement aux abonnés [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne soit créé.  
  
-   Par défaut, les scripts générés par l'Agent d'instantané pour les abonnés non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilisent des identificateurs sans guillemets dans la syntaxe CREATE TABLE. Ainsi, une table publiée nommée « test » est répliquée comme « TEST ». Pour utiliser la même casse que la table dans la base de données de publication, utilisez le **- QuotedIdentifier** paramètre pour l’Agent de Distribution. Le **- QuotedIdentifier** paramètre doit également être utilisé si les noms d’objet publié (tels que des tables, colonnes et contraintes) comportent des espaces ou des mots qui sont des mots réservés dans la version de la base de données non -[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] abonné. Pour plus d'informations sur ce paramètre, consultez [Replication Distribution Agent](../../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
-   Le compte sous lequel s'exécute l'Agent de distribution doit disposer de droits d'accès au répertoire d'installation du fournisseur OLE DB.  
  
-   Par défaut pour les non -[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] abonnés, l’Agent de Distribution utilise la valeur [(destination par défaut)] pour la base de données d’abonnement (le **- SubscriberDB** paramètre pour l’Agent de Distribution) :  
  
    -   Sur Oracle, un serveur a au plus une base de données, il n'est donc pas nécessaire de la spécifier.  
  
    -   Pour IBM DB2, la base de données est spécifiée dans la chaîne de connexion DB2. Pour plus d’informations, consultez [créer un abonnement pour un abonné Non SQL Server](../../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md).  
  
-   Si le serveur de distribution [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est exécuté sur une plateforme 64 bits, vous devez utiliser la version 64 bits du fournisseur OLE DB approprié.  
  
-   La réplication déplace les données en format Unicode quelles que soient les pages de classement/de codes utilisées sur le serveur de publication et sur l'Abonné. Il est recommandé de choisir une page de classement/de codes compatible lors de la réplication entre serveurs de publication et abonnés.  
  
-   Si un article est ajouté ou supprimé d'une publication, les abonnements aux abonnés non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] doivent être réinitialisés.  
  
-   Les seules contraintes prises en charge pour tous les Abonnés non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sont : NULL et NOT NULL. Les contraintes de clés primaires sont répliquées en tant qu'index uniques.  
  
-   La valeur NULL est traitée différemment par différentes bases de données, ce qui affecte la façon dont une valeur vide, une chaîne vide ou une valeur NULL est représentée. Cela affecte à son tour le comportement des valeurs insérées dans des colonnes où des contraintes uniques sont définies. Par exemple, Oracle autorise plusieurs valeurs NULL dans une colonne considérée comme unique, alors de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] n'autorise qu'une seule valeur NULL dans une colonne unique.  
  
     Un autre facteur est la façon dont les valeurs NULL, les chaînes vides ou les valeurs vides sont traitées lorsque la colonne est définie comme NOT NULL. Pour plus d'informations sur la résolution de ce problème pour les abonnés Oracle, consultez [Oracle Subscribers](../../../relational-databases/replication/non-sql/oracle-subscribers.md).  
  
-   Les métadonnées liées à la réplication (table de la séquence de la transaction) ne sont pas supprimées d'abonnés non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lorsque l'abonnement est supprimé.  
  
### Se conformer aux conditions requises de la base de données de l'Abonné.  
  
-   Le schéma et les données publiés doivent être conformes aux conditions requises de la base de données sur l'Abonné. Par exemple, si la taille maximale de ligne d'une base de données non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est plus petite que pour une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vous devez vous assurer que le schéma et les données publiés ne dépassent pas cette taille.  
  
-   Les tables répliquées sur des Abonnés non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] adoptent les conventions d'affectation des noms de tables de la base de données sur l'Abonné.  
  
-   Les instructions DDL ne sont pas prises en charge pour les Abonnés non SQL Server. Pour plus d’informations sur les modifications de schéma, consultez [apporter des modifications de schéma sur les bases de données de Publication](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
### Prise en charge de la fonctionnalité de réplication  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] offre deux types d'abonnements : les abonnements par émission de données et les abonnements par extraction. Les abonnés non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] doivent utiliser les abonnements par envoi de données (push), dans lesquels l'Agent de distribution est exécuté sur le serveur de distribution [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] offre deux formats d’instantané : bcp en mode natif et en mode caractère. Les abonnés non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nécessitent des instantanés en mode caractère.  
  
-   Les abonnés non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne peuvent pas utiliser d'abonnements mis à jour immédiatement ou mis à jour en attente, et ne peuvent pas être des nœuds dans une topologie d'égal à égal.  
  
-   Les abonnés non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne peuvent pas être initialisés automatiquement à partir d'une sauvegarde.  
  
## Voir aussi  
 [Réplication hétérogène d'une base de données](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [S'abonner à des publications](../../../relational-databases/replication/subscribe-to-publications.md)  
  
  