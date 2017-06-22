---
title: "Réorganiser et reconstruire des index | Microsoft Docs"
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-indexes
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.index.rebuild.f1
- sql13.swb.indexproperties.fragmentation.f1
- sql13.swb.index.reorg.f1
helpviewer_keywords:
- large object defragmenting
- indexes [SQL Server], reorganizing
- index reorganization [SQL Server]
- reorganizing indexes
- defragmenting large object data types
- index fragmentation [SQL Server]
- index rebuilding [SQL Server]
- rebuilding indexes
- indexes [SQL Server], rebuilding
- defragmenting indexes
- nonclustered indexes [SQL Server], defragmenting
- fragmentation [SQL Server]
- index defragmenting [SQL Server]
- LOB data [SQL Server], defragmenting
- clustered indexes, defragmenting
ms.assetid: a28c684a-c4e9-4b24-a7ae-e248808b31e9
caps.latest.revision: 70
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: d4dc2ff665ff191fb75dd99103a222542262d4c4
ms.openlocfilehash: 8f0efc0281809b6547a86d708e4596666f10e0c0
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="reorganize-and-rebuild-indexes"></a>Réorganiser et reconstruire des index
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

 > Pour accéder au contenu relatif aux versions précédentes de SQL Server, consultez [Réorganiser et reconstruire des index](https://msdn.microsoft.com/en-US/library/ms189858(SQL.120).aspx).

  Cette rubrique explique comment réorganiser ou reconstruire un index fragmenté dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] gère automatiquement des index lorsque des opérations d'insertion, de mise à jour ou de suppression sont effectuées sur les données sous-jacentes. Au fil des modifications, les informations figurant dans l'index sont éparpillées dans la base de données (fragmentée). La fragmentation intervient lorsque des index possèdent des pages dans lesquelles l'organisation logique (reposant sur la valeur de la clé) ne correspond pas à l'organisation physique dans le fichier de données. Une fragmentation importante des index peut diminuer les performances des requêtes et ralentir la vitesse de réponse de votre application.  
  
 Vous pouvez remédier à la fragmentation des index en réorganisant un index ou en reconstruisant un index. Dans le cas d'index partitionnés reposant sur un schéma de partition, vous pouvez utiliser les méthodes suivantes sur la totalité ou sur une partition unique d'un index. La reconstruction d'un index entraîne sa suppression puis sa recréation. Ceci permet d'éviter toute fragmentation, de libérer de l'espace disque en compactant les pages d'après le paramètre du facteur de remplissage spécifié ou déjà existant et en retriant les lignes de l'index en pages contiguës. Quand ALL est précisé, tous les index sur la table sont supprimés puis reconstruits en une seule transaction. La réorganisation d'un index utilise des ressources système minimes. En effet, elle défragmente le niveau feuille des index cluster et non cluster sur les tables et les vues en retriant les pages de niveau feuille de façon physique afin de resuivre l'ordre logique, c'est-à-dire de gauche à droite, des nœuds. Cette opération compacte également les pages d'index. Le compactage s'appuie sur la valeur du facteur de remplissage existante.  
  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Fragmentation"></a> Détection de la fragmentation  
 Lorsque vous déterminez la méthode de défragmentation à adopter, la première étape consiste à analyser l'index pour évaluer son degré de fragmentation. La fonction système [sys.dm_db_index_physical_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)vous permet de détecter la fragmentation dans un index spécifique, dans tous les index d’une table ou d’une vue indexée, dans tous les index d’une base de données ou dans tous les index de l’ensemble des bases de données. Pour les index partitionnés, **sys.dm_db_index_physical_stats** procure aussi des informations de fragmentation pour chaque partition.  
  
 Le jeu de résultats retourné par la fonction **sys.dm_db_index_physical_stats** inclut les colonnes suivantes.  
  
|Colonne|Description|  
|------------|-----------------|  
|**avg_fragmentation_in_percent**|Pourcentage de fragmentation logique (pages non ordonnées dans un index).|  
|**fragment_count**|Nombre de fragments (pages de feuille consécutives physiquement) dans l'index.|  
|**avg_fragment_size_in_pages**|Nombre moyen de pages dans un fragment d'un index.|  
  
 Une fois le degré de fragmentation connu, utilisez le tableau suivant pour déterminer la méthode la mieux adaptée pour corriger la fragmentation.  
  
