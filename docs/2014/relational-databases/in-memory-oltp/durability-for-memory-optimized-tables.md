---
title: Durabilité pour les tables optimisées en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d304c94d-3ab4-47b0-905d-3c8c2aba9db6
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: 0d742a0985177d9a6c860c6dedcb34eba128c930
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044239"
---
# <a name="durability-for-memory-optimized-tables"></a>Durabilité pour les tables optimisées en mémoire
  [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] fournit la durabilité complète pour les tables optimisées en mémoire. Lorsqu'une transaction qui a modifié une table optimisée en mémoire est validée, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (comme pour les tables sur disque), garantit que les modifications sont permanentes (perdureront au redémarrage d'une base de données), à condition que le stockage sous-jacent soit disponible. Il existe deux composantes clés de durabilité : l'enregistrement des transactions et la conservation des modifications de données dans un stockage sur disque.  
  
## <a name="transaction-log"></a>Journal des transactions  
 Toutes les modifications apportées aux tables sur disque ou aux tables optimisées en mémoire durables sont capturées dans un ou plusieurs enregistrements de journaux des transactions. Lorsqu'une transaction est validée, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] écrit les enregistrements de journal associés à la transaction sur le disque avant d'indiquer à l'application ou à la session utilisateur que la transaction a été validée. Cela garantit que les modifications apportées par la transaction sont durables. Le journal des transactions pour les tables optimisées en mémoire est entièrement intégré au même flux du journal utilisé par les tables sur disque. Cette intégration permet de continuer les opérations de sauvegarde, de récupération et de restauration des journaux des transactions existants sans aucune étape supplémentaire. Toutefois, étant donné que [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] augmente le débit des transactions de votre charge de travail de manière significative, vous devez vérifier que le stockage du journal des transactions est correctement configuré pour gérer l'augmentation des E/S requise.  
  
## <a name="data-and-delta-files"></a>Fichiers de données et fichiers delta  
 Les données des tables mémoire optimisées sont stockées en tant que lignes de données de forme libre qui sont liées via un ou plusieurs index en mémoire, en mémoire. Il n'existe aucune structure de page pour les lignes de données, par exemple celles utilisées pour les tables sur disque. Lorsque l’application est prête à valider la transaction, le [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] génère les enregistrements du journal pour la transaction. La persistance des tables mémoire optimisées est effectuée avec un jeu de fichiers de données et de fichiers delta à l'aide d'un thread d'arrière-plan. Les fichiers de données et les fichiers delta se trouvent dans un ou plusieurs conteneurs (utilisant le même mécanisme que celui utilisé pour les données FILESTREAM). Ces conteneurs sont mappés à un nouveau type de groupe de fichiers, appelé groupe de fichiers mémoire optimisé.  
  
 Les données sont écrites dans ces fichiers et générées de façon séquentielle stricte, ce qui réduit la latence sur le disque pour les supports rotatifs. Utilisez plusieurs conteneurs sur différents disques pour distribuer l'activité d'E/S. L'utilisation de fichiers de données et de fichiers delta dans plusieurs conteneurs sur différents disques améliore les performances de récupération, lorsque les données sont lues en mémoire à partir de ces fichiers.  
  
 Une application n'accède pas directement aux fichiers de données et aux fichiers delta. Toutes les opérations de lecture et d'écriture de données utilisent des données en mémoire.  
  
### <a name="the-data-file"></a>Fichier de données  
 Un fichier de données contient des lignes provenant d'une ou de plusieurs tables mémoire optimisées qui ont été insérées par plusieurs transactions dans le cadre d'opérations INSERT ou UPDATE. Par exemple, une ligne peut provenir de la table mémoire optimisée t1 et la ligne suivante de la table mémoire optimisée t2. Les lignes sont ajoutées au fichier de données dans l'ordre des transactions du journal des transactions, ce qui permet un accès séquentiel aux données. Ceci permet un meilleur ordre de grandeur pour le débit des E/S, par rapport à des E/S aléatoires. Chaque fichier de données a une taille d'environ 128 Mo pour les ordinateurs avec une capacité de mémoire supérieure à 16 Go, et à 16 Mo pour les ordinateurs avec une capacité de mémoire inférieure ou égale à 16 Go. Une fois que le fichier de données est plein, les lignes insérées par les nouvelles transactions sont stockées dans un autre fichier de données. Au fil du temps, les lignes provenant de tables mémoire optimisées durables sont stockées dans un ou plusieurs fichiers de données et chaque fichier de données contient des lignes provenant d'une plage disjointe mais contigüe de transactions. Par exemple, un fichier de données dont l'horodateur de validation de transaction est dans une plage de (100, 200) contient toutes les lignes insérées par les transactions dont l'horodateur de validation est supérieur à 100 et inférieur ou égal à 200. L'horodateur de validation est un nombre à croissance monotone attribué à une transaction lorsqu'elle est prête pour la validation. Chaque transaction a un horodateur de validation unique.  
  
 Lorsqu'une ligne est supprimée ou mise à jour, elle n'est pas supprimée ou modifiée sur place dans le fichier de données, mais les lignes supprimées sont suivies dans un autre type de fichier : le fichier delta. Les opérations de mise à jour sont traitées comme un tuple d'opérations de suppression et d'insertion pour chaque ligne. Cela supprime les E/S aléatoires dans le fichier de données.  
  
