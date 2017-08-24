---
title: "Quelles sont les nouveautés de SQL Server 2017 RC1 sur Linux | Documents Microsoft"
description: "Cette rubrique présente les nouveautés de la version actuelle de 2017 du serveur SQL sur Linux."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 08/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 456b6f31-6b97-4e31-80ab-b40151ec4868
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 649c7cbd03b6d2e61dbbb572a34cdbcd2a7ab7cd
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="whats-new-for-sql-server-2017-on-linux"></a>Nouveautés de 2017 du serveur SQL sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

Cette rubrique décrit les nouveautés de SQL Server 2017 est en cours d’exécution sur Linux.

## <a name="rc2"></a>RC2

La version RC2 contient divers correctifs de bogues et améliorations.

## <a name="rc1"></a>RC1

La version RC1 contient les améliorations suivantes et les correctifs :

- Activé Transparent Layer Security (TLS) pour les connexions chiffrées. Pour plus d’informations, consultez [chiffrement des connexions à SQL Server sur Linux](sql-server-linux-encrypted-connections.md).
- Activé [l’authentification Active Directory](sql-server-linux-active-directory-authentication.md).
- Activé [messagerie de base de données](../relational-databases/database-mail/database-mail.md).
- Prise en charge IPV6.
- Variables d’environnement ajouté pour l’installation initiale de SQL Server. Pour plus d’informations, consultez [des paramètres de configuration de SQL Server avec les variables d’environnement sur Linux](sql-server-linux-configure-environment-variables.md).
- Supprimé **sqlpackage** installé binaires. SqlPackage peut toujours être exécutée sur Linux à distance à partir de Windows.
- Partagé des ensembles de l’agent de ressources disque cluster que le nom de ressource, comme il est sur une instance de cluster de basculement Windows SQL Server. `@@ServerName`Retourne le nom de ressource cluster du disque partagé de SQL Server ; avant RC1, il retourné le nom du nœud de cluster qui possédait la ressource.

## <a name="ctp-21"></a>CTP 2.1

La version CTP 2.1 contient les améliorations suivantes et les correctifs :