|Valeur**avg_fragmentation_in_percent** |Instruction corrective|  
|-----------------------------------------------|--------------------------|  
|> 5 % et < = 30 %|ALTER INDEX REORGANIZE|  
|> 30%|ALTER INDEX REBUILD WITH (ONLINE = ON)*|  
  
 \* La reconstruction d’un index peut être exécutée en ligne ou hors connexion. La réorganisation d'un index s'effectue toujours en ligne. Pour obtenir le même niveau de disponibilité qu'avec l'option de réorganisation, vous devez reconstruire les index en ligne.  
  
 Ces valeurs fournissent des directives grossières pour déterminer le point auquel vous devez basculer entre ALTER INDEX REORGANIZE et ALTER INDEX REBUILD. Toutefois, les valeurs réelles peuvent varier d'un cas à l'autre. Il est important que vous fassiez des essais pour déterminer le meilleur seuil pour votre environnement. Des niveaux très bas de fragmentation (inférieurs à 5 %) ne doivent pas être pris en compte par ces commandes, car l'avantage de la suppression d'un volume de fragmentation aussi réduit est quasiment toujours largement compensé par le coût de la réorganisation ou de la reconstruction de l'index.  
  
> [!NOTE]
>  En général, la fragmentation sur les petits index n'est pas contrôlable. Les pages de petits index sont parfois stockées sur des extensions mixtes. Les extensions mixtes sont partagées par huit objets maximum ; par conséquent, la fragmentation dans un petit index peut ne pas être réduite après la réorganisation ou la reconstruction de l'index.
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Les index possédant plus de 128 extensions sont reconstruits en deux phases distinctes : une phase logique et une phase physique. Dans la phase logique, les unités d'allocation utilisées par l'index sont signalées comme devant être désallouées, les lignes de données sont copiées et triées, puis elles sont déplacées vers les nouvelles unités d'allocation ayant été créées pour stocker l'index reconstruit. Dans la phase physique, les unités d'allocation préalablement signalées pour être désallouées sont supprimées physiquement dans des transactions courtes qui interviennent en arrière-plan et nécessitent peu de verrous.  
  
-   Vous ne pouvez pas spécifier des options d'index lors de la réorganisation d'un index.  
  
-   L’instruction `ALTER INDEX REORGANIZE` a besoin du fichier de données contenant l’index pour disposer d’espace, car l’opération peut uniquement allouer des pages de travail temporaires à un même fichier, mais pas à un autre fichier du groupe de fichiers.  De ce fait, même si le groupe de fichiers a des pages libres, l’utilisateur peut toujours rencontrer l’erreur 1105 « Impossible d’allouer de l’espace pour l’objet \<nom_index>.\<nom_table> dans la base de données \<nom_base_données>, car le groupe de fichiers 'PRIMARY' est plein ».
  
-   La création et la reconstruction des index non alignés sur une table contenant plus de 1 000 partitions sont possibles, mais ne sont pas prises en charge. Ces opérations peuvent entraîner une dégradation des performances ou une consommation de mémoire excessive.
  
> [!NOTE]
>  À partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], les statistiques ne sont pas créées en analysant toutes les lignes de la table quand un index partitionné est créé ou reconstruit. Au lieu de cela, l'optimiseur de requête utilise l'algorithme d'échantillonnage par défaut pour générer des statistiques. Pour obtenir des statistiques sur les index partitionnés en analysant toutes les lignes de la table, utilisez CREATE STATISTICS ou UPDATE STATISTICS avec la clause FULLSCAN.
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite une autorisation ALTER sur la table ou la vue. L’utilisateur doit être membre du rôle serveur fixe **sysadmin** ou des rôles de base de données fixes **db_ddladmin** et **db_owner** .  
  
##  <a name="SSMSProcedureFrag"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-check-the-fragmentation-of-an-index"></a>Pour vérifier la fragmentation d'un index  
  
1.  Dans l'Explorateur d'objets, développez la base de données qui contient la table sur laquelle vous souhaitez vérifier une fragmentation d'index.  
  
2.  Développez le dossier **Tables** .  
  
3.  Développez la table sur laquelle vous souhaitez vérifier une fragmentation d'index.  
  
4.  Développez le dossier **Index** .  
  