### <a name="the-delta-file"></a>Fichier delta  
 Chaque fichier de données est couplé à un fichier delta ayant la même plage de transactions et effectue le suivi des lignes supprimées insérées par les transactions dans cette plage. Ces données et ce fichier delta sont appelés « paire de fichiers de point de contrôle » (CFP, Checkpoint File Pair). Il s'agit de l'unité d'allocation et de désallocation, ainsi que de l'unité pour les opérations de fusion. Par exemple, un fichier delta correspondant à la plage de transaction (100, 200) enregistre les lignes supprimées qui avaient été insérées par les transactions de la plage (100, 200). Comme pour les fichiers de données, le fichier delta est accessible de manière séquentielle.  
  
 Lorsqu'une ligne est supprimée, elle n'est pas supprimée du fichier de données mais une référence à la ligne est ajoutée au fichier delta associé à la plage de transaction où la ligne de données a été insérée. Étant donné que la ligne à supprimer existe déjà dans le fichier de données, le fichier delta stocke uniquement les informations de référence sur `{inserting_tx_id, row_id, deleting_tx_id }` et suit l'ordre des opérations de suppression ou de mise à jour d'origine du journal des transactions.  
  
## <a name="populating-data-and-delta-files"></a>Remplissage des fichiers de données et des fichiers delta  
 Les fichiers de données et delta sont remplis par un thread d'arrière-plan appelé point de contrôle hors connexion. Ce thread lit les enregistrements du journal des transactions générés par les transactions validées sur les tables mémoire optimisées et ajoute des informations concernant les lignes insérées et supprimées dans les fichiers de données et delta appropriés. Contrairement aux tables sur disque où les pages de données/index sont vidées avec des E/S aléatoires lorsque le point de contrôle est effectué, la persistance de la table mémoire optimisée est une opération en arrière-plan continue. Plusieurs fichiers delta sont accédés car une transaction peut supprimer ou mettre à jour toute ligne ayant été insérée par une transaction précédente. Les informations de suppression sont toujours ajoutées à la fin du fichier delta. Par exemple, une transaction avec un horodateur de validation de 600 insère une nouvelle ligne et supprime les lignes insérées par les transactions ayant un horodateur de validation de 150, 250 et 450, comme le montre l'illustration ci-après. Les quatre opérations d'E/S de fichier (trois pour les lignes supprimées et une pour les nouvelles lignes insérées) sont des opérations Append-Only sur les fichiers de données et delta correspondants.  
  
 ![Lecture des enregistrements du journal des tables optimisées en mémoire](../../database-engine/media/read-logs-hekaton.gif "Lecture des enregistrements du journal des tables optimisées en mémoire")  
  
## <a name="accessing-data-and-delta-files"></a>Accès aux fichiers de données et aux fichiers delta  
 Les paires de fichiers de données et delta sont accessibles dans les cas suivants.  
  
 Thread de point de contrôle hors connexion  
 Ce thread applique les modifications apportées aux lignes de données mémoire optimisées (insertions et suppressions) dans les paires de fichiers de données et delta correspondantes.  
  
 Opération de fusion  
 L'opération fusionne une ou plusieurs paires de fichiers de données et delta afin de créer une nouvelle paire de fichiers de données et delta.  
  
 Pendant une récupération sur incident  
 Lorsque [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] redémarre ou que la base de données est remise en ligne, les données mémoire optimisées sont remplies en utilisant les paires de fichiers de données et delta. Le fichier delta filtre les lignes supprimées lors de la lecture des lignes à partir du fichier de données correspondant. Dans la mesure où chaque paire de fichier de données et de fichier delta est indépendante, ces fichiers sont chargés en parallèle pour réduire le temps de chargement en mémoire des données. Une fois que les données ont été chargées en mémoire, le moteur OLTP en mémoire applique les enregistrements du journal des transactions non encore couverts par les fichiers de point de contrôle afin que les données optimisées en mémoire soient complètes.  
  
 Pendant une opération de restauration  
 Les fichiers de point de contrôle de l'OLTP en mémoire sont créés à partir de la sauvegarde de base de données, puis une ou plusieurs sauvegardes de journal de transactions sont appliquées. Comme pour la récupération sur incident, le moteur OLTP en mémoire charge les données en mémoire en parallèle pour minimiser l'impact sur le temps de récupération.  
  
