---
title: Architecture du journal des transactions SQL Server et gestion | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 4d1a4f97-3fe4-44af-9d4f-f884a6eaa457
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 799b6a05850abb88c97c8e2a27214055eb20d976
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164869"
---
# <a name="sql-server-transaction-log-architecture-and-management"></a>Architecture et gestion du journal des transactions SQL Server
[!INCLUDE[appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Chaque base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] possède un journal des transactions qui enregistre toutes les transactions et les modifications apportées par chacune d'entre elles. Le journal des transactions est un composant essentiel de la base de données et, en cas de défaillance du système, vous pouvez en avoir besoin pour rétablir la cohérence de la base de données. Ce guide contient des informations sur l'architecture physique et logique du journal des transactions. Ces informations pourront vous aider à gérer plus efficacement les journaux des transactions.  

  
##  <a name="Logical_Arch"></a> Architecture logique du journal des transactions  
 Le journal des transactions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fonctionne de façon logique comme s'il s'agissait d'une chaîne d'enregistrements de journal. Chacun de ces enregistrements est identifié par un numéro séquentiel dans le journal (LSN). Chaque nouvel enregistrement est écrit à la fin logique du journal avec un LSN supérieur à celui de l'enregistrement qui le précède. Lors de leur création, les enregistrements de journal sont stockés séquentiellement. Chacun d'eux contient l'ID de la transaction à laquelle il appartient. Pour chaque transaction, tous les enregistrements de journal associés sont reliés de façon individuelle dans une chaîne grâce aux pointeurs arrière qui accélèrent la restauration de la transaction.  
  
 Les enregistrements de journal relatifs aux modifications de données consignent soit l'opération logique effectuée, soit les images avant/après des données modifiées. L'image avant est une copie des données avant que l'opération n'ait été effectuée, tandis que l'image après est une copie des données après que l'opération a été effectuée.  
  
 Les étapes pour récupérer une opération dépendent du type de journal d'enregistrement :  
  
-   Opération logique enregistrée  
  
    -   Si vous repositionnez l'opération logique avant, elle est effectuée à nouveau.  
  
    -   Si vous annulez l'opération logique, l'opération inverse est effectuée.  
  
-   Image avant et après enregistrées  
  
    -   Si vous repositionnez l'opération avant, l'image après est appliquée.  
  
    -   Si vous annulez l'opération, l'image avant est appliquée.  
  
 De nombreux types d'opérations sont enregistrés dans le journal des transactions. Ces opérations comprennent :  
  
-   Le début et la fin de chaque transaction.  
  
-   Chaque modification de données (insertion, mise à jour ou suppression). Il s'agit des modifications apportées aux tables, y compris les tables système, par les procédures stockées système ou les instructions DDL (Data Definition Language).  
  
-   Chaque allocation ou désallocation de page et d'étendue.  
  
-   Création ou suppression d'une table ou d'un index.  
  
 Les opérations de restauration sont également consignées dans le journal. Chaque transaction réserve de l'espace dans le journal des transactions afin qu'il existe suffisamment d'espace journal pour prendre en charge une restauration déclenchée par une instruction de restauration explicite ou par la détection d'une erreur. Le volume d'espace réservé dépend des opérations effectuées dans la transaction, mais il est généralement égal au volume d'espace utilisé pour la journalisation de chaque opération. Cet espace réservé est libéré lorsque la transaction est terminée.  
  
 La section du fichier journal comprise entre le premier enregistrement de journal nécessaire à une restauration portant sur l’ensemble de la base de données et la fin du journal représente la partie active du journal, également appelée le *journal actif*. Cette section est indispensable pour procéder à une récupération complète de la base de données. Aucune partie de ce journal actif ne peut être tronquée. Le numéro séquentiel dans le journal (LSN) de ce premier enregistrement est le LSN de récupération minimum (*MinLSN*).  
  
##  <a name="physical_arch"></a> Architecture physique du journal des transactions  
 Le journal des transactions d'une base de données s'étend sur un ou plusieurs fichiers physiques. D'un point de vue conceptuel, le fichier journal est une chaîne d'enregistrements. D'un point de vue physique, la séquence des enregistrements du journal est stockée de façon efficace dans l'ensemble de fichiers physiques qui implémente le journal des transactions. Chaque base de données doit posséder au moins un fichier journal.  
  
 Le [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] divise chaque fichier journal physique en un certain nombre de fichiers journaux virtuels. La taille et le nombre de ces fichiers journaux virtuels sont variables. Le [!INCLUDE[ssDE](../includes/ssde-md.md)] choisit dynamiquement la taille des fichiers journaux virtuels en créant ou en étendant des fichiers journaux. Le [!INCLUDE[ssDE](../includes/ssde-md.md)] essaie de ne conserver qu’un petit nombre de fichiers virtuels. Après une extension du fichier journal, la taille des fichiers virtuels est la somme de la taille du journal existant et de la taille du nouvel incrément de fichier. La taille et le nombre des fichiers journaux virtuels ne peuvent être ni configurés, ni définis par les administrateurs.  
  
 Le seul moment où les fichiers journaux virtuels ont une incidence sur les performances du système est lorsque les valeurs *size* et *growth_increment* des fichiers journaux physiques sont faibles. La valeur *size* correspond à la taille initiale du fichier journal et la valeur *growth_increment* correspond à la quantité d’espace ajoutée au fichier chaque fois qu’un espace supplémentaire s’avère nécessaire. Si la taille des fichiers journaux s'accroît par de petits incréments, de nombreux fichiers journaux virtuels vont être créés, ce qui peut ralentir le démarrage de la base de données ainsi que les opérations de sauvegarde et de restauration. Il est conseillé d’affecter aux fichiers journaux une valeur *size* proche de la taille finale souhaitée et une valeur *growth_increment* relativement importante. Pour plus d’informations sur ces paramètres, consultez [Options de fichiers et de groupes de fichiers ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).  
  
 Le journal des transactions est un fichier cumulatif. Considérons, par exemple, une base de données possédant un fichier journal physique divisé en quatre fichiers journaux virtuels. Lors de la création de la base de données, le fichier journal logique commence au début du fichier journal physique. Les nouveaux enregistrements du journal sont ajoutés à la fin du journal logique, qui s'étend vers la fin du journal physique. Le fait de tronquer le journal permet de libérer tous les journaux virtuels dont les enregistrements précèdent tous le MinLSN (numéro séquentiel dans le journal minimum). Le *MinLSN* est le numéro séquentiel dans le journal du plus ancien enregistrement du journal requis pour une opération de restauration réussie de l’ensemble de la base de données. Le journal des transactions de la base de données exemple ressemblerait à celui de l'illustration suivante :  
  
 ![Fichier journal divisé en quatre fichiers journaux virtuels](media/tranlog3.gif "fichier journal divisé en quatre fichiers journaux virtuels")  
  
 Lorsque la fin du journal logique atteint la fin du fichier journal physique, le nouvel enregistrement du journal revient au début du fichier journal physique.  
  
 ![Enregistrements de journal environ au début du fichier journal de type wrap](media/tranlog4.gif "enregistrements de journal sont automatiquement environ début du fichier journal")  
  
 Le cycle se répète indéfiniment tant que la fin du journal logique n'a pas atteint le début du journal logique. Si les anciens enregistrements du journal sont tronqués suffisamment souvent pour laisser de la place à tous les nouveaux enregistrements créées jusqu'au point de contrôle suivant, le journal ne se remplit jamais. Si la fin du journal logique atteint le début du journal logique, l'une ou l'autre des situations suivantes se produit :  
  
-   Si le paramètre FILEGROWTH est activé pour le journal et que l’espace disque est suffisant, le fichier s’étend en fonction de la taille spécifiée dans le paramètre *growth_increment*, les nouveaux enregistrements du journal étant ajoutés à l’extension. Pour plus d’informations sur le paramètre FILEGROWTH, consultez [Options de fichiers et de groupes de fichiers ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).  
  
-   Si le paramètre FILEGROWTH n’est pas activé ou si l’espace disque réservé au fichier journal est inférieur à la taille spécifiée dans le paramètre *growth_increment*, l’erreur 9002 est générée.  
  
 Si le journal contient plusieurs fichiers journaux physiques, le journal logique va se déplacer dans tous les fichiers journaux physiques avant de revenir au début du premier fichier journal physique.  
  
### <a name="log-truncation"></a>Troncation de journal  
 La troncation du journal est essentielle pour empêcher que le journal se remplisse. La troncation du journal supprime les fichiers journaux virtuels inactifs du journal des transactions logique d'une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , ce qui libère de l'espace dans le journal logique de façon à ce qu'il soit réutilisé par le journal des transactions physique. Si un journal des transactions n'était jamais tronqué, il finirait par occuper tout l'espace disque alloué à ses fichiers journaux physiques. Toutefois, une opération de point de contrôle est requise avant que le journal des transactions puisse être tronqué. Un point de contrôle écrit les pages modifiées en mémoire actuelles (appelées pages de modifications) et les informations du journal des transactions de la mémoire vers le disque. Lorsque le point de contrôle est créé, la partie inactive du journal des transactions est marquée comme réutilisable. Après cela, elle peut être libérée par troncation du journal. Pour plus d’informations sur les points de contrôle, consultez [Points de contrôle de base de données &#40;SQL Server&#41;](../relational-databases/logs/database-checkpoints-sql-server.md).  
  
 Les illustrations suivantes montrent un journal des transactions avant et après une troncation. La première illustration montre un journal des transactions qui n'a jamais été tronqué. Actuellement, quatre fichiers journaux virtuels sont utilisés par le journal logique. Le journal logique commence avant le premier fichier journal virtuel et se termine au journal virtuel 4. L'enregistrement NSEmin se trouve dans le journal virtuel 3. Les journaux virtuels 1 et 2 contiennent uniquement des enregistrements de journal inactifs. Ces enregistrements peuvent être tronqués. Le journal virtuel 5 est encore inutilisé et ne fait pas partie du journal logique actuel.  
  
 ![Journal des transactions avec quatre journaux virtuels](media/tranlog2.gif "journal des transactions avec quatre journaux virtuels")  
  
 La deuxième illustration montre le journal après sa troncation. Les journaux virtuels 1 et 2 ont été libérés en vue de leur réutilisation. Le journal logique commence désormais au début du journal virtuel 3. Le journal virtuel 5 est encore inutilisé et ne fait pas partie du journal logique actuel.  
  
 ![Fichier journal divisé en quatre fichiers journaux virtuels](media/tranlog3.gif "fichier journal divisé en quatre fichiers journaux virtuels")  
  
 La troncation du journal se produit automatiquement après les événements suivants, à moins qu'elle ne soit retardée pour une raison quelconque :  
  
-   En mode de récupération simple, après un point de contrôle.  
  
-   En mode de restauration complète ou en mode de récupération utilisant les journaux de transactions, après une sauvegarde du journal, si un point de contrôle s'est produit depuis la dernière sauvegarde.  
  
 La troncation du journal peut être retardée pour différents motifs. En cas de retard prolongé de la troncation du journal, le journal des transactions peut se remplir complètement. Pour plus d’informations, consultez [Facteurs pouvant retarder la troncation du journal](../relational-databases/logs/the-transaction-log-sql-server.md#FactorsThatDelayTruncation) et [Résoudre les problèmes liés à un journal des transactions saturé &#40;erreur SQL Server 9002&#41;](../relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md).  
  
##  <a name="WAL"></a> Journal des transactions à écriture anticipée  
 Cette section décrit le rôle que joue le journal des transactions à écriture anticipée (journal WAL) au niveau de l'enregistrement sur disque des modifications apportées aux données. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilise un journal WAL (write-ahead log) qui garantit qu’aucune modification de données n’est écrite sur le disque avant l’écriture du journal associé sur celui-ci. Ainsi, les propriétés ACID (Atomicité, Cohérence, Isolation et Durabilité) d'une transaction sont conservées.  
  
 Pour comprendre le fonctionnement du journal à écriture anticipée, il est important que vous sachiez comment les données modifiées sont écrites sur le disque. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] gère un cache des tampons dans lequel il lit les pages de données lorsque celles-ci doivent être extraites. Lorsqu’une page est modifiée dans le cache des tampons, elle n’est pas réécrite immédiatement sur le disque, mais elle est marquée comme *erronée*. Une page peut avoir plusieurs écritures logiques avant son écriture physique sur le disque. Pour chaque écriture logique, un enregistrement du journal des transactions est inséré dans le cache du journal qui enregistre la modification. L'enregistrement doit être écrit sur le disque avant que la page de modifications associée n'ait été supprimée du cache et écrite sur le disque. Le processus de point de contrôle analyse régulièrement le cache à la recherche de tampons contenant des pages issues d'une base de données spécifiée et écrit toutes les pages de modifications sur le disque. Les points de contrôle permettent une récupération ultérieure du système en créant un point où toutes les pages de modifications sont effectivement écrites sur le disque.  
  
 Le processus d'écriture d'une page de données modifiée, du cache des tampons vers le disque, porte le nom de vidage. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] possède une logique qui empêche la suppression d’une page de modifications avant que l’enregistrement du journal associé n’ait été écrit. Les enregistrements de journal sont écrits sur le disque lorsque les transactions sont validées.  
  