- Ajouté [variables d’environnement pour configurer le service SQL Server](sql-server-linux-configure-environment-variables.md).
- [MSSQL-conf](sql-server-linux-configure-mssql-conf.md) requiert désormais la convention d’affectation de noms en deux parties pour les paramètres.
- Le [mssql-scripter](https://github.com/Microsoft/sql-xplat-cli) outil. Cet utilitaire permet aux développeurs, les administrateurs et les administrateurs système générer `CREATE` et `INSERT` scripts Transact-SQL à partir des objets de base de données dans les bases de données SQL Server, base de données SQL Azure et entrepôt de données SQL Azure à partir de la ligne de commande.
- Le [outil DBFS](https://github.com/Microsoft/dbfs). Il s’agit d’un outil open source qui active des bases de données et les administrateurs système surveiller SQL Server plus facilement en exposant les données actives à partir des vues de gestion dynamique (DMV) SQL Server en tant que fichiers virtuels dans un répertoire virtuel sur les systèmes d’exploitation Linux.
- SQL Server Integration Services (SSIS) s’exécute désormais sur Linux. En outre, il est d’un nouveau package qui vous permet d’exécuter des packages SSIS sur Linux à partir de la ligne de commande. Pour plus d’informations, consultez la [annonce de billet de blog SSIS prise en charge de Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/). SSIS lors de l’actualisation de Linux CTP 2.1, vos packages SSIS permet les connexions ODBC sur Linux. Pour plus d’informations, consultez la [blog de l’annonce prise en charge d’ODBC sur Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

## <a name="ctp-20"></a>CTP 2.0

La version CTP 2.0 contient les améliorations suivantes et les correctifs :

- Ajouté **journaux** fonctionnalités de SQL Server Agent.
- Messages localisés de mssql-conf.
- Mise en forme de chemin d’accès Linux sont désormais compatibles dans le moteur SQL Server. Mais prend en charge pour « C:\\» continuent avec des préfixes de chemins d’accès.
- Activé DMV **sys.dm_os_file_exists**.
- Activé DMV **sys.fn_trace_gettable**.
- Ajouté [mode de sécurité stricte de CLR](/sql/database-engine/configure-windows/clr-strict-security).
- Graphique SQL.
- Reconstructions d’Index en ligne peut être repris.
- Traitement des requêtes adaptative.
- Ajout d’encodage UTF-8 pour les fichiers système, y compris les fichiers journaux.
- Correction des bases de données en mémoire limitation de l’emplacement. 
- Ajouter le nouveau type de cluster `CLUSTER_TYPE = EXTERNAL` pour la configuration d’un groupe de disponibilité pour la haute disponibilité.
- Corrigez l’écouteur du groupe de disponibilité pour le routage en lecture seule.
- Prise en charge de production pour les clients du programme d’Adoption anticipée (EAP). Inscrivez-vous [ici](http://aka.ms/eapsignup).

## <a name="ctp-14"></a>CTP 1.4

La version CTP 1.4 contient les améliorations suivantes et les correctifs :

- Activé le [l’Agent SQL Server](sql-server-linux-setup-sql-agent.md).
  - Fonctionnalité de travaux de T-SQL activée.
- Fuseau horaire des bogues :
  - Prise en charge de fuseau horaire pour Asie/Kolkata.
  - Fonction GETDATE() fixe.
- Réseau Async I / 0 améliorations :
  - Améliorations significatives des performances de charge de travail OLTP en mémoire.
- Image de docker inclut désormais les utilitaires de ligne de commande de SQL Server. (sqlcmd/bcp).
- Prise en charge de Virtual Device Interface (VDI) activée pour les sauvegardes.
- Emplacement de TempDB peut désormais être modifié après l’installation à l’aide `ALTER DATABASE`.

## <a name="ctp-13"></a>CTP 1.3

La version CTP 1.3 contient les améliorations suivantes et les correctifs :

- Activé [recherche en texte intégral](sql-server-linux-setup-full-text-search.md) fonctionnalité.
- Activé Always On [la fonctionnalité de groupes de disponibilité](sql-server-linux-availability-group-overview.md) pour la haute disponibilité.
- Des fonctionnalités supplémentaires dans **mssql-conf**:
  - Première configuration en utilisant **mssql-conf**. Consultez l’utilisation de mssql-conf dans le [guides d’installation](sql-server-linux-setup.md#platforms).
  - L’activation de groupes de disponibilité. Consultez le [rubrique de groupes de disponibilité](sql-server-linux-availability-group-overview.md).
- Chemin fixe de Linux natif prend en charge les groupes de fichiers OLTP en mémoire.
- Activé la fonctionnalité de gestion dynamique dm_os_host_info.

## <a name="ctp-12"></a>CTP 1.2

La version CTP 1.2 contient les améliorations suivantes et les correctifs :

- Prise en charge de [SUSE Linux Enterprise Server v12 SP2](quickstart-install-connect-suse.md).
- Correctifs de bogues pour les améliorations de stabilité et de moteur de base.
- Image de docker : 
  - Fixe [problème #1](https://github.com/Microsoft/mssql-docker/issues/1) en ajoutant les Python à l’image.
  - Supprimé `/opt/mssql/data` en tant que le volume par défaut.
- Mise à jour vers .NET 4.6.2.

## <a name="ctp-11"></a>CTP 1.1

La version CTP 1.1 contient les améliorations suivantes et les correctifs :

- Prise en charge pour Red Hat Enterprise Linux version 7.3.
- Prise en charge pour Ubuntu 16.10.
- Couche Docker du système d’exploitation mis à niveau pour Ubuntu 16.04.
- Résolu les problèmes de télémétrie dans l’image de Docker.
- Script d’installation de SQL Server fixe relatives bogues.
- Performances améliorées pour les modules T-SQL compilés en mode natif, y compris :
  - **OPENJSON**, **FOR JSON**, **JSON** intégrés.
  - Colonnes calculées (index uniquement autorisés sur les colonnes calculées persistantes, mais pas sur des colonnes calculées non persistantes pour les tables en mémoire).
  - **CROSS APPLY** operations.
- Nouvelles fonctionnalités de langage :
  - Fonctions de chaîne : **TRIM**, **CONCAT_WS**, **traduire** et **STRING_AGG** avec prise en charge pour **WITHIN GROUP (ORDER BY)**.
  - **IMPORTATION en bloc** prend désormais en charge au format CSV et le stockage d’objets Blob Azure en tant que fichier Source.

Mode de compatibilité 140 :

- Amélioré les performances de mise à jour de l’index columnstore non cluster dans le cas lorsque la ligne est dans la banque delta. Modifié à partir de la supprimer et insérer des opérations de mise à jour. Également modifier la forme de plan permet de limiter à partir de l’échelle.
- Requêtes en mode de traitement par lots prennent désormais en charge les « allocations de mémoire des boucles de commentaires ». Cela améliorera la concurrence et le débit sur les systèmes exécutant des requêtes répétées qui utilisent le mode de traitement par lots. Cela peut permettre plus de requêtes à exécuter sur les systèmes bloquant sur la mémoire avant de lancer des requêtes.
- Amélioration des performances dans le parallélisme de mode lot en ignorant le plan ordinaire pour le mode de traitement par lots des plans autoriser des plans parallèles être sélectionnées à la place sur columnstores. 

[Améliorations du Service Pack 1](https://blogs.msdn.microsoft.com/sqlreleaseservices/sql-server-2016-service-pack-1-sp1-released/) dans cette version CTP1.1 :
- Base de données de clonage pour le CLR, Filestream/Filetable, les objets en mémoire et le magasin de requêtes.
- **CRÉER** ou **ALTER** opérateurs pour les objets de programmabilité.
- Nouvelle **indicateur USE** option pour fournir des indications pour le processeur de requêtes de requête. En savoir plus ici : [indicateurs de requête](https://msdn.microsoft.com/en-us/library/ms181714.aspx).
- Compte de service SQL peut identifier par programme maintenant activer le verrouillage des Pages dans les autorisations de la mémoire et l’initialisation instantanée des fichiers.
- Prise en charge pour le nombre de fichiers TempDB, taille de fichier et les paramètres de croissance de fichier.
- Étendue des diagnostics dans showplan XML.
- Opérateur léger requête d’exécution de profilage.
- Nouvelle fonction de gestion dynamique **sys.dm_exec_query_statistics_xml**.
- Nouvelle fonction de gestion dynamique pour les statistiques incrémentielles.
- Supprimé bruyante dans-relatifs à la mémoire des messages de journalisation à partir du journal des erreurs.
- Diagnostics de latence AlwaysOn améliorée.
- Nettoyer le suivi des modifications manuel.
- **DROP TABLE** prend en charge pour la réplication.
- **BULK INSERT** dans le tas avec **automatique TABLOCK** sous TF 715.
- Parallèle **INSERT... Sélectionnez** modifications pour les tables temporaires locales.

En savoir plus sur ces correctifs dans le [description de la version de Service Pack 1](https://blogs.msdn.microsoft.com/sqlreleaseservices/sql-server-2016-service-pack-1-sp1-released/).

Plusieurs améliorations du moteur de base de données s’appliquent à Windows et Linux. La seule exception serait pour les fonctionnalités du moteur de base de données qui ne sont actuellement pas pris en charge sous Linux. Pour plus d’informations, consultez [Nouveautés de SQL Server 2017 (moteur de base de données)](https://msdn.microsoft.com/library/mt775028).

## <a name="see-also"></a>Voir aussi

Pour les exigences d’installation, les zones de fonctionnalité non prise en charge et les problèmes connus, consultez [notes de publication pour 2017 du serveur SQL sur Linux](sql-server-linux-release-notes.md).