## <a name="merging-data-and-delta-files"></a>Fusion de fichiers de données et de fichiers delta  
 Les données des tables mémoire optimisées sont stockées dans une ou plusieurs paires de fichiers de données et delta (également appelées une paire de fichiers de point de contrôle, ou CFP). Les fichiers de données stockent les lignes insérées et les fichiers delta référencent les lignes supprimées. Pendant l'exécution d'une charge de travail OLTP, lorsque les opérations DML mettent à jour, insèrent et suppriment des lignes, de nouvelles paires de fichiers de point de contrôle sont créées pour rendre les nouvelles lignes persistantes, et la référence aux lignes supprimées est ajoutée aux fichiers delta.  
  
 Les métadonnées de toutes les paires de fichiers de point de contrôle précédemment fermées et actuellement actives sont enregistrées dans une structure de tableau interne appelée tableau de stockage. Il s'agit d'un tableau de taille définie (8 192 entrées) de paires de fichiers de point de contrôle. Les entrées du tableau de stockage sont triées par la plage de transaction. Les paires de fichiers de point de contrôle dans le tableau de stockage (et la fin du journal) représentent la totalité de l'état sur disque requis pour extraire une base de données avec des tables mémoire optimisées.  
  
 Au fil du temps, avec les opérations DML, le nombre de paires de fichiers de point de contrôle augmente et le tableau de stockage atteint sa capacité, ce qui introduit les problèmes suivants :  
  
-   Lignes supprimées.  Les lignes supprimées restent dans le fichier de données mais sont marquées comme supprimées dans le fichier delta correspondant. Ces lignes ne sont plus nécessaires et seront supprimées du stockage. Si les lignes supprimées n'étaient pas supprimées des CFPs, elles utiliseraient inutilement de l'espace et ralentiraient le temps de récupération.  
  
