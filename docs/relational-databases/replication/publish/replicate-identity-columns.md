---
title: "R&#233;pliquer des colonnes d&#39;identit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "10/04/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "identités [réplication SQL Server]"
  - "valeurs d'identité [réplication SQL Server]"
  - "réplication de fusion [réplication SQL Server], gestion des plages d’identité"
  - "publication [réplication SQL Server], colonnes d’identité"
  - "réplication transactionnelle, gestion des plages d’identité"
  - "colonnes d’identité [SQL Server], réplication"
ms.assetid: eb2f23a8-7ec2-48af-9361-0e3cb87ebaf7
caps.latest.revision: 51
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 51
---
# R&#233;pliquer des colonnes d&#39;identit&#233;
  Lorsque vous attribuez une propriété IDENTITY à une colonne, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] génère automatiquement des numéros séquentiels pour les nouvelles lignes insérées dans la table contenant la colonne d’identité. Pour plus d’informations, consultez [IDENTITY &#40 ; Propriété &#41 ; &#40 ; Transact-SQL &#41 ;](../Topic/IDENTITY%20\(Property\)%20\(Transact-SQL\).md). Les colonnes d'identité devant être incluses comme composantes de la clé primaire, il est important d'éviter les valeurs dupliquées dans les colonnes d'identité. Pour utiliser des colonnes d'identité dans une topologie de réplication qui a des mises à jour sur plusieurs nœuds, chaque nœud de cette topologie de réplication doit avoir une plage différente de valeurs d'identité, de façon à ce qu'il n'y ait pas de valeurs dupliquées.  
  
 Par exemple, la plage 1-100 pourrait être affectée au serveur de publication, la plage 101-200 à l'abonné A et la plage 201-300 à l'abonné B. Si une ligne est insérée au niveau du serveur de publication et la valeur d'identité est, par exemple, 65, cette valeur est répliquée sur chaque abonné. Quand la réplication insère des données sur chaque Abonné, elle n'incrémente pas la valeur de la colonne d'identité dans la table de l'Abonné ; c'est au contraire la valeur littérale 65 qui est insérée. Seules les insertions des utilisateurs - et pas les insertions des agents de réplication - provoquent l'incrémentation de la valeur de la colonne d'identité.  
  
 La réplication gère les colonnes d'identité à travers tous les types de publications et d'abonnements ; elle vous permet de gérer les colonnes manuellement ou de demander à ce que la réplication les gère automatiquement.  
  
> [!NOTE]  
>  L'ajout d'une colonne d'identité à une table publiée n'est pas pris en charge, car la nouvelle colonne peut entraîner une non-convergence quand la colonne est répliquée vers l'Abonné. Les valeurs de la colonne d'identité sur l'Abonné dépendent de l'ordre dans lequel les lignes sont physiquement stockées dans la table affectée. Les lignes sont susceptibles d'être stockées différemment sur l'Abonné ; la valeur de la colonne d'identité peut donc être différente pour les mêmes lignes.  
  
## Spécification d'une option de gestion des plages d'identités  
 La réplication offre trois options de gestion des plages d'identités :  
  
-   Automatique. Utilisée pour la réplication de fusion et la réplication transactionnelle avec des mises à jour sur l'Abonné. Spécifiez des plages de taille pour le serveur de publication et les Abonnés, et la réplication gère automatiquement l'affectation des nouvelles plages. La réplication définit l'option NOT FOR REPLICATION pour la colonne d'identité sur l'Abonné, de sorte que seules les insertions des utilisateurs provoquent l'incrémentation de la valeur sur l'Abonné.  
  
    > [!NOTE]  
    >  Les Abonnés doivent se synchroniser avec le serveur de publication pour recevoir de nouvelles plages. Les plages d'identité étant affectées automatiquement aux Abonnés, il est possible pour les Abonnés d'épuiser la totalité des plages d'identité disponibles s'ils requièrent de nouvelles plages de façon répétée.  
  
-   Manuel. Utilisée pour la réplication d'instantané et la réplication transactionnelle sans mises à jour sur l'Abonné, pour la réplication transactionnelle d'égal à égal ou si votre application doit contrôler les plages d'identité par programmation. Si vous spécifiez une gestion manuelle, vous devez vérifier que les plages sont affectées au serveur de publication et à chaque Abonné, et que de nouvelles plages sont attribuées si les plages initiales sont utilisées. La réplication définit l'option NOT FOR REPLICATION sur la colonne d'identité sur l'Abonné.  
  
-   Aucun. Cette option n'est recommandée que pour assurer une compatibilité amont avec les versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et elle est disponible seulement à partir de l'interface des procédures stockées pour les publications transactionnelles.  
  
 Pour spécifier une option Gestion des plages d’identité, consultez [Gérer les colonnes d’identité](../../../relational-databases/replication/publish/manage-identity-columns.md).  
  
## Attribution de plages d'identité  
 La réplication de fusion et la réplication transactionnelle utilisent différentes méthodes pour l'attribution des plages ; ces méthodes sont décrites dans cette section.  
  
 Il existe deux types de plages à prendre en compte lors de la réplication de colonnes d'identité : les plages attribuées au serveur de publication et aux Abonnés, et la plage du type de données de la colonne. Le tableau suivant indique les plages disponibles pour les types de données généralement utilisés dans les colonnes d'identité. La plage est utilisée à travers tous les nœuds d'une topologie. Par exemple, si vous utilisez **smallint** commençant à 1 avec un incrément de 1, le nombre maximal d’insertions est 32 767 pour le serveur de publication et tous les abonnés. Le nombre réel d'insertions dépend de la présence d'interruptions dans les valeurs et de l'utilisation d'une valeur de seuil. Pour plus d'informations sur les seuils, consultez les sections suivantes, « Réplication de fusion » et « Réplication transactionnelle avec des abonnements mis à jour en attente ».  
  
 Si le serveur de publication épuise sa plage d’identité après une insertion, il peut affecter automatiquement une nouvelle plage si l’insertion a été effectuée par un membre de la **db_owner** rôle fixe de base de données. Si l’insertion a été effectuée par un utilisateur non dans ce rôle, l’Agent de lecture du journal, l’Agent de fusion ou un utilisateur qui est membre de la **db_owner** doit s’exécuter [sp_adjustpublisheridentityrange &#40 ; Transact-SQL &#41 ;](../../../relational-databases/system-stored-procedures/sp-adjustpublisheridentityrange-transact-sql.md). Pour les publications transactionnelles, l'Agent de lecture du journal doit être en cours d'exécution pour allouer automatiquement une nouvelle plage (la configuration par défaut est que l'agent s'exécute en continu).  
  
> [!WARNING]  
>  Au cours d’une insertion de lot volumineux le déclencheur de réplication est déclenché une seule fois, pas pour chaque ligne de l’instruction insert. Cela peut entraîner un échec de l’instruction insert si une plage d’identité est épuisée pendant une insertion importante, comme un **INSERT INTO** instruction.  
  
|Type de données|Plage|  
|---------------|-----------|  
|**tinyint**|Non pris en charge pour la gestion automatique|  
|**smallint**|-2^15 (-32 768) à 2^15-1 (32 767)|  
|**int**|-2^31 (-2 147 483 648) à 2^31-1 (2 147 483 647)|  
|**bigint**|-2^63 (-9,223,372,036,854,775,808) à 2^63-1 (9,223,372,036,854,775,807)|  
|**décimal** et **numérique**|-10^38+1 à 10^38-1|  
  
> [!NOTE]  
>  Pour créer un numéro à incrémentation automatique qui peut être utilisé dans plusieurs tables ou être appelé par des applications sans faire référence à une table, consultez [Numéros de séquence](../../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
### Réplication de fusion  
 Les plages d'identité sont gérées par le serveur de publication et propagées aux Abonnés par l'Agent de fusion (dans une hiérarchie de réédition, les plages sont gérées par le serveur de publication racine et les rééditeurs). Les valeurs d'identité sont affectées à partir d'un pool au serveur de publication. Lorsque vous ajoutez un article avec une colonne d’identité à une publication dans l’Assistant Nouvelle Publication ou à l’aide de [sp_addmergearticle &#40 ; Transact-SQL &#41 ;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md), vous spécifiez des valeurs pour :  
  
-   Le **@identity_range** paramètre qui contrôle la taille de plage d’identité initialement allouée au serveur de publication et sur les abonnés avec des abonnements clients.  
  
    > [!NOTE]  
    >  Pour les abonnés exécutant des versions précédentes de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], ce paramètre (et non les **@pub_identity_range** paramètre) contrôle également la taille de plage d’identité sur les abonnés de republication.  
  
-   Le **@pub_identity_range** paramètre qui contrôle la taille de plage d’identité pour la réédition allouée aux abonnés avec des abonnements serveur (nécessaires pour republier des données). Tous les Abonnés avec des abonnements serveur reçoivent une plage pour la réédition, même s'ils ne rééditent pas réellement des données.  
  
-   Le **@threshold** paramètre, qui est utilisé pour déterminer quand une nouvelle plage d’identités est requise pour un abonnement à [!INCLUDE[ssEW](../../../includes/ssew-md.md)] ou une version antérieure de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Par exemple, vous pouvez spécifier 10 000 pour **@identity_range** et 500000 pour **@pub_identity_range**. Le serveur de publication et tous les abonnés exécutant [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou une version ultérieure, y compris l’abonné avec l’abonnement serveur sont affectés à une plage principale de 10 000. L’abonné avec l’abonnement serveur est également assignée une plage principale de 500000, qui peut être utilisé par les abonnés qui se synchronisent avec l’abonné de republication (vous devez également spécifier **@identity_range**, **@pub_identity_range**, et **@threshold** pour les articles de la publication sur l’abonné de republication).  
  
 Chaque abonné exécutant [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou une version ultérieure reçoit également une plage d’identité secondaire. La plage secondaire a une taille équivalente à celle de la plage principale ; quand la plage principale est épuisée, la plage secondaire est utilisée et l'Agent de fusion attribue une nouvelle plage à l'Abonné. La nouvelle plage devient la plage secondaire et le processus continue tant que l'Abonné utilise des valeurs d'identité.  
  
  
### Réplication transactionnelle avec des abonnements mis à jour en attente  
 Les plages d'identités sont gérées par le serveur de distribution et propagées aux Abonnés par l'Agent de distribution. Les valeurs d'identité sont attribuées à partir d'un pool au serveur de distribution. La taille du pool est basée sur la taille du type de données et sur l'incrément utilisé par la colonne d'identité. Lorsque vous ajoutez un article avec une colonne d’identité à une publication dans l’Assistant Nouvelle Publication ou à l’aide de [sp_addarticle &#40 ; Transact-SQL &#41 ;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md), vous spécifiez des valeurs pour :  
  
-   Le **@identity_range** paramètre qui contrôle la taille de plage d’identité initialement allouée à tous les abonnés.  
  
-   Le **@pub_identity_range** paramètre qui contrôle la taille de plage d’identité allouée au serveur de publication.  
  
-   Le **@threshold** paramètre, qui est utilisé pour déterminer quand une nouvelle plage d’identités est requise pour un abonnement.  
  
 Par exemple, vous pouvez spécifier 10 000 pour **@pub_identity_range**, 1000 pour **@identity_range** (en supposant que moins mises à jour sur l’abonné) et 80 pour cent pour **@threshold**. Après 800 insertions sur un Abonné (80 pour cent de 1 000), un Abonné se voit attribuer une nouvelle plage. Après 8 000 insertions sur l'Abonné, le serveur de publication se voit attribuer une nouvelle plage. Quand une nouvelle plage est attribuée, il y aura une interruption dans les valeurs de plage d'identités de la  table. La spécification d'un seuil plus élevé donne des interruptions plus courtes, mais le système tolère moins les pannes : si l'agent de distribution ne peut pas être exécuté pour une raison quelconque, un abonné peut tomber plus facilement à court d'identités.  
  
## Attribution de plages pour la gestion manuelle des plages d'identité  
 Si vous spécifiez une gestion manuelle des plages d'identité, vous devez vérifier que le serveur de publication et que chaque Abonné utilisent des plages d'identités différentes. Par exemple, supposons une table sur le serveur de publication avec une colonne d'identité définié en tant que `IDENTITY(1,1)` : la colonne d'identité commence à 1 et elle est incrémentée de 1 chaque fois qu'une ligne est insérée. Si la table sur le serveur de publication a 5 000 lignes et que vous vous attendez à un accroissement de la table au cours de la durée de vie de l'application, le serveur de publication peut utiliser la plage 1 à 10 000. Étant donnés deux Abonnés, l'Abonné A peut utiliser la plage 10 001 à 20 000 et l'Abonné B peut utiliser la plage 20 001 à 30 000.  
  
 Après qu'un Abonné ait été initialisé avec un instantané ou via un autre moyen, exécutez DBCC CHECKIDENT pour attribuer un point de départ pour sa plage d'identités. Par exemple, sur l'Abonné A, vous pouvez exécuter `DBCC CHECKIDENT('<TableName>','reseed',10001)`. Sur l’abonné B, vous pouvez exécuter `CHECKIDENT('<TableName>','reseed',20001)`.  
  
 Pour attribuer de nouvelles plages au serveur de publication ou aux Abonnés, exécutez DBCC CHECKIDENT et spécifiez une nouvelle valeur permettant de réalimenter la table. Vous devez disposer d'un moyen quelconque pour déterminer quand une nouvelle plage doit être attribuée. Par exemple, votre application peut avoir un mécanisme détectant quand un nœud est sur le point d'utiliser la totalité de sa plage et attribuant une nouvelle plage à l'aide de DBCC CHECKIDENT. Vous pouvez aussi ajouter une contrainte de vérification pour garantir qu'une ligne ne peut pas être ajoutée si une valeur de colonne d'identité en dehors de la page devait être utilisée.  
  
## Gestion des plages d'identités après la restauration d'une base de données  
 Si vous utilisez la gestion automatique des plages d'identités, quand un Abonné est restauré à partir d'une sauvegarde, il requiert automatiquement une nouvelle plage de valeurs d'identité. Si un serveur de publication est restauré à partir d'une sauvegarde, vous devez vérifier que le serveur de publication se voit attribuer une plage appropriée. La réplication de fusion, attribuer une plage à l’aide [sp_restoremergeidentityrange &#40 ; Transact-SQL &#41 ;](../../../relational-databases/system-stored-procedures/sp-restoremergeidentityrange-transact-sql.md). Pour la réplication transactionnelle, déterminez la valeur la plus élevée qui a été utilisée, puis définissez le point de départ pour les nouvelles plages. Utilisez la procédure suivante après que la base de données de publication ait été restaurée :  
  
1.  Arrêtez toutes les activités sur tous les Abonnés.  
  
2.  Pour chaque table publiée comportant une colonne d'identité :  
  
    1.  Dans la base de données d'abonnement sur chaque Abonné, exécutez `IDENT_CURRENT('<TableName>')`.  
  
    2.  Enregistrez la valeur la plus élevée trouvée parmi tous les Abonnés.  
  
    3.  Dans la base de données de publication sur le serveur de publication, exécutez `DBCC CHECKIDENT(<TableName>','reseed',<HighestValueFound+1>`).  
  
    4.  Dans la base de données de publication sur le serveur de publication, exécutez `sp_adjustpublisheridentityrange <PublicationName>, <TableName>`.  
  
    > [!NOTE]  
    >  Si la valeur de la colonne d'identité est définie pour se décrémenter au lieu de s'incrémenter, enregistrez la valeur la plus faible, puis réalimentez la table avec cette valeur.  
  
## Voir aussi  
 [BACKUP &#40;Transact-SQL&#41;](../../../t-sql/statements/backup-transact-sql.md)   
 [DBCC CHECKIDENT &#40 ; Transact-SQL &#41 ;](../../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md)   
 [IDENT_CURRENT &#40 ; Transact-SQL &#41 ;](../../../t-sql/functions/ident-current-transact-sql.md)   
 [IDENTITY &#40;Propriété&#41; &#40;Transact-SQL&#41;](../Topic/IDENTITY%20\(Property\)%20\(Transact-SQL\).md)   
 [sp_adjustpublisheridentityrange &#40 ; Transact-SQL &#41 ;](../../../relational-databases/system-stored-procedures/sp-adjustpublisheridentityrange-transact-sql.md)  
  
  