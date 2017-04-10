---
title: "Abonn&#233;s IBM DB2 | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "abonnés non-SQL Server, IBM DB2"
  - "types de données [réplication SQL Server], abonnés non-SQL Server"
  - "Abonnés IBM DB2"
  - "mappage de types de données [réplication SQL Server]"
  - "abonnés hétérogènes, IBM DB2"
ms.assetid: a1a27b1e-45dd-4d7d-b6c0-2b608ed175f6
caps.latest.revision: 74
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 73
---
# Abonn&#233;s IBM DB2
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge les abonnements envoyés IBM DB2/AS 400, DB2/MVS et DB2/Universal Database par les fournisseurs OLE DB inclus avec [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Host Integration Server.  
  
## Configuration d'un Abonné IBM DB2  
 Pour configurer un Abonné IBM DB2, procédez comme suit :  
  
1.  Installez la dernière version du fournisseur [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB pour DB2 sur le serveur de distribution :  
  
    -   Si vous utilisez [!INCLUDE[ssEnterpriseEd11](../../../includes/ssenterpriseed11-md.md)], sur le [Téléchargements SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=149256) page Web, dans le **Téléchargements apparentés** cliquez sur le lien vers la dernière version de Microsoft SQL Server 2008 Feature Pack. Sur la **Microsoft SQL Server 2008 Feature Pack** page Web, recherchez **fournisseur Microsoft OLE DB pour DB2**.  
  
    -   Si vous utilisez [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Standard, installez la dernière version du serveur HIS ([!INCLUDE[msCoName](../../../includes/msconame-md.md)] Host [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]) qui inclut le fournisseur.  
  
     Outre l’installation du fournisseur, nous vous recommandons d’installer l’outil d’accès aux données, qui est utilisé dans l’étape suivante (il est installé par défaut avec le téléchargement de [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Enterprise). Pour plus d'informations sur l’installation et l'utilisation de l'outil d'accès aux données, consultez la documentation du fournisseur ou de HIS.  
  
2.  Créez une chaîne de connexion pour l'Abonné. Il est possible de créer la chaîne de connexion dans n'importe quel éditeur de texte mais il est conseillé d'utiliser l'outil d'accès aux données. Pour créer la chaîne dans l'outil d'accès aux données :  
  
    1.  Cliquez sur **Démarrer**, **programmes**, **fournisseur Microsoft OLE DB pour DB2**, puis **outil d’accès aux données**.  
  
    2.  Dans la **outil d’accès aux données**, suivez les étapes pour fournir des informations sur le serveur DB2. Après quoi, un lien UDL (Universal Data Link) est créé avec une chaîne de connexion associée (en fait, c'est la chaîne de connexion et non l'UDL qui est utilisée par la réplication).  
  
    3.  La chaîne de connexion d’accès : cliquez sur l’UDL dans l’outil d’accès aux données et sélectionnez **Afficher la chaîne de connexion**.  
  
     La chaîne de connexion se présentera comme suit (des sauts de ligne ont été insérés pour faciliter la lecture) :  
  
    ```  
    Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
    PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
    Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
    Persist Security Info=False;Connection Pooling=True;  
    ```  
  
     La plupart des options de cette chaîne sont spécifiques du serveur DB2 que vous configurez, mais vous devez attribuer à l'option `Process Binary as Character` la valeur `False`. Une valeur est nécessaire afin que l'option `Initial Catalog` identifie la base de données d'abonnement. La chaîne de connexion sera indiquée dans l'Assistant Nouvel abonnement lorsque vous créerez l'abonnement.  
  
3.  Créez une publication transactionnelle ou d'instantané, activez-la pour les Abonnés non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] puis créez un abonnement par émission de données pour l'Abonné. Pour plus d’informations, consultez [créer un abonnement pour un abonné Non SQL Server](../../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md).  
  
4.  Éventuellement, spécifiez un script de création personnalisé pour un ou plusieurs articles. Lors de la publication d'une table, un script CREATE TABLE est créé pour cette table. Pour les Abonnés non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], le script est créé en dialecte [!INCLUDE[tsql](../../../includes/tsql-md.md)] avant d'être traduit dans un dialecte SQL plus générique par l'Agent de distribution et d'être appliqué à l'Abonné. Pour spécifier un script de création personnalisé, vous devez soit modifier existant [!INCLUDE[tsql](../../../includes/tsql-md.md)] script ou créer un script complet qui utilise le dialecte SQL DB2 ; si un script DB2 est créé, utilisez la **bypass_translation** directive afin que l’Agent de Distribution applique le script sur l’abonné sans traduction.  
  
     Les scripts sont modifiés pour diverses raisons mais le plus souvent pour changer les mappages des types de données. Pour plus d'informations, consultez la section « Considérations sur le mappage des types de données », plus loin dans cette rubrique. Si vous modifiez le script [!INCLUDE[tsql](../../../includes/tsql-md.md)], limitez vos modifications aux mappages des types de données (le script ne doit par ailleurs contenir aucun commentaire). Si des modifications plus importantes sont nécessaires, créez un script DB2.  
  
     **Pour modifier un script d'article et le fournir en tant que script de création personnalisé**  
  
    1.  Après la génération de l'instantané pour la publication, accédez au dossier d'instantanés de la publication.  
  
    2.  Recherchez le fichier .sch portant le même nom que l'article, par exemple MonArticle.sch.  
  
    3.  Ouvrez ce fichier à l'aide du Bloc-notes ou d'un autre éditeur de texte.  
  
    4.  Modifiez le fichier et enregistrez-le dans un autre répertoire.  
  
    5.  Exécutez sp_changearticle, en spécifiant le chemin d’accès et nom de la *creation_script* propriété. Pour plus d’informations, consultez [sp_changearticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md).  
  
     **Pour créer un script d'article et le fournir en tant que script de création personnalisé**  
  
    1.  Créez un script d'article en langage SQL DB2. Vérifiez que la première ligne du fichier est **bypass_translation**, et rien d’autre sur la ligne.  
  
    2.  Exécutez sp_changearticle, en spécifiant le chemin d’accès et nom de la *creation_script* propriété.  
  
## Considérations relatives aux Abonnés IBM DB2  
 Outre les considérations mentionnées dans la rubrique [les abonnés non-SQL Server](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md), considérez les points suivants lors de la réplication vers des abonnés DB2 :  
  
-   Les données et les index de chaque table répliquée sont assignées à un espace disque logique DB2. La taille de page d'un espace disque logique DB2 détermine le nombre maximal de colonnes et la taille de ligne maximale des tables appartenant à l'espace disque logique. Vérifiez que l'espace disque logique associé aux tables répliquées est suffisant par rapport au nombre de colonnes répliquées et à la taille de ligne maximale des tables.  
  
-   Ne publiez pas des tables sur des Abonnés DB2 à l'aide de la réplication transactionnelle si une ou plusieurs colonnes clés primaire a le type de données DECIMAL(32-38, 0-38) ou NUMERIC(32-38, 0-38). La réplication transactionnelle identifie les lignes à l'aide de la clé primaire ; des échecs peuvent se produire car ces types de données sont mappés à VARCHAR(41) sur l'Abonné. Les tables avec des clés primaires qui utilisent ces types de données peuvent être publiées à l'aide de la réplication d'instantané.  
  
-   Si vous souhaitez créer préalablement ces tables sur l'Abonné plutôt qu'elles soient créées par la réplication, utilisez l'option Prise en charge de la réplication uniquement. Pour plus d’informations, consultez [initialiser un abonnement transactionnel sans instantané](../../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] permet des noms de table plus longs et des noms de colonnes que DB2 :  
  
    -   Si la base de données de publication comprend des tables dont les noms sont plus longs que ceux pris en charge par la version DB2 de l'Abonné, spécifiez un autre nom pour la propriété de l'article destination_table. Pour plus d’informations sur la définition des propriétés lors de la création d’une publication, consultez [Création d’une Publication](../../../relational-databases/replication/publish/create-a-publication.md) et [définir un Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
    -   Il est impossible de spécifier d'autres noms pour les colonnes. Vous devez vous assurer que les tables publiées ne contiennent pas des noms de colonne plus longs que ceux pris en charge par la version DB2 de l'Abonné.  
  
## Mappage des types de données SQL Server et IBM DB2  
 Le tableau suivant répertorie les mappages des types de données utilisés dans le cadre de la réplication des données sur un Abonné IBM DB2.  
  
|Type de données SQL Server|Type de données IBM DB2|  
|--------------------------|-----------------------|  
|**bigint**|DECIMAL (19,0)|  
|**binary(1-254)**|CHAR(1-254) FOR BIT DATA|  
|**binary(255-8000)**|VARCHAR(255-8000) FOR BIT DATA|  
|**bit**|SMALLINT|  
|**char(1-254)**|CHAR(1-254)|  
|**char(255-8000)**|VARCHAR(255-8000)|  
|**date**|DATE|  
|**datetime**|TIMESTAMP|  
|**datetime2(0-7)**|VARCHAR (27)|  
|**DateTimeOffset(0-7)**|VARCHAR (34)|  
|**Decimal (1-31, 0-31)**|DECIMAL(1-31, 0-31)|  
|**Decimal (32-38, 0-38)**|VARCHAR (41)|  
|**float(53)**|DOUBLE|  
|**float**|FLOAT|  
|**geography**|IMAGE|  
|**geometry**|IMAGE|  
|**hierarchyid**|IMAGE|  
|**image**|VARCHAR(0) FOR BIT DATA*|  
|**en**|INT|  
|**money**|DECIMAL(19,4)|  
|**NCHAR(1-4000)**|VARCHAR(1-4000)|  
|**ntext**|VARCHAR(0)*|  
|**numérique (1-31, 0-31)**|DECIMAL(1-31,0-31)|  
|**numérique (32-38, 0-38)**|VARCHAR (41)|  
|**nvarchar(1-4000)**|VARCHAR(1-4000)|  
|**nvarchar(max)**|VARCHAR(0)*|  
|**real**|REAL|  
|**smalldatetime**|TIMESTAMP|  
|**smallint**|SMALLINT|  
|**smallmoney**|DECIMAL(10,4)|  
|**sql_variant**|Néant|  
|**sysname**|VARCHAR (128)|  
|**texte**|VARCHAR(0)*|  
|**Time(0-7)**|VARCHAR(16)|  
|**timestamp**|CHAR(8) FOR BIT DATA|  
|**tinyint**|SMALLINT|  
|**uniqueidentifier**|CHAR(38)|  
|**varbinary(1-8000)**|VARCHAR(1-8000) FOR BIT DATA|  
|**varchar(1-8000)**|VARCHAR(1-8000)|  
|**varbinary(max)**|VARCHAR(0) FOR BIT DATA*|  
|**varchar(max)**|VARCHAR(0)*|  
|**xml**|VARCHAR(0)*|  
  
 *Pour en savoir plus sur les mappages au type VARCHAR(0), voir la section suivante.  
  
### Considérations sur le mappage des types de données  
 Lors de la réplication sur des Abonnés DB2, prenez en compte ce qui suit pour le mappage des types de données :  
  
-   Lors du mappage [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **char**, **varchar**, **binaire** et **varbinary** à DB2 CHAR, VARCHAR, CHAR FOR BIT DATA et VARCHAR FOR BIT DATA, respectivement, la réplication définit la longueur du type de données DB2 pour être le même que celui de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] type.  
  
     La table générée est ainsi correctement créée sur l'Abonné, pour autant que la contrainte de taille de page DB2 soit suffisamment grande pour prendre en charge la taille maximale de la ligne. Vérifiez que le nom de connexion utilisé pour accéder à la base de données DB2 possède des autorisations d'accès à des espaces disque logiques d'une taille suffisante pour contenir les tables répliquées sur DB2.  
  
-   DB2 peut prendre en charge des colonnes VARCHAR d'une largeur de 32 kilo-octets (Ko) ; par conséquent, il est possible de mapper correctement certaines colonnes d'objet volumineux [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à des colonnes DB2 VARCHAR. En revanche, le fournisseur OLE DB utilisé par la réplication sur DB2 ne prend pas en charge le mappage d'objets volumineux [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à des objets DB2 volumineux. Pour cette raison, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **texte**, **varchar (max)**, **ntext**, et **nvarchar (max)** colonnes sont mappées aux VARCHAR(0) dans les scripts de création générés. La valeur de longueur 0 doit être changée en valeur appropriée avant d'appliquer le script sur l'Abonné. Si la longueur du type de données n'est pas modifiée, DB2 génère l'erreur 604 lors de la tentative de création de table sur l'Abonné DB2 (l'erreur 604 indique que l'attribut precision ou length d'un type de données n'est pas valide).  
  
     En fonction de ce que vous connaissez de la table source à répliquer, déterminez s'il est approprié de mapper un objet volumineux [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à un élément DB2 de longueur variable et spécifiez une longueur maximale adaptée dans le script de création personnalisé. Pour plus d'informations sur la spécification d'un script de création personnalisé, reportez-vous à l'étape 5 de la section « Configuration d'un Abonné IBM DB2 » dans cette rubrique.  
  
    > [!NOTE]  
    >  La longueur spécifiée du type DB2, lorsqu'elle est combinée avec d'autres longueurs de colonne, ne peut pas dépasser la taille de ligne maximale évaluée en fonction de l'espace disque logique DB2 auquel sont assignées les données de table.  
  
     En l'absence d'un mappage approprié pour une colonne d'objet volumineux, envisagez d'utiliser le filtrage de colonnes sur l'article afin que la colonne ne soit pas répliquée. Pour plus d’informations, consultez [filtrer les données publiées](../../../relational-databases/replication/publish/filter-published-data.md).  
  
-   Lors de la réplication [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **nchar** et **nvarchar** DB2 CHAR et VARCHAR, la réplication utilise le même spécificateur de longueur pour le type DB2 que pour les [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] type. Toutefois, il se peut que la longueur du type de données soit trop petite pour la table DB2 générée.  
  
     Dans certains environnements DB2, un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **char** un élément de données n’est pas limité aux caractères codés sur ; la longueur d’un élément de type CHAR ou VARCHAR doit en tenir compte. Vous devez également prendre en compte *MAJ dans* et *hors* caractères s’ils sont nécessaires. Si vous répliquez des tables avec **nchar** et **nvarchar** colonnes, vous devrez peut-être spécifier une longueur maximale plus élevée pour le type de données dans un script de création personnalisé. Pour plus d'informations sur la spécification d'un script de création personnalisé, reportez-vous à l'étape 5 de la section « Configuration d'un Abonné IBM DB2 » dans cette rubrique.  
  
## Voir aussi  
 [Abonnés non-SQL Server](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [S'abonner à des publications](../../../relational-databases/replication/subscribe-to-publications.md)  
  
  