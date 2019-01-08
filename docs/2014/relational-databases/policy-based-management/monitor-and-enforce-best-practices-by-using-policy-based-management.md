---
title: Surveiller et appliquer les bonnes pratiques à l’aide de la gestion basée sur des stratégies | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 46788407-187e-4b0b-bfe4-529af8d77c60
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: bfc7cc16c9751ebdf64a8e9cd110547255c944ee
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52758011"
---
# <a name="monitor-and-enforce-best-practices-by-using-policy-based-management"></a>Surveiller et appliquer les bonnes pratiques à l'aide de la Gestion basée sur des stratégies
  Gestion basée sur des stratégies vous permet de surveiller les bonnes pratiques pour la [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] propose un ensemble de fichiers de stratégie que vous pouvez importer en tant que stratégies de meilleures pratiques, pour ensuite évaluer ces stratégies par rapport à un jeu de cibles qui inclut des instances, des objets d'instance, des bases de données ou des objets de base de données. Vous pouvez évaluer des stratégies manuellement, définir des stratégies pour évaluer un jeu de cibles selon une planification ou définir des stratégies pour évaluer un jeu de cibles en fonction d'un événement. Pour plus d’informations sur la gestion basée sur des stratégies, consultez [Administrer des serveurs à l’aide de la gestion basée sur des stratégies](administer-servers-by-using-policy-based-management.md).  
  
## <a name="policy-and-rules-for-database-engine"></a>Stratégies et règles du moteur de base de données  
 Le tableau suivant répertorie les stratégies qui sont inclus avec l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et inclut des informations sur les règles de meilleures pratiques qui évalue chaque stratégie. Les stratégies sont stockées sous la forme de fichiers XML et doivent être importées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations sur l’importation de stratégies, consultez [Importer une stratégie de gestion basée sur des stratégies](import-a-policy-based-management-policy.md).  
  
