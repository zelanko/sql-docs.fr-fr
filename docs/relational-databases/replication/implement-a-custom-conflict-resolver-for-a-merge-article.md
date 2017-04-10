---
title: "Impl&#233;menter un outil personnalis&#233; de r&#233;solution des conflits pour un article de fusion | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "résolution des conflits de réplication de fusion [réplication SQL Server], programmes de résolution s'appuyant sur des procédures stockées"
  - "articles [réplication SQL Server], résolution des conflits"
  - "résolution des conflits [réplication SQL Server], réplication de fusion"
ms.assetid: 76bd8524-ebc1-4d80-b5a2-4169944d6ac0
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Impl&#233;menter un outil personnalis&#233; de r&#233;solution des conflits pour un article de fusion
  Cette rubrique décrit comment implémenter la résolution des conflits personnalisé pour un article de fusion dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou un [résolveur personnalisé COM](../../relational-databases/replication/merge/com-based-custom-resolvers.md).  
  
 **Dans cette rubrique**  
  
-   **Pour implémenter l'outil personnalisé de résolution des conflits pour un article de fusion à l'aide de :**  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Programme de résolution s'appuyant sur l'architecture COM.](#COM)  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Vous pouvez écrire votre propre outil personnalisé de résolution des conflits sous forme de procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)] au niveau de chaque serveur de publication. Au cours de la synchronisation, cette procédure stockée est appelée en cas de conflits dans un article pour lequel ce programme de résolution a été enregistré, et les informations sur la ligne en conflit sont passées par l'Agent de fusion aux paramètres requis de la procédure. Les outils personnalisés de résolution des conflits s'appuyant sur des procédures stockées sont toujours créés au niveau du serveur de publication.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les résolveurs de procédure stockée sont appelés uniquement pour gérer les conflits de changement de ligne. Ils ne peuvent pas être utilisés pour gérer d'autres types de conflits, comme les échecs d'insertion en raison de violations de clés primaires ou de violations de contraintes d'index unique.  
  
#### Pour créer un outil personnalisé de résolution des conflits s'appuyant sur des procédures stockées  
  
1.  Dans la base de données de publication ou la base de données **msdb** sur le serveur de publication, créez une procédure stockée système qui implémente les paramètres requis suivants :  
  
    |Paramètre|Type de données|Description|  
    |---------------|---------------|-----------------|  
    |**@tableowner**|**sysname**|Nom du propriétaire de la table pour laquelle un conflit est résolu. Il s'agit du propriétaire de la table dans la base de données de publication.|  
    |**@tablename**|**sysname**|Nom de la table pour laquelle un conflit est résolu.|  
    |**@rowguid**|**uniqueidentifier**|Identificateur unique de la ligne en conflit.|  
    |**@subscriber**|**sysname**|Nom du serveur depuis lequel une modification en conflit est propagée.|  
    |**@subscriber_db**|**sysname**|Nom de la base de données depuis laquelle la modification en conflit est propagée.|  
    |**@log_conflict OUTPUT**|**int**|Indique si le processus de fusion doit enregistrer un conflit en vue de le résoudre ultérieurement :<br /><br /> **0** = ne pas enregistrer le conflit.<br /><br /> **1** = abonné est le perdant du conflit.<br /><br /> **2** = serveur de publication est le perdant du conflit.|  
    |**@conflict_message OUTPUT**|**nvarchar (512)**|Message accompagnant la résolution si le conflit est enregistré.|  
    |**@destowner**|**sysname**|Propriétaire de la table publiée créée sur l'Abonné.|  
  
     Cette procédure stockée utilise les valeurs passées par l'Agent de fusion à ces paramètres pour implémenter votre logique de résolution des conflits personnalisée. Elle doit retourner un jeu de résultats d'une seule ligne dont la structure est identique à la table de base et qui contient les valeurs de données pour la version gagnante de la ligne.  
  
2.  Accordez les autorisations EXECUTE sur la procédure stockée à toutes connexions utilisées par les Abonnés pour se connecter au serveur de publication.  
  
#### Pour utiliser un outil de résolution des conflits personnalisé avec un nouvel article de table  
  
1.  Exécuter [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) pour définir un article, la valeur **affectant** **Server résolveur de procédures stockées** pour la **@article_resolver** paramètre et le nom de la procédure stockée qui implémente la logique de programme de résolution de conflit pour la **@resolver_info** paramètre. Pour plus d'informations, voir [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
#### Pour utiliser un outil de résolution des conflits personnalisé avec un article de table existant  
  
1.  Exécuter [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), en spécifiant **@publication**, **@article**, une valeur de **article_resolver** pour **@property**, et la valeur **pour MicrosoftSQL** **serveur stockées ProcedureResolver** pour **@value**.  
  
2.  Exécutez [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), en spécifiant **@publication**, **@article**, une valeur de **resolver_info** pour **@property**, et le nom de la procédure stockée qui implémente la logique de résolution des conflits **@value**.  
  
##  <a name="COM"></a> Programme de résolution personnalisé basé sur COM  
 Le <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> espace de noms implémente une interface qui vous permet d’écrire une logique métier complexe pour gérer des événements et résoudre les conflits qui se produisent pendant le processus de synchronisation de la réplication de fusion. Pour plus d'informations, voir [Implement a Business Logic Handler for a Merge Article](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md). Vous pouvez également écrire votre propre logique métier personnalisée en code natif pour résoudre ces conflits. Cette logique est construite sous la forme d'un composant COM et compilée dans des bibliothèques de liens dynamiques (DLL) à l'aide de produits tels que [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C++. Cet résolution des conflits personnalisé basé sur COM doit implémenter le **ICustomResolver** interface, qui est spécifiquement conçu pour la résolution des conflits.  
  
#### Pour créer et enregistrer un outil de résolution des conflits personnalisé  basé sur COM  
  
1.  Dans un environnement de création compatible COM, ajoutez des références à la bibliothèque de l'outil de résolution des conflits personnalisé.  
  
2.  Pour un projet Visual C++, utilisez la directive #import pour importer cette bibliothèque dans votre projet.  
  
3.  Créez une classe qui implémente l'interface **ICustomResolver** .  
  
4.  Implémentez certaines méthodes et propriétés.  
  
5.  Générez le projet de manière à créer le fichier bibliothèque de l'outil de résolution des conflits personnalisé.  
  
6.  Déployez la bibliothèque dans le répertoire contenant l'exécutable de l'agent de fusion (généralement \Microsoft SQL Server\100\COM).  
  
    > [!NOTE]  
    >  Un outil de résolution des conflits personnalisé doit être déployé sur l'Abonné pour un abonnement par extraction, sur le serveur de distribution pour un abonnement par émission de données ou sur le serveur Web utilisé avec la synchronisation Web.  
  
7.  Enregistrez la bibliothèque de l'outil de résolution des conflits personnalisé à l'aide de regsvr32.exe à partir du répertoire de déploiement, comme suit :  
  
    ```  
    regsvr32.exe mycustomresolver.dll  
    ```  
  
8.  Sur le serveur de publication, exécutez [sp_enumcustomresolvers & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) Pour vérifier que la bibliothèque n’est pas déjà inscrit en tant qu’un programme de résolution de conflits personnalisé.  
  
9. Pour inscrire la bibliothèque comme un résolveur de conflits personnalisé, exécutez [sp_registercustomresolver & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md), sur le serveur de distribution. Spécifiez le nom convivial de l’objet COM pour **@article_resolver**, ID (CLSID de la bibliothèque) de **@resolver_clsid**, et la valeur **false** pour **@is_dotnet_assembly**.  
  
    > [!NOTE]  
    >  Lorsque vous n’avez plus besoin, un programme de résolution de conflits personnalisé peut être annulé à l’aide [sp_unregistercustomresolver & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md).  
  
10. (Facultatif) Sur un cluster, répétez les étapes 5 à 8 pour enregistrer le programme de résolution personnalisé sur tous les nœuds du cluster. Cette procédure est nécessaire pour garantir que le programme de résolution personnalisé sera en mesure de charger correctement le réconciliateur suite à un basculement.  
  
#### Pour utiliser un outil de résolution des conflits personnalisé avec un nouvel article de table  
  
1.  Sur le serveur de publication, exécutez [sp_enumcustomresolvers & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) et notez le nom convivial du programme de résolution souhaité.  
  
2.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergearticle & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Pour définir un article. Spécifiez le nom convivial du programme de résolution de l’étape 1 de l’article **@article_resolver**. Pour plus d'informations, voir [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
#### Pour utiliser un outil de résolution des conflits personnalisé avec un article de table existant  
  
1.  Sur le serveur de publication, exécutez [sp_enumcustomresolvers & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) et notez le nom convivial du programme de résolution souhaité.  
  
2.  Exécutez [sp_changemergearticle & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), en spécifiant **@publication**, **@article**, une valeur de **article_resolver** pour **@property**, et le nom convivial du programme de résolution de l’étape 1 de l’article **@value**.  
  
#### Affichage d'un exemple de programme de résolution personnalisé  
  
1.  Un exemple est disponible dans les fichiers d'exemple de SQL Server 2000. Téléchargez **sql2000samples.cab** dans les [Exemples mis à jour pour SQL Server 2000 Service Pack 3](http://www.microsoft.com/download/details.aspx?id=8560). Huit fichiers sont téléchargés d'une taille de 6,9 Mo.  
  
2.  Extrayez les fichiers du fichier .cab compressé téléchargé.  
  
3.  Exécutez **setup.exe**.  
  
    > [!NOTE]  
    >  Lorsque vous choisissez les options d'installation, il est uniquement nécessaire d'installer les exemples de **Réplication** . (Le chemin d’installation par défaut est **C:\Program fichiers (x86) \Microsoft SQL Server 2000 Samples\1033\\**)  
  
4.  Accédez au dossier d'installation. (Le dossier par défaut est **C:\Program fichiers (x86) \Microsoft SQL Server 2000 Samples\1033\sqlrepl\unzip_sqlreplSP3.exe**)  
  
5.  Exécutez le **unzip_sqlreplSP3.exe** programme.  
  
    > [!NOTE]  
    >  Le programme de résolution com exemple installe (par défaut) pour le **C:\Program Files (x86) \Microsoft SQL Server 2000 Samples\1033\sqlrepl\resolver\subspres** dossier.  
  
6.  Dans le **subspres** dossier, rechercher toutes les occurrences de **#include sqlres.h** dans tous les fichiers sources et remplacez-les par **#import « replrec.dll » no_namespace, raw_interfaces_only**  
  
## Voir aussi  
 [Détection et résolution avancées des conflits de réplication de fusion](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Programmes de résolution personnalisés COM](../../relational-databases/replication/merge/com-based-custom-resolvers.md)   
 [Méthodes préconisées en matière de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  