5.  Cliquez avec le bouton droit sur l’index dont vous voulez vérifier la fragmentation, puis sélectionnez **Propriétés**.  
  
6.  Sous **Sélectionner une page**, sélectionnez **Fragmentation**.  
  
     Les informations suivantes sont disponibles dans la page **Fragmentation** :  
  
     **Remplissage de la page**  
     Indique le remplissage moyen des pages d'index, sous forme de pourcentage. 100% signifie que les pages d'index sont totalement remplies. 50% signifie qu'en moyenne, chaque page d'index est remplie à moitié.  
  
     **Fragmentation totale**  
     Pourcentage de fragmentation logique. Cette valeur indique le nombre de pages dans un index qui ne sont pas stockées dans l'ordre.  
  
     **Taille moyenne de ligne**  
     Taille moyenne d'une ligne de niveau feuille.  
  
     **Profondeur**  
     Nombre de niveaux dans l'index, notamment le niveau feuille.  
  
     **Enregistrements transférés**  
     Nombre d'enregistrements d'un segment qui contiennent des pointeurs avant vers un autre emplacement de données. (Cet état se produit pendant une mise à jour, lorsque l'espace disponible est insuffisant pour stocker la nouvelle ligne à l'emplacement d'origine.)  
  
     **Lignes fantômes**  
     Nombre de lignes marquées pour la suppression qui ne sont pas encore supprimées. Ces lignes seront supprimées par un thread de nettoyage, lorsque le serveur n'est pas occupé. Cette valeur ne comprend pas les lignes qui sont conservées à cause d'une transaction d'isolement d'instantané en suspens.  
  
     **Type d'index**  
     Type de l'index. Les valeurs possibles sont **Index cluster**, **Index non-cluster**et **XML primaire**. Les tables peuvent également être stockées en tant que segment (sans index), mais dans ce cas la page Propriétés de l'index est impossible à ouvrir.  
  
     **Lignes de niveau feuille**  
     Nombre de lignes de niveau feuille.  
  
     **Taille maximale de ligne**  
     Taille maximale des lignes de niveau feuille.  
  
     **Taille minimale de ligne**  
     Taille minimale des lignes de niveau feuille.  
  
     **Pages**  
     Nombre total de pages de données.  
  
     **ID de partition (Partition ID)**  
     ID de partition de l'arbre B (B-tree) qui contient l'index.  
  
     **Enregistrement de version fantôme**  
     Nombre d'enregistrements fantômes étant conservés en raison d'une transaction d'isolement d'instantané en attente.  
  
##  <a name="TsqlProcedureFrag"></a> Utilisation de Transact-SQL  
  
#### <a name="to-check-the-fragmentation-of-an-index"></a>Pour vérifier la fragmentation d'un index  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Find the average fragmentation percentage of all indexes  
    -- in the HumanResources.Employee table.   
    SELECT a.index_id, name, avg_fragmentation_in_percent  
    FROM sys.dm_db_index_physical_stats (DB_ID(N'AdventureWorks2012'), 
          OBJECT_ID(N'HumanResources.Employee'), NULL, NULL, NULL) AS a  
        JOIN sys.indexes AS b 
          ON a.object_id = b.object_id AND a.index_id = b.index_id;   
    GO  
    ```  
  
     L'instruction ci-dessus peut retourner un jeu de résultats similaire au suivant.  
  
    ```  
    index_id    name                                                  avg_fragmentation_in_percent  
    ----------- ----------------------------------------------------- ----------------------------  
    1           PK_Employee_BusinessEntityID                          0  
    2           IX_Employee_OrganizationalNode                        0  
    3           IX_Employee_OrganizationalLevel_OrganizationalNode    0  
    5           AK_Employee_LoginID                                   66.6666666666667  
    6           AK_Employee_NationalIDNumber                          50  
    7           AK_Employee_rowguid                                   0  
  
    (6 row(s) affected)  
    ```  
  
 Pour plus d’informations, consultez [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md).  
  
##  <a name="SSMSProcedureReorg"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-reorganize-or-rebuild-an-index"></a>Pour réorganiser ou reconstruire un index  
  
1.  Dans l'Explorateur d'objets, développez la base de données qui contient la table sur laquelle vous souhaitez réorganiser un index.  
  
2.  Développez le dossier **Tables** .  
  
3.  Développez la table sur laquelle vous souhaitez réorganiser un index.  
  
4.  Développez le dossier **Index** .  
  
5.  Cliquez avec le bouton droit sur l’index que vous souhaitez réorganiser et sélectionnez **Réorganiser**.  
  
6.  Dans la boîte de dialogue **Réorganiser les index** , vérifiez que l'index correct figure dans la grille **Index à réorganiser** , puis cliquez sur **OK**.  
  
7.  Cochez la case **Compacter les données de la colonne d’objets volumineux** pour indiquer que toutes les pages qui contiennent des données LOB seront aussi compactées.  
  
8.  Cliquez sur **OK.**  
  
#### <a name="to-reorganize-all-indexes-in-a-table"></a>Pour réorganiser tous les index d'une table  
  
1.  Dans l'Explorateur d'objets, développez la base de données qui contient la table sur laquelle vous souhaitez réorganiser les index.  
  
2.  Développez le dossier **Tables** .  
  
3.  Développez la table sur laquelle vous souhaitez réorganiser les index.  
  
4.  Cliquez avec le bouton droit sur le dossier **Index** , puis sélectionnez **Réorganiser tout**.  
  
5.  Dans la boîte de dialogue **Réorganiser les index** , vérifiez que les index corrects sont dans **Index à réorganiser**. Pour supprimer un index de la grille **Index à réorganiser** , sélectionnez l'index et appuyez sur la touche SUPPR.  
  
6.  Cochez la case **Compacter les données de la colonne d’objets volumineux** pour indiquer que toutes les pages qui contiennent des données LOB seront aussi compactées.  
  
7.  Cliquez sur **OK.**  
  
#### <a name="to-rebuild-an-index"></a>Pour reconstruire un index  
  
1.  Dans l'Explorateur d'objets, développez la base de données qui contient la table sur laquelle vous souhaitez réorganiser un index.  
  
2.  Développez le dossier **Tables** .  
  
3.  Développez la table sur laquelle vous souhaitez réorganiser un index.  
  
4.  Développez le dossier **Index** .  
  
5.  Cliquez avec le bouton droit sur l’index que vous souhaitez réorganiser et sélectionnez **Regénérer**.  
  
6.  Dans la boîte de dialogue **Reconstruire les index** , vérifiez que l'index correct figure dans la grille **Index à reconstruire** , puis cliquez sur **OK**.  
  
7.  Cochez la case **Compacter les données de la colonne d’objets volumineux** pour indiquer que toutes les pages qui contiennent des données LOB seront aussi compactées.  
  
8.  Cliquez sur **OK.**  
  
##  <a name="TsqlProcedureReorg"></a> Utilisation de Transact-SQL  
  
#### <a name="to-reorganize-a-defragmented-index"></a>Pour réorganiser un index défragmenté  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- Reorganize the IX_Employee_OrganizationalLevel_OrganizationalNode 
    -- index on the HumanResources.Employee table.   
  
    ALTER INDEX IX_Employee_OrganizationalLevel_OrganizationalNode 
      ON HumanResources.Employee  
    REORGANIZE ;   
    GO  
    ```  
  
#### <a name="to-reorganize-all-indexes-in-a-table"></a>Pour réorganiser tous les index d'une table  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- Reorganize all indexes on the HumanResources.Employee table.  
    ALTER INDEX ALL ON HumanResources.Employee  
    REORGANIZE ;   
    GO  
    ```  
  
#### <a name="to-rebuild-a-defragmented-index"></a>Pour reconstruire un index défragmenté  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple reconstruit un seul index portant sur la table `Employee` .  
  
     [!code-sql[IndexDDL#AlterIndex1](../../relational-databases/indexes/codesnippet/tsql/reorganize-and-rebuild-i_1.sql)]  
  
#### <a name="to-rebuild-all-indexes-in-a-table"></a>Pour reconstruire tous les index d'une table  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête. L'exemple spécifie le mot de passe `ALL`. Ceci permet de reconstruire tous les index associés à la table. Trois options sont spécifiées.  
  
     [!code-sql[IndexDDL#AlterIndex2](../../relational-databases/indexes/codesnippet/tsql/reorganize-and-rebuild-i_2.sql)]  
  
 Pour plus d’informations, consultez [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
  [Guide de conception d’index SQL Server](../../relational-databases/sql-server-index-design-guide.md)   
  