|Nom de stratégie|Règle de meilleure pratique|  
|-----------------|------------------------|  
|Algorithme de chiffrement à clé asymétrique|[Force de chiffrement des clés asymétriques](asymmetric-keys-encryption-strength.md)|  
|Emplacement des fichiers de données et de sauvegarde|[Les fichiers de sauvegarde doivent être placés sur des périphériques distincts des fichiers de base de données](../../database-engine/backup-files-must-be-on-separate-devices-from-the-database-files.md)|  
|Emplacement des fichiers de données et des fichiers journaux|[Placer les fichiers de données et les fichiers journaux sur des lecteurs distincts](place-data-and-log-files-on-separate-drives.md)|  
|Fermeture automatique de la base de données|[Définir l'option de base de données AUTO_CLOSE sur OFF](set-the-auto-close-database-option-to-off.md)|  
|Réduction automatique de la base de données|[Définir l'option de base de données AUTO_SHRINK sur OFF](set-the-auto-shrink-database-option-to-off.md)|  
|Classement de base de données|[Définir le même classement pour les bases de données définies par l'utilisateur que pour les bases de données MASTER ou model](../../database-engine/set-collation-user-defined-databases-match-master-model-databases.md)|  
|Vérification de la page de base de données|[Définir l'option de base de données PAGE_VERIFY sur CHECKSUM](set-the-page-verify-database-option-to-checksum.md)|  
|État de la page de base de données|[Vérifier l'intégrité d'une base de données contenant des pages suspectes](check-integrity-of-database-with-suspect-pages.md)|  
|Autorisations Invité|[Autorisations Invité sur les bases de données utilisateur](guest-permissions-on-user-databases.md)|  
|Date de la dernière sauvegarde réussie|[Sauvegarde obsolète](outdated-backup.md)|  
|Autorisations du serveur public non accordées|[Autorisations du serveur public](server-public-permissions.md)|  
|Chevauchement de masque d’affinité 32 bits SQL Server|[Masque d’affinité correcte et le chevauchement de masque d’affinité d’entrée/sortie](correct-affinity-mask-and-affinity-input-and-output-mask-overlap.md)|  
|Chevauchement de masque d'affinité SQL Server 64 bits|[Masque d’affinité correcte et le chevauchement de masque d’affinité d’entrée/sortie](correct-affinity-mask-and-affinity-input-and-output-mask-overlap.md)|  
|Masque d'affinité SQL Server|[Conserver la valeur par défaut du masque d'affinité](keep-the-affinity-mask-default-value.md)|  
|Seuil de processus bloqué SQL Server|[Augmenter la valeur de l'option blocked process threshold ou la désactiver](increase-or-disable-blocked-process-threshold.md)|  
|Trace par défaut SQL Server|[Fichiers journaux de trace par défaut désactivés](default-trace-log-files-disabled.md)|  
|Verrous dynamiques SQL Server|[Conserver la valeur par défaut de l'option de configuration locks](keep-the-locks-configuration-option-default-value.md)|  
|Regroupement léger SQL Server|[Désactiver le regroupement léger](disable-lightweight-pooling.md)|  
|Mode de connexion SQL Server|[Choisir un mode d'authentification](../security/choose-an-authentication-mode.md)|  
|Degré maximal de parallélisme SQL Server|[Définir l'option max degree of parallelism pour des performances optimales](set-the-max-degree-of-parallelism-option-for-optimal-performance.md)|  
|Nombre maximal de threads de travail SQL Server pour SQL Server 2000 32 bits|[Vérifier le paramètre de l'option Max Worker Threads](verify-max-worker-threads-setting.md)|  
|Nombre maximal de threads de travail SQL Server pour SQL Server 2000 64 bits|[Vérifier le paramètre Nombre maximum de threads de travail](verify-max-worker-threads-setting.md)|  
|Nombre maximal de threads de travail SQL Server pour SQL Server 2005 et versions ultérieures|[Vérifier le paramètre de l'option Max Worker Threads](verify-max-worker-threads-setting.md)|  
|Taille du paquet réseau SQL Server|[La taille du paquet réseau ne doit pas dépasser 8060 octets](network-packet-size-should-not-exceed-8060-bytes.md)|  
|Expiration du mot de passe SQL Server|[Expiration du mot de passe de connexion SQL Server](sql-server-login-password-expiration.md)|  
|Stratégie de mot de passe SQL Server|[Force du mot de passe de connexion SQL Server](sql-server-login-password-strength.md)|  
|Chiffrement à clé symétrique pour les bases de données utilisateur|[Clés symétriques sur les bases de données utilisateur](symmetric-keys-on-user-databases.md)|  
|Clé symétrique pour base de données MASTER|[Clés symétriques sur les bases de données système](symmetric-keys-on-system-databases.md)|  
|Clé symétrique pour bases de données système|[Clés symétriques sur les bases de données système](symmetric-keys-on-system-databases.md)|  
|Base de données de confiance|[Bit de confiance](trustworthy-bit.md)|  
|Journal des événements Windows : erreur liée à des ressources disque de cluster endommagées|[Détecter des problèmes de carte hôte SCSI](detect-scsi-host-adapter-issues.md)|  
|Journal des événements Windows : erreur liée au contrôle de pilote de périphérique|[Erreur de contrôle du pilote de périphérique](device-driver-control-error.md)|  
|Journal des événements Windows : erreur liée à un périphérique non prêt|[Erreur de périphérique non prêt](device-not-ready-error.md)|  
|Journal des événements Windows : erreur liée à un échec de requête d'E/S|[Détecter la demande d’entrée et sortie ayant échoué](detect-failed-input-and-output-requests.md)|  
|Journal des événements Windows : avertissement lié à un retard d'E/S|[Rechercher des problèmes de délai d’E/S dans le sous-système d’E/S disque](check-disk-input-and-output-subsystem-for-io-delay-problems.md)|  
|Journal des événements Windows : erreur liée à une erreur d'E/S durant une défaillance de page matérielle|[Erreur d’E/S lors du contrôle des erreurs de défaut de page matérielle](input-and-output-error-during-hard-page-fault.md)|  
|Journal des événements Windows : erreur liée à une nouvelle tentative de lecture|[Rechercher des problèmes de nouvelle tentative de lecture dans le sous-système d’E/S disque](check-disk-input-output-subsystem-for-read-retry-problems.md)|  
|Journal des événements Windows : erreur liée à un délai d'attente d'E/S au niveau du système de stockage|[Délai d’attente d’entrée-sortie du système de stockage](storage-system-input-output-time-out.md)|  
|Journal des événements Windows : erreur liée à une défaillance du système|[Défaillances inattendues du système](unexpected-system-failures.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser les facettes de la gestion basée sur des stratégies](working-with-policy-based-management-facets.md)  
  
  