-   Tableau de stockage complet. Lorsque 8 000 entrées dans le tableau de stockage sont allouées (192 entrées du tableau sont réservées pour la concurrence des fusions existantes ou pour vous permettre d'effectuer des fusions manuelles), aucune nouvelle transaction DML ne peut être exécutée sur les tables mémoire optimisées durables. Seules les opérations de point de contrôle et de fusion peuvent consommer les entrées restantes. Cela garantit que les transactions DML ne remplissent pas le tableau et que certaines entrées du tableau sont réservées pour fusionner les fichiers existants et libérer l'espace du tableau.  
  
-   Traitement de manipulation du tableau de stockage. Les processus internes recherchent le tableau de stockage pour les opérations telles que la recherche de fichier delta pour ajouter des informations sur une ligne supprimée. Le coût de ces opérations augmente avec le nombre d'entrées.  
  
 Pour éviter ces inefficacités, les paires de fichiers de point de contrôle fermées plus anciennes sont fusionnées, en fonction d'une stratégie de fusion décrite ci-dessous, de sorte que le tableau de stockage est condensé pour représenter le même jeu de données, avec un nombre réduit d'appels aux paires de fichiers de point de contrôle.  
  
 La taille totale en mémoire des tables durables dans une base de données ne doit pas dépasser 250 Go. Les tables durables qui utilisent jusqu'à 250 Go de mémoire (en supposant des opérations d'insertion, de suppression et de mise à jour) auront besoin d'un espace de stockage moyen de 500 Go. 4 000 paires de fichiers de données et de fichiers delta dans le groupe de fichiers mémoire optimisé sont nécessaires pour prendre en charge les 500 Go d'espace de stockage.  
  
 Les pics à court terme d'activité dans la base de données peuvent entraîner un décalage des opérations de point de contrôle et de fusion, qui augmentera le nombre de paires de fichiers de données et delta nécessaires. Pour gérer les pics à court terme d'activité dans la base de données, le système de stockage peut allouer jusqu'à 8 000 paires de fichiers de données et delta pour au plus un total de 1 To de stockage. Lorsque cette limite est atteinte, aucune nouvelle transaction n'est autorisée sur la base de données tant que les opérations de point de contrôle n'ont pas rattrapé leur retard. Si la taille des tables durables en mémoire dépasse 250 Go pendant de longues périodes, il est possible d'atteindre la limite de 8 000 paires de fichiers.  
  
 L'opération de fusion prend comme entrée une ou plusieurs paires de fichiers de point de contrôle fermées adjacentes (appelées source de fusion) à partir d'une stratégie de fusion définie en interne, et produit une paire de fichiers de point de contrôle résultante, appelée la cible de fusion. Les entrées dans chaque fichier delta des paires de fichiers de point de contrôle sources sont utilisées pour filtrer les lignes à partir du fichier de données correspondant pour supprimer des lignes de données qui ne sont pas nécessaires. Les lignes restantes dans les paires de fichiers de point de contrôle sources sont consolidées dans une paire de fichiers de point de contrôle cible. Après la fusion, la paire de fichiers de point de contrôle résultante (cible de fusion) remplace les paires de fichiers de point de contrôle sources (sources de fusion). Les paires de fichiers de point de contrôle sources de fusion passent par une phase de transition avant d'être supprimées du stockage.  
  
 Dans l'exemple ci-dessous, le groupe de fichiers de la table mémoire optimisée contient quatre paires de fichiers de données et delta ayant l'horodateur 500 et contenant des données issues de transactions précédentes. Par exemple, les lignes du premier fichier de données correspondent aux transactions avec un horodateur supérieur à 100 et inférieur ou égal à 200 ; alternativement représenté comme (100, 200]. Le deuxième et le troisième fichiers de données affichent un taux de remplissage inférieur à 50 % après prise en compte des lignes marquées comme supprimées. L'opération de fusion associe ces deux paires de fichiers de point de contrôle et crée une paire de fichiers de point de contrôle contenant des transactions avec un horodateur supérieur à 200 et inférieur ou égal à 400, qui est la plage combinée de ces deux paires de fichiers de point de contrôle. Vous voyez une autre paire de fichiers de point de contrôle avec une plage (500, 600] et un fichier delta non vide pour la plage de transactions (200, 400] indique que l'opération de fusion peut être effectuée en même temps que l'activité transactionnelle comprenant la suppression de plus de lignes des paires de fichiers de point de contrôle source.  
  
 ![Le diagramme affiche le groupe de fichiers de table optimisé en mémoire](../../database-engine/media/storagediagram-hekaton.png "Le diagramme affiche le groupe de fichiers de table optimisé en mémoire")  
  
 Un thread d'arrière-plan évalue toutes les paires de fichiers de point de contrôle fermées à l'aide d'une stratégie de fusion, puis initie une ou plusieurs demandes de fusion pour les paires de fichiers de point de contrôle qualifiées. Ces demandes de fusion sont traitées par le thread de point de contrôle hors connexion. L'évaluation de la stratégie de fusion est effectuée périodiquement et lorsqu'un point de contrôle est fermé.  
  
### <a name="includesssql14includessssql14-mdmd-merge-policy"></a>[!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Stratégie de fusion  
 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] implémente la stratégie de fusion suivante :  
  
-   Une fusion est planifiée si 2 ou plus paires de fichiers de point de contrôle peuvent être consolidées, après avoir tenu compte des lignes supprimées, de sorte que les lignes résultantes puissent tenir dans une paire de fichiers de point de contrôle de taille idéale. La taille idéale d'une paire de fichiers de point de contrôle est déterminée comme suit :  
  
    -   Si un ordinateur a 16 Go de mémoire ou moins, le fichier de données a une taille de 16 Mo et le fichier delta a une taille de 1 Mo.  
  
    -   Si un ordinateur a plus de 16 Go de mémoire, le fichier de données a une taille de 128 Mo et le fichier delta a une taille de 16 Mo.  
  
-   Une seule paire de fichiers de point de contrôle peut être fusionnée automatiquement si le fichier de données dépasse 256 Mo et plus de la moitié des lignes sont supprimées. Un fichier de données peut atteindre une taille de 128 Mo si, par exemple, une seule transaction ou plusieurs transactions simultanées insèrent ou mettent à jour un grand nombre de données, forçant le fichier de données à dépasser sa taille idéale car une transaction ne peut pas couvrir plusieurs paires de fichiers de point de contrôle.  
  
 Voici des exemples qui montrent les paires de fichiers de point de contrôle qui seront fusionnées dans le cadre de la stratégie de fusion :  
  