##  <a name="Backups"></a> Sauvegardes du journal de transactions  
 Cette section présente les concepts sur la sauvegarde et la restauration (application) des journaux de transactions. En mode de récupération complète et en mode de récupération utilisant les journaux de transactions, la sauvegarde régulière des journaux de transactions (*sauvegardes des journaux*) est indispensable pour pouvoir récupérer les données. Sauvegardez le journal pendant l'exécution d'une sauvegarde complète. Pour plus d’informations sur les modes de récupération, consultez [Sauvegarde et restauration des bases de données SQL Server](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
 Avant de pouvoir créer la première sauvegarde du journal, vous devez créer une sauvegarde complète, telle qu'une sauvegarde de base de données ou la première d'une série de sauvegardes de fichiers. La restauration d'une base de données à l'aide seulement de sauvegardes de fichiers peut être complexe. Par conséquent, nous vous recommandons de commencer par une sauvegarde de base de données complète dès que possible. Puis, sauvegardez le journal des transactions régulièrement. Vous pouvez ainsi réduire les risques de perte de travail mais aussi permettre la troncation du journal des transactions. En général, le journal des transactions est tronqué après chaque sauvegarde de journal conventionnelle.  
  
 Nous vous recommandons d'effectuer des sauvegardes de journaux suffisamment fréquentes pour répondre à vos besoins, en particulier votre tolérance des pertes de données comme celles causées par un lecteur de journal endommagé. La fréquence appropriée des sauvegardes de journaux dépend de votre gestion des risques liés aux pertes de données et du nombre de sauvegardes de journaux qu'il vous est possible de stocker, gérer et potentiellement restaurer. Réaliser une sauvegarde de journal tous les 15 à 30 minutes peut être suffisant. Si vos besoins nécessitent de minimiser les risques de perte de travail, vous devez envisager des sauvegardes de journaux plus fréquentes. Une meilleure fréquence pour les sauvegardes de fichiers journaux offre l'avantage d'augmenter la fréquence de la troncation des journaux qui produit des fichiers journaux plus petits.  
  
 Pour limiter le nombre des sauvegardes de fichiers journaux à restaurer, il est essentiel de sauvegarder vos données régulièrement. Vous pouvez, par exemple, planifier une sauvegarde complète hebdomadaire et des sauvegardes différentielles quotidiennes de la base de données.  
  
### <a name="the-log-chain"></a>Séquence de journaux de transactions consécutifs  
 Une séquence continue de sauvegardes de journaux s’appelle une *séquence de journaux de transactions consécutifs*. Une séquence de journaux de transactions consécutifs commence par une sauvegarde complète de la base de données. Généralement, une nouvelle séquence de journaux de transactions consécutifs ne démarre que lorsque la base de données est sauvegardée pour la première fois ou après que le mode de récupération simple est remplacé par le mode de récupération complète ou le mode de récupération utilisant les journaux de transactions. Si vous ne choisissez pas de remplacer les jeux de sauvegarde existants lors de la création d'une sauvegarde complète de base de données, la séquence de journaux de transactions consécutifs existante reste intacte. Grâce à la séquence de journaux de transactions consécutifs intacte, vous pouvez restaurer votre base de données à partir d'une sauvegarde complète de base de données du support de sauvegarde, suivie de toutes les sauvegardes de fichiers journaux suivantes jusqu'à votre point de récupération. Le point de récupération peut être la fin de la dernière sauvegarde de fichier journal ou un point de récupération spécifique dans chacune des sauvegardes de fichiers journaux. Pour plus d’informations, consultez [Sauvegardes du journal des transactions &#40;SQL Server&#41;](../relational-databases/backup-restore/transaction-log-backups-sql-server.md).  
  
 Pour restaurer une base de données jusqu'au point d'échec, la séquence de journaux de transactions consécutifs doit être intacte. Autrement dit, la séquence ininterrompue des sauvegardes des journaux de transactions doit aller jusqu'au point de défaillance. Le point de commencement de cette séquence du journal dépend du type des sauvegardes de données que vous restaurez : base de données, partielle ou fichiers. Pour une sauvegarde partielle ou de base de données, la séquence des sauvegardes des journaux doit s'étendre à partir de la fin d'une sauvegarde partielle ou de base de données. Pour un jeu de sauvegardes de fichiers, la séquence des sauvegardes des journaux doit s'étendre à partir du début d'un jeu complet de sauvegardes de fichiers. Pour plus d’informations, consultez [Appliquer les sauvegardes du journal de transactions &#40;SQL Server&#41;](../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md).  
  
### <a name="restore-log-backups"></a>Restaurer des sauvegardes du journal  
 La restauration d'une sauvegarde de journal restaure par progression les modifications enregistrées dans le journal des transactions, afin de recréer l'état exact de la base de données qui existait au début de la sauvegarde du journal. Lorsque vous restaurez une base de données, vous devez restaurer les sauvegardes des journaux créées à la suite de la sauvegarde complète de base de données que vous restaurez ou à partir de la première sauvegarde de fichiers que vous restaurez. En règle générale, vous devez restaurer une série de sauvegardes de journaux jusqu'au point de récupération, après avoir restauré les données les plus récentes ou une sauvegarde différentielle. Ensuite, vous récupérez la base de données. Cette opération restaure toutes les transactions qui n'étaient pas terminées au début de la récupération et place la base de données en ligne. Une fois la base de données récupérée, vous ne pouvez plus restaurer des sauvegardes. Pour plus d’informations, consultez [Appliquer les sauvegardes du journal de transactions &#40;SQL Server&#41;](../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md).  
  
## <a name="additional-reading"></a>Lecture supplémentaire  
 Pour plus d'informations sur le journal des transactions, nous vous recommandons de lire les articles et les ouvrages suivants.  
  
 [Fonctionnement de la journalisation et de la récupération dans SQL Server de Paul Randall](http://technet.microsoft.com/magazine/2009.02.logging.aspx)  
  
 [Gestion du journal des transactions SQL Server de Tony Davis et Gail Shaw](http://www.simple-talk.com/books/sql-books/sql-server-transaction-log-management-by-tony-davis-and-gail-shaw/)  
  
  