|Paires de fichiers sources de point de contrôle adjacentes (% de remplissage)|Sélection pour la fusion|  
|-------------------------------------------|---------------------|  
|CFP0 (30%), CFP1 (50%), CFP2 (50%), CFP3 (90%)|(CFP0, CFP1)<br /><br /> CFP2 n'est pas choisi car le fichier de données résultant sera supérieur à 100 % de la taille idéale.|  
|CFP0 (30%), CFP1 (20%), CFP2 (50%), CFP3 (10%)|(CFP0, CFP1, CFP2). Les fichiers sont sélectionnés à partir de la gauche.<br /><br /> CTP3 n'est pas choisi car le fichier de données résultant sera supérieur à 100 % de la taille idéale.|  
|CFP0 (80%), CFP1 (30%), CFP2 (10%), CFP3 (40%)|(CFP1, CFP2, CFP3). Les fichiers sont sélectionnés à partir de la gauche.<br /><br /> CFP0 est ignoré car si associé à CFP1, le fichier de données résultant sera supérieur à 100 % de la taille idéale.|  
  
 Toutes les paires de fichiers de point de contrôle avec de l'espace disponible ne sont pas qualifiées pour la fusion. Par exemple, si deux paires de fichiers de point de contrôle adjacentes sont complètes à 60 %, elles ne seront pas qualifiées pour la fusion et chacune des paires aura 40 % de stockage inutilisé. Dans le pire des cas, toutes les paires de fichiers de point de contrôle seront complètes à 50%, soit une utilisation du stockage de seulement 50 %. Alors que des lignes supprimées peuvent exister dans le stockage car les paires de fichiers de contrôle ne sont pas qualifiées pour la fusion, les lignes supprimées peuvent déjà avoir été supprimées de la mémoire par le garbage collection en mémoire. La gestion du stockage et de la mémoire est indépendante du garbage collection. Le stockage pris par des paires de fichiers de point de contrôle actives (certaines paires de fichiers de point de contrôle n'ont pas été mises à jour) peut être jusqu'à 2 fois supérieur à la taille des tables durables en mémoire.  
  
 Si nécessaire, une fusion manuelle peut être effectuée en appelant explicitement [sys.sp_xtp_merge_checkpoint_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql).  
  
### <a name="life-cycle-of-a-cfp"></a>Cycle de vie d'une paire de fichiers de point de contrôle  
 Les paires de fichiers de point de contrôle traversent plusieurs états avant de pouvoir être libérées. À tout moment, les paires de fichiers de point de contrôle sont dans l'une des phases suivantes : PRECREATED, UNDER CONSTRUCTION, ACTIVE, MERGE TARGET, MERGED SOURCE, REQUIRED FOR BACKUP/HA, IN TRANSITION TO TOMBSTONE, et TOMBSTONE. Pour obtenir une description de ces phases, consultez [sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql).  
  
 Après prise en compte du stockage occupé par les paires de fichiers de point de contrôle selon leurs états, le stockage global pris par les tables mémoire optimisées peut être bien plus grand que 2 fois la taille des tables en mémoire. La DMV [sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41; ](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql) peut être interrogée pour répertorier toutes les paires dans le groupe de fichiers mémoire optimisé, y compris leur phase. Les paires de fichiers de point de contrôle qui passent de l'état MERGE SOURCE à l'état TOMBSTONE et l'opération de garbage collection peuvent occuper jusqu'à cinq points de contrôle, et chaque point est suivi d'une sauvegarde du journal des transactions, si la base de données est configurée selon un mode de restauration complète ou de récupération utilisant les journaux de transactions.  
  
 Forcez manuellement le point de contrôle, puis la sauvegarde de fichier journal pour accélérer l'opération de garbage collection, mais cela ajoutera 5 paires de fichiers de point de contrôle vides (5 paires de fichiers de données/delta avec chacune une taille de fichier de données de 128 Mo). Dans les scénarios de production, les points de contrôle automatiques et les sauvegardes de fichier journal effectuées dans le cadre de la stratégie de sauvegarde basculent sans problème les paires de fichiers de point de contrôle vers ces phases sans aucune intervention manuelle. L'impact du processus de garbage collection est le suivant : les bases de données avec des tables mémoire optimisées peuvent avoir une plus grande taille de stockage comparée à leur taille en mémoire. Il n'est pas rare que les paires de fichiers de point de contrôle soient jusqu'à quatre fois plus volumineuses que les tables mémoire optimisées durables en mémoire.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et gestion du stockage des objets mémoire optimisés](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